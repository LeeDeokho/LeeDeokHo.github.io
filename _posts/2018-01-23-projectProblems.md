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
- mybatis



## mybatis
스프링 프로젝트를 시작하면서 제일 낯설었던 것이 mybatis를 사용하는 것이었다. 

1. DB TABLE을 생성할 때 AUTO_INCREMENT로 생성된 ID 값을 가져오고 싶다면<br>
다음과 같이 `mapper.xml`에서 `useGeneratedKeys="true" keyProperty="letterId"` 속성을 줌으로써 해결할 수 있다.
리턴값으로 생성된 아이디의 값을 가져오게 된다.

```xml
<insert id="insert" parameterType="Letter" useGeneratedKeys="true" keyProperty="letterId">
```
