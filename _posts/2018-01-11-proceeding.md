---
layout: post
title: "2018-01-11-proceeding"
date: 2018-01-11 19:40:06
description: 1월 11일 회의록
tags: 
 - sun-proceeding
comments: true
---


# 루키햇님 1월 11일 회의록 
---
* 회의 참석자 : 김가림, 김희범, 선도형, 이덕호, 함상혁
* 회의 주제 : 메일 프로젝트 기획 및 아이디어 회의

## 내용
---
* 메일 시스템의 주제 정하기
	* 아이들을 위한
		* 이름 스토밍 : 핑퐁
	
	* 노인분들을 위한
		* 노인분들은 메일 사용을 잘 못하시니까 노인분들도 쓸 수 있을만큼 쉽게 만들어서 쓸 수 있도록 도와드리자
		* 최대한 쉽고 간결하게
		* 이름 스토밍 :  

	* 음악(예술)인들을 위한
		* 메일에서 스트리밍으로 음악 재생
		* 각 초 마다 댓글 작성 기능
	
	* 맞춤법 검사(격식 차리기)
		* 템플릿 제공(상황에 맞는)(ex: 교수님한테 보낼 때, 거래처 직원에게 보낼 떄 등)
		* 이름 스토밍 : MMM(Manner Maketh Mail)

	* 이중 맞춤법 검사는 컨셉이라기 보다는 기능
	* __회의를 통해 아이들을 위한 서비스로 결정__



* ## MockUp
### 로그인 & 회원가입 관련
![img]({{ '/assets/images/2018-01-11-mockup/login.png' | relative_url }}){: .center-image }
* 로그인 & 회원가입
	1. 아이디가 있다면 아이디 패스워드를 입력후 로그인 버튼을 누른다.
	    * 아이디와 비밀번호를 제대로 입력했다면 메인페이지로 연결한다
  		* 일치하는 id,pw가 없다면 팝업창을 띄운다.
  	2. 아이디가 없다면 회원가입 버튼을 누르며 회원가입용 페이지로 연결한다.
	    
![img]({{ '/assets/images/2018-01-11-mockup/registerUser.png' | relative_url }}){: .center-image }
* 회원가입
	- 모든 조건을 만족했을때 회원가입 버튼을 누르면 회원가입이 된다.

![img]({{ '/assets/images/2018-01-11-mockup/registerUser-differentPwd.png' | relative_url }}){: .center-image }
* 회원가입 - 비밀번호 틀릴 시
	- 비밀번호 확인 텍스트와 비밀번호가 같지않으면 회원가입 할 수 없다
![img]({{ '/assets/images/2018-01-11-mockup/registerUser-repeated.png' | relative_url }}){: .center-image }
* 회원가입 - 중복된 값이 있을 경우
	- 아이디, 별명에 대해서는 중복확인을 하고 중복이 없을시 회원가입 할 수 잇다.

---
### 메인 페이지 프레임
![img]({{ '/assets/images/2018-01-11-mockup/main.png' | relative_url }}){: .center-image }
* 메인 페이지

![img]({{ '/assets/images/2018-01-11-mockup/main-clickedProfileIcon.png' | relative_url }}){: .center-image }
* 메인 페이지 - 사용자 프로필 아이콘 클릭 시 

![img]({{ '/assets/images/2018-01-11-mockup/main-clickedPerson.png' | relative_url }}){: .center-image }
* 메인 페이지 - 사용자 별명 클릭 시 


---
### 받은 편지함
![img]({{ '/assets/images/2018-01-11-mockup/main-checked.png' | relative_url }}){: .center-image }
* 받은 편지함 - 읽은 편지일 경우 

![img]({{ '/assets/images/2018-01-11-mockup/importantLetter.png' | relative_url }}){: .center-image }
* 중요 편지함

---
### 편지 보기
![img]({{ '/assets/images/2018-01-11-mockup/viewLetter.png' | relative_url }}){: .center-image }
* 편지 보기

---
### 편지 보내기 관련

![img]({{ '/assets/images/2018-01-11-mockup/sendLetter.png' | relative_url }}){: .center-image }
* 편지 보내기
	- 메일 보내는 기능

![img]({{ '/assets/images/2018-01-11-mockup/sendLetter-clickedFileAttach.png' | relative_url }}){: .center-image }
* 편지 보내기 - 파일 첨부
	- 파일 선택창 띄워서 파일 선
    - 선택 파일 리스트 히든(true/false)

![img]({{ '/assets/images/2018-01-11-mockup/sendLetter-success.png' | relative_url }}){: .center-image }
* 편지 보내기 - 성공 
	- 메일 보내기 성공 시 성공 페이지로 이동

![img]({{ '/assets/images/2018-01-11-mockup/sendLetter-fail.png' | relative_url }}){: .center-image }
* 편지 보내기 - 실패 
	- 메일 보내기 실패 시 알러트창 띄우기





