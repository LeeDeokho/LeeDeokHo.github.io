---
layout: post
title: "NHN 루키 기술교육 프로젝트하면서 겪었던 문제점 기록하는 글"
date: 2018-01-23 00:40:06
description: NHN 루키 기술교육 프로젝트하면서 겪었던 문제점 기록하는 글
tags: 
 - spring
comments: true
---


# 목록
- [mybatis](#mybatis)
- [krajee fileinput](#krajee-fileinput)
- [mysql](#mysql)
- [Spring Dependency](#spring-dependency)

## mybatis
스프링 프로젝트를 시작하면서 제일 낯설었던 것이 mybatis를 사용하는 것이었다. 


1. DB TABLE을 생성할 때 AUTO_INCREMENT로 생성된 ID 값을 가져오고 싶다면<br>
다음과 같이 `mapper.xml`에서 `useGeneratedKeys="true" keyProperty="letterId"` 속성을 줌으로써 해결할 수 있다.
리턴값으로 생성된 아이디의 값을 가져오게 된다.

```xml
<insert id="insert" parameterType="Letter" useGeneratedKeys="true" keyProperty="letterId">
```





## krajee fileinput
부트스트랩 기반의 file input인 krajee fileinput을 가져다 쓰는 중 문제가 발생.
`glyphicon`이 안나온다 ..
그래서 theming을 사용해 `font awesome`을 사용하는 것으로 theme를 바꿔서 사용했다.
아이콘은 잘 나오나 fa theme를 적용하면 사용하는 용도가 제한 적이게 된다.
예를 들면 드래그앤드랍 화면이 처음에 안나오다가 파일을 추가할 때만 나와야 하는 데 ,
고정 화면이 되버린다.
preview를 없애면 파일을 추가해도 preview가 안나온다.

해결 방안.
    1. glyphicon이 나오게 한다.
    2. fa theme를 그대로 사용하고 preview를 숨겼다 보여줬다 조작을 해본다.



## mysql

- 루트 계정 비밀번호 변경

`mysql -u root -p`
를 입력 후 root 비밀번호를 입력해 root 계정으로 로그인을 한다.

`use mysql;`
를 입력 하면 
`Database changed` 라는 문구가 나온다.

`describe user;`
를 해보면 password라는 필드가 없다.
password 대신에 `authentication_string` 라는 필드가 있다.

```
update user set authentication_string=password('바꿀 비밀 번호') where user='root';
```

라고 입력해주면 비밀변호 변경 완료!


## Spring Dependency
노트북에서 하다가 데스크탑으로 옮겨서 실행하니 다음과 같은 에러 발생.
처음엔 코드가 잘못된 줄 알았으나, 다른 팀원 환경에서는 다 잘되고 내 데스크탑에서만 안되는 상황.
진혜진선임님의 도움으로 해결.<br>
내컴퓨터 기준으로 `C:\Users\{사용자이름}\.m2\repository`
안에 dependency들이 저장된다. 그래서 폴더를 날리고 다시 업데이트해서 dependency를 다운 받았더니 해결.

```
Failed to instantiate SLF4J LoggerFactory
Reported exception:
java.lang.NoClassDefFoundError: ch/qos/logback/core/spi/LifeCycle
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(Unknown Source)
	at java.security.SecureClassLoader.defineClass(Unknown Source)
	at java.net.URLClassLoader.defineClass(Unknown Source)
	at java.net.URLClassLoader.access$100(Unknown Source)
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.slf4j.impl.StaticLoggerBinder.<init>(StaticLoggerBinder.java:59)
	at org.slf4j.impl.StaticLoggerBinder.<clinit>(StaticLoggerBinder.java:50)
	at org.slf4j.LoggerFactory.bind(LoggerFactory.java:150)
	at org.slf4j.LoggerFactory.performInitialization(LoggerFactory.java:124)
	at org.slf4j.LoggerFactory.getILoggerFactory(LoggerFactory.java:412)
	at org.slf4j.LoggerFactory.getLogger(LoggerFactory.java:357)
	at org.apache.commons.logging.impl.SLF4JLogFactory.getInstance(SLF4JLogFactory.java:155)
	at org.apache.commons.logging.impl.SLF4JLogFactory.getInstance(SLF4JLogFactory.java:132)
	at org.apache.commons.logging.LogFactory.getLog(LogFactory.java:273)
	at org.springframework.boot.SpringApplication.<clinit>(SpringApplication.java:179)
	at com.nhnent.rookie5.pingpong.PingpongApplication.main(PingpongApplication.java:17)
```
