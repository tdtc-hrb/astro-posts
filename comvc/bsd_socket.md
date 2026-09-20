---
layout: ../../layouts/MarkdownPostLayout.astro
title: "使用BSD socket"
description: "Windows"
date: 2023-03-05
author: "tdtc"
---
  BSD Socket是标准的套接字规范，那么怎么在windows使用他们呢？

# Init & clean
  首先要引用<winsock2.h>和ws2_32.lib；
  使用struct addrinfo需引用<ws2tcpip.h>。

  程序头: WSAStartup(),
  程序尾: WSACleanup();


# code
> 以下程序在VC9/VC14.1下编译通过

## 客户端程序

### prj1Clt
> 无getaddrinfo版
>>  注意：InetPton函数只能在Windows Version >=6上实现！

```c++
// prj1Clt.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

/**
 * Networking program is Win version with BSD Socket
 * Client side
 *
 * Author: xiaobin
 * Date: 2013-12-12
 * Modfity: 2020-5-28
 */

#include <iostream>

#if _MSC_VER > 1800
#include <tchar.h>
#endif

#ifdef _WIN32
#include <winsock2.h>
#include <ws2tcpip.h>
#pragma comment(lib, "ws2_32.lib")
#else
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/in.h>
#endif

#define MAXLINE 254
#define DEFAULT_PORT 3293

int main(int argc, char* argv[])
{
	int 				 sockfd;
	struct  sockaddr_in  servaddr;
	int					 iStatus;
	char				*sendBuff = "this is test message!";

#ifdef _WIN32
	WORD wVersionRequested;
	WSADATA wsaData;
	wVersionRequested = MAKEWORD(1, 1);
	iStatus = WSAStartup(wVersionRequested, &wsaData);
	if (iStatus != 0) {
		return 0;
	}
	if (LOBYTE(wsaData.wVersion) != 1 ||
		HIBYTE(wsaData.wVersion) != 1) {
		WSACleanup();
		return 0;
	}
#endif

	if (argc != 2)
		printf("Usage: <IPaddress>\n");

	sockfd = socket(AF_INET, SOCK_STREAM, 0);
	if (sockfd < 0)
		printf("socket error\n");

	/* check Server address */
	// inet_pton is win version - InetPton
	if (InetPton(AF_INET, (wchar_t*)argv[1], &servaddr.sin_addr) < 0)
		//if (InetPtonA(AF_INET, argv[1], &servaddr.sin_addr) < 0)
		printf("inet_pton error for %ls", argv[1]);

	/* Set serveraddr */
	memset(&servaddr, 0, sizeof(servaddr));
	servaddr.sin_family = AF_INET;
	servaddr.sin_addr.S_un.S_addr = inet_addr((char *)argv[1]);
	servaddr.sin_port = htons(DEFAULT_PORT);

	printf("%s%ls%s\n", "Connecting ", argv[1], " ...");

	/* connect server */
	iStatus = connect(sockfd, (struct sockaddr *) &servaddr, sizeof(servaddr));
	if (iStatus < 0) {
		closesocket(sockfd);
		printf("connect error\n");
	}

	printf("%s\n", "Writing...");
	/* Write data */
	iStatus = send(sockfd, sendBuff, (int)strlen(sendBuff), 0);
	if (iStatus < 0) {
		printf("%s\n", "write data error");
	}
	printf("%s\n", "Writed.");

#ifdef _WIN32
	closesocket(sockfd);
	WSACleanup();
#endif

	return 0;
}

```


### prj2Clt
> getaddrinfo版

```c++
// prj2Clt.cpp : Defines the entry point for the console application.
//

/**
 * Networking program is Win version with BSD Socket
 * Server side
 *
 * Author: xiaobin
 * Date: 2020-05-28 07:35
 */

#include <iostream>

#ifdef _WIN32
#include <winsock2.h>
#include <ws2tcpip.h>
#pragma comment(lib, "ws2_32.lib")
#else
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/in.h>
#endif

#define MAXLINE 254
#define DEFAULT_PORT_S "3293"

int main(int argc, char* argv[])
{
	int 				 sockfd;
	struct addrinfo      hints;
	struct addrinfo    	*servInfo = NULL;
	int    				 status;
	int					 iStatus;
	char				*sendBuff = "this is test message!";

#ifdef _WIN32
	WORD wVersionRequested;
	WSADATA wsaData;
	wVersionRequested = MAKEWORD(1, 1);
	iStatus = WSAStartup(wVersionRequested, &wsaData);
	if (iStatus != 0) {
		return 0;
	}
	if (LOBYTE(wsaData.wVersion) != 1 ||
		HIBYTE(wsaData.wVersion) != 1) {
		WSACleanup();
		return 0;
	}
#endif

	if (argc != 2)
		printf("Usage: <IPaddress>\n");

	/* Set serveraddr */
	memset(&hints, 0, sizeof(hints));
	hints.ai_family = AF_UNSPEC;
	hints.ai_socktype = SOCK_STREAM;
	hints.ai_flags = AI_PASSIVE;
	hints.ai_protocol = IPPROTO_TCP;

	status = getaddrinfo(argv[1], DEFAULT_PORT_S, &hints, &servInfo);
	if (status != 0) {
		printf("getaddrinfo:%s failed with error: %d\n", argv[1], status);
		return 1;
	}

	sockfd = socket(servInfo->ai_family, servInfo->ai_socktype, servInfo->ai_protocol);
	if (sockfd < 0)
		printf("socket error\n");

	printf("%s%s%s\n", "Connecting ", argv[1], " ...");

	/* connect server */
	iStatus = connect(sockfd, servInfo->ai_addr, servInfo->ai_addrlen);
	if (iStatus < 0) {
		closesocket(sockfd);
		printf("connect error\n");
	}

	freeaddrinfo(servInfo);

	printf("%s\n", "Writing...");
	/* Write data */
	iStatus = send(sockfd, sendBuff, (int)strlen(sendBuff), 0);
	if (iStatus < 0) {
		printf("%s\n", "write data error");
	}
	printf("%s\n", "Writed.");

#ifdef _WIN32
	closesocket(sockfd);
	WSACleanup();
#endif

	return 0;
}

```


## 服务器端程序

### prj1Srv
> 无getaddrinfo版

```c++
// prj1Srv.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

/**
 * Networking program is Win version with BSD Socket
 * Server side
 *
 * Author: xiaobin
 * Date: 2012-12-18 23:35
 * Modfity: 2023-3-6
 */

#include <iostream>

#ifdef _WIN32
#include <winsock2.h>
#pragma comment(lib, "ws2_32.lib")
#else
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/in.h>
#endif

#define DEFAULT_BUFLEN 128
#define DEFAULT_PORT 3293

int main(int argc, char* argv[])
{
	int					srvSock, client;
	struct sockaddr_in  addrSrv;
	int					iStatus;
	int					len;
	char				buff[DEFAULT_BUFLEN];

#ifdef _WIN32
	WORD wVersionRequested;
	WSADATA wsaData;
	wVersionRequested = MAKEWORD(1, 1);
	iStatus = WSAStartup(wVersionRequested, &wsaData);
	if (iStatus != 0) {
		return 0;
	}
	if (LOBYTE(wsaData.wVersion) != 1 ||
		HIBYTE(wsaData.wVersion) != 1) {
		WSACleanup();
		return 0;
	}
#endif
	
	srvSock = socket(AF_INET, SOCK_STREAM, 0);

	SecureZeroMemory(&addrSrv, sizeof(addrSrv));
	addrSrv.sin_family = AF_INET;
	addrSrv.sin_addr.S_un.S_addr = htonl(INADDR_ANY);
	addrSrv.sin_port = htons(DEFAULT_PORT);

	bind(srvSock, (struct sockaddr *)&addrSrv, sizeof(addrSrv));
	listen(srvSock, 5);

	len = sizeof(struct sockaddr);

	while (1) {
		client = accept(srvSock, (struct sockaddr *)&addrSrv, (int *)&len);
		iStatus = recv(client, buff, DEFAULT_BUFLEN, 0);
		if (iStatus > 0)
			printf("%s\n", buff);
	}


#ifdef _WIN32
	closesocket(client);
	closesocket(srvSock);
	WSACleanup();
#endif

	return 0;
}

```

### prj2Srv
> getaddrinfo版

```c++
// prj2Srv.cpp : Defines the entry point for the console application.
//

/**
 * Networking program is Win version with BSD Socket
 * Server side
 *
 * Author: xiaobin
 * Date: 2020-05-27 23:35
 */

#include <iostream>

#ifdef _WIN32
#include <winsock2.h>
#include <ws2tcpip.h>
#pragma comment(lib, "ws2_32.lib")
#else
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/in.h>
#endif

#define DEFAULT_BUFLEN 128
#define DEFAULT_PORT_S "3293"

int main(int argc, char* argv[])
{
	int						srvSock, client;
	struct addrinfo     	hints;
	struct addrinfo    		*servInfo = NULL;
	struct sockaddr_storage clientAddr;
	int    					status;
	int						iStatus;
	int						len;
	char					buff[DEFAULT_BUFLEN];

#ifdef _WIN32
	WORD wVersionRequested;
	WSADATA wsaData;
	wVersionRequested = MAKEWORD(1, 1);
	iStatus = WSAStartup(wVersionRequested, &wsaData);
	if (iStatus != 0) {
		return 0;
	}
	if (LOBYTE(wsaData.wVersion) != 1 ||
		HIBYTE(wsaData.wVersion) != 1) {
		WSACleanup();
		return 0;
	}
#endif

	if (argc != 2) {
		printf("Usage: <IPaddress>\n");
		exit(0);
	}

	memset(&hints, 0, sizeof(hints));
	hints.ai_family = AF_UNSPEC;
	hints.ai_socktype = SOCK_STREAM;
	hints.ai_flags = AI_PASSIVE;
	hints.ai_protocol = IPPROTO_TCP;

	status = getaddrinfo(argv[1], DEFAULT_PORT_S, &hints, &servInfo);
	if (status != 0) {
		printf("getaddrinfo:%s failed with error: %d\n", argv[1], status);
		return 1;
	}

	srvSock = socket(servInfo->ai_family, servInfo->ai_socktype, servInfo->ai_protocol);

	bind(srvSock, servInfo->ai_addr, (int)servInfo->ai_addrlen);
	listen(srvSock, 5);

	freeaddrinfo(servInfo);

	while (1) {
		len = sizeof(clientAddr);
		client = accept(srvSock, (struct sockaddr *)&clientAddr, &len);
		iStatus = recv(client, buff, DEFAULT_BUFLEN, 0);
		if (iStatus > 0)
			printf("%s\n", buff);
	}

#ifdef _WIN32
	closesocket(client);
	closesocket(srvSock);
	WSACleanup();
#endif

	return 0;
}

```

# 参考文献

- [Running the Winsock Client and Server Code Sample](https://docs.microsoft.com/zh-cn/windows/win32/winsock/finished-server-and-client-code) - microsoft

- [getaddrinfo function](https://docs.microsoft.com/en-us/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) - microsoft

- [5.1 getaddrinfo](https://blog.csdn.net/xiaobin_HLJ80/article/details/8826313) - xiaobin

- [网络编程client和server](https://tdtc-hrb.github.io/csdn/post/c-bsd_socket/) - xiaobin

- [WSAStartup](http://msdn.microsoft.com/en-us/library/ms742213(v=vs.85).aspx) - Microsoft Developer Network

- [WSACleanup](http://msdn.microsoft.com/en-us/library/ms741549(v=vs.85).aspx) - Microsoft Developer Network

- [InetPton](http://msdn.microsoft.com/en-us/library/cc805844(v=vs.85).aspx) - Microsoft Developer Network
