---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Angular 的HttpClient应用"
description: "HttpClientModule, Observable"
date: 2025-05-29
author: "tdtc"
---

# Prepare
- install Angular CLI
```js
npm install -g @angular/cli
```
- create project
```bash
npx @angular/cli new userDetails-client --style=css --routing=false --skip-tests
```
## v17+
> From Angular v17 onwards, Standalone is now the new default for the CLI.
So when you create a new project, you won't have any modules in it if you don't specify anything.    
However, it is still possible to create a module-based app by using the ["--no-standalone"](https://stackoverflow.com/a/77457122) flag :
```
npx @angular/cli new userDetails-client --no-standalone --style=css --routing=false --skip-tests
```

# Angular struct

## Angular module
> app/app.module.ts

Add system modules and user components

- system module
example for: httpclient module

import pack:
```js
import { HttpClientModule } from "@angular/common/http";
```

declare Decorator:
```js
// import HttpClientModule after BrowserModule.
    HttpClientModule,
```

- user component
See the next section("Angular Component - add component") for examples of user components. 


## Angular Component
> app/component.ts

The root component.

When we need some services that need to be started at the beginning, we need to write code here.

## Angular Html
> app/app.component.html

View section.

To call root components and plug-and-play components, you need to write code here.




# Angular Service

![angular chrome](https://gitee.com/xiaobin80/cnblogs/raw/master/images/UserDetailsClient-static.png)
[run port](http://localhost:4260/)

Generate service and model:
```bash
ng generate service user/user
ng generate class user/user --type=model
```

Every service must use Dependency Injection.
```js
@Injectable(providedIn: 'root')
```


## [Creating observables](https://angular.io/guide/observables#creating-observables)

Use the Observable constructor to create an observable stream of any type. 
The constructor takes as its argument the subscriber function to run when the observable’s subscribe() method executes. 

- Get
```js
getUsers(): Observable<UserModel[]>
```

- Post
About the post method: The return value must be "Observable<any>"!

```js
postUser(userModel: UserModel): Observable<any> {// your code here}
```


## call them
```js
    this.userservice.getUsers().subscribe(
      data => {
        this.users = data;
        console.log(data);
    });
```


# Angular Component
- generate
```bash
ng generate component sign-up
```

- call
```js
<app-sign-up></app-sign-up>
```

## add component
> app/app.module.ts

```js
@NgModule({
  declarations: [
    AppComponent,
    SignUpComponent
  ],
```

```js
imports: [
    BrowserModule,
    ReactiveFormsModule
  ],
```



# Appendix

## Project code
> The token is not used in the demo.
- [userDetails-client](https://github.com/tdtc-hrb/userDetails-client)

## Reactive Forms
Use FormBuilder, FormGroup to implement applications.

see<sup>3</sup>, It should be noted that the verification part in html(sign-up.component.html) needs to refer to <sup>4</sup>.

```js
signUpForm.controls['xxx'].yyy
```

## Authorization
在[实际应用](https://github.com/tdtc-hrb/UserDetails-jwt-client)中：使用用户名和密码登录，获得Token值。    
![chrome shot](https://gitee.com/xiaobin80/cnblogs/raw/master/images/UserDetailsJwtClient.png)


最后，在http头添加token值, See[《Adding and updating headers》](https://angular.io/guide/http#adding-and-updating-headers).
```js
import { HttpHeaders } from '@angular/common/http';

const httpOptions = {
  headers: new HttpHeaders({
    'Content-Type':  'application/json',
    Authorization: 'my-auth-token'
  })
};
```

Angular applies interceptors in the order that you provide them.    
For example, consider a situation in which you want to handle the authentication    
of your HTTP requests and log them before sending them to a server.    
To accomplish this task, you could provide an AuthInterceptor service and then a LoggingInterceptor service.    
Outgoing requests would flow from the AuthInterceptor to the LoggingInterceptor.    
Responses from these requests would flow in the other direction, from LoggingInterceptor back to AuthInterceptor.    
The following is a visual representation of the process:

![angular auth](https://angular.io/generated/images/guide/http/interceptor-order.svg)

# Ref
- [Communicating with backend services using HTTP](https://angular.io/guide/http)
- [Using observables to pass values](https://angular.io/guide/observables)
- [<sup>3</sup>How To Use Reactive Forms in Angular](https://www.digitalocean.com/community/tutorials/angular-reactive-forms-introduction/)
- [<sup>4</sup>How to implement angular reactive forms validation in Angular 12 .?](https://edupala.com/angular-reactive-form-validation/)
- [The semantics of @Injectable(providedIn: 'root')?](https://stackoverflow.com/questions/51990188/the-semantics-of-injectableprovidedin-root)    
```
When you write @Injectable(providedIn: 'root') this means that the service in singletion 
for whole application and you can inject in anywhere in the application.
```
```
When you want to make service singleton only for an exact module, you need to assign 
your module as the parameter to the providedIn - @Injectable(providedIn: MyModule)
```
```
The only other action required in order to use the @Injectable decorated service is 
to import it and constructor inject it and that's it. 
No need to import it in the AppModule.
```
- [About SSR](https://dev-mind.fr/blog/2024/server_side_rendering.html)
```
SSR is a good option for static websites whose content doesn't change frequently. 
```
