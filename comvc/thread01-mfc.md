---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Multithreading with MFC - CWinThread"
description: "All threads in MFC applications are represented by CWinThread objects."
date: 2025-11-11
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
AfxBeginThread function is used in MFC to create threads in an MFC application.

#### [Difference between Afxbeginthread and CreateThread](https://stackoverflow.com/a/21718917)
```
For MFC programs, use AfxBeginThread.

CreateThread is raw Win32. It's incompatible with parts of the standard library.

_beginthread is part of the C standard library. 
It adds extra code to handle thread safety for other parts of the standard library that would be unsafe if you used CreateThread instead.

AfxBeginThread is (obviously enough) part of MFC. 
Along with the thread safety supported by _beginthread, it adds some (if only a few) C++ niceties.

So, you should only use CreateThread if the rest of your program is also pure, raw Win32, 
with no use of the standard library or MFC. If you're using MFC otherwise, 
you should normally use AfxBeginThread rather than CreateThread.
```

### Start
```
void CMFCApplication1Dlg::OnBnClickedButton1()
{
    // TODO: Add your control notification handler code here
    if (!m_pThread) {
        m_bThread = TRUE;
        m_pThread = AfxBeginThread(WorkerThread,
            this,
            THREAD_PRIORITY_NORMAL,
            0,
            0,
            NULL);
    }
}
```
#### Stop
```
void CMFCApplication1Dlg::OnBnClickedButton2()
{
    // TODO: Add your control notification handler code here
    m_bThread = FALSE;
    m_pThread = NULL;
}
```

### work thread
```
UINT WorkerThread(LPVOID arg)
{
    SYSTEMTIME st;
    CMFCApplication1Dlg *dlg = (CMFCApplication1Dlg *)arg;
    while (dlg->m_bThread) {
        GetSystemTime(&st);
        CString tm;
        tm.Format(_T("Time %.2d:%.2d:%.2d Date %.2d/%.2d/%.4d"),
            st.wHour, st.wMinute, st.wSecond, st.wDay, st.wMonth, st.wYear);
        
        dlg->m_Edt.SetWindowText((LPCTSTR)tm);
        Sleep(500);
    }
    AfxEndThread(0, TRUE);
    return 0;
}
```

### declare
```
private:
    CWinThread *m_pThread;
    bool m_bThread;
    friend  UINT WorkerThread(LPVOID arg);
```

## Ref
- [How can I create a worker thread using AfxBeginThread() function? ](https://www.equestionanswers.com/vcpp/worker-thread-afxbeginthread.php)
- [AfxBeThDemo.zip](https://mega.nz/file/DUVj3BgT#YzQzaGQKvrfy3-TJi-IUoveC0yYC5To7sIe7xIL3Zfg)
