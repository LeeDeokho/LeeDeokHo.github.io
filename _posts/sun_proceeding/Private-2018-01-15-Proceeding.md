---
layout: post
title: "2018-01-15-proceeding"
date: 2018-01-15 19:40:06
description: 1월 15일 회의록
tags: 
 - sun-proceeding
comments: true
---


## 회의 주제
1. 기능 우선 순위 정하기
2. 역할 분담
3. db 설계
4. 일정
5. 이슈

.

## 기능 우선 순위 정하기 & 역할 분담

1.  받은 편지함 & 중요 편지함 **(희범, 가림)**
    - 페이지네이션 구성
    - 편지 리스트 가져오기
    - 카드뷰 프론트엔드 구성
2. 편지 쓰기 **(덕호, 도형)**
    - 받는 사람 유효성 검사(일치하는 별명일 경우에만 전송 가능)
    - 파일 첨부
    - 유효날짜 & 제목 & 내용 
3. 편지 보기 **(덕호, 도형)**
    -  편지 내용 가져오기
    -  첨부파일 로컬에 저장하기    
 4. 로그인 & 회원 가입 **(상혁)** 
 5. 메인 화면 **(가림, 상혁)**
     - 왼쪽 네브바
     - 헤더
     - 프로필 관리
6. 보낸 편지함 **(희범)**
    * 편지 리스트 가져오기

__*팀원들 모두가 front에서 backend까지 모두 경험하기 위해 페이지별로 개발을 분담.*__

## 이슈
- 유효 날짜 지난 메일의 삭제는 어떻게 할 것인가 ?
    - 배치파일 이용해서 일정 시간마다 검색해서 삭제
    - 편지 목록 확인 시 유효기간 지난 메일 삭제
    - 혹은 SQL 내부에 사용할 수 있는 기능이 있는 지 ?