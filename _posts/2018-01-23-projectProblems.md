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
