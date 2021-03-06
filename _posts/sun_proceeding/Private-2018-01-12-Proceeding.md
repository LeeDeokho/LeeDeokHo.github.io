---
layout: post
title: "2018-01-12-proceeding"
date: 2018-01-12 19:40:06
description: 1월 12일 회의록
tags: 
 - sun-proceeding
comments: true
---


# 루키햇님TF GROUPWARE 기획서
### 팀원
- 김가림, 김희범, 선도형, 이덕호, 함상혁
### 멘토님
- 조영환, 진혜진


## 개요

* 서비스명 : **핑퐁**
* 영문명 : _Pingpong_
* 서비스명의 의미 : 아이들이 탁구치듯 편지를 주고받는 모습을 비유적으로 표현

## 컨셉

* 메일 서비스를 처음 접하는 아이들이 편지처럼 가볍게 주고 받으며 메일의 사용법을 익힐 수 있도록 기획, 카드뷰 형식의 쉽고 직관적인 UI가 특징.

## 화면별 스펙 및 설명

### 1\. 로그인 \(pp\_101\)
![img]({{ '/assets/images/2018-01-12-mockup/로그인페이지.png' | relative_url }}){: .center-image }
* 사용자는 아이디와 패스워드를 입력 후 로그인 버튼을 누른다.
    * ID/PW가 일치하는 지를 검사한다.
        * 검증 성공시 메인 페이지로 이동한다.
        * 검증 실패시 'ID/PW를 확인해주세요' 팝업창 띄운다.

### 2\. 회원가입 \(pp\_201\, pp\_202\)

![img]({{ '/assets/images/2018-01-12-mockup/회원가입 페이지.png' | relative_url }}){: .center-image }
* ID는 4-15자, 별명은 2-15자, 비밀번호는 8-15자 조건을 만족해야 한다.
* ID는 영어, 숫자 조합으로 구성할 수 있음
* PW는 영어, 숫자로 구성(특수문자 사용불가)
* 비밀번호와 비밀번호 확인칸의 문자가 일치해야 한다.

![img]({{ '/assets/images/2018-01-12-mockup/회원가입 페이지 - 각 상태메세지 표시.png' | relative_url }}){: .center-image }
* 비밀번호와 비밀번호 확인칸의 문자가 일치하지 않다면 '비밀번호가 일치하지 않습니다'라는 문구가 표시된다.
* 입력한 아이디가 중복이라면 '이미 사용중인 아이디입니다'라는 문구가 표시된다.
* 입력한 아이디가 조건에 맞지 않다면 '아이디는 4-15자 사이로 입력해 주세요'라는 문구가 표시된다.
* 입력한 별명이 중복이라면 '이미 사용중인 별명입니다'라는 문구가 표시된다.
* 입력한 별명이 조건에 맞지 않다면 '별명은 2-15자 사이로 입력해주세요'라는 문구가 표시된다.
* 모든 조건을 만족하였을 때 회원가입 버튼을 누르면 로그인 페이지로 이동한다.

### 3\. 메인 페이지\(pp\_301\, pp\_302\)

![img]({{ '/assets/images/2018-01-12-mockup/메인 페이지.png' | relative_url }}){: .center-image }
![img]({{ '/assets/images/2018-01-12-mockup/메인 페이지-프로필아이콘클릭시.png' | relative_url }}){: .center-image }
* 상단바에서 서비스 로고와 사용자의 프로필 아이콘과 별명을 확인할 수 있다.
* 프로필 아이콘을 클릭하면 선택할 수 있는 아이콘이 드롭다운으로 표시된다.
* 사용자 별명 옆의 드롭다운 아이콘(▼)을 클릭하면 로그아웃 기능을 선택할 수 있다.
* 사용자는 왼쪽 전면의 네비게이션 바에서 기능을 선택할 수 있다.
    * 편지 쓰기
    * 받은 편지함
    * 보낸 편지함
    * 중요 편지함
* 네비게이션의 각 기능을 선택하면 해당 페이지로 이동하고, 아이콘 색깔이 변한다.
* 메인페이지의 디폴트 화면은 받은편지함이다.

### 4\. 편지 쓰기 \(pp\_401\, pp\_402\)

![img]({{ '/assets/images/2018-01-12-mockup/메일 보내기.png' | relative_url }}){: .center-image }
* 받는 사람, 제목, 내용을 기입할 수 있다.
    * 받는 사람들 사이에 "," 혹은 ";" 를 입력하여 사용자를 구분한다.
    * 받는 사람은 최대 40명으로 제한한다.

![img]({{ '/assets/images/2018-01-12-mockup/메일 보내기 - 파일 첨부 아이콘 클릭 시 파일 선택 팝업.png' | relative_url }}){: .center-image }
![img]({{ '/assets/images/2018-01-12-mockup/메일 보내기 - 파일 첨부시.png' | relative_url }}){: .center-image }
![img]({{ '/assets/images/2018-01-12-mockup/메일 보내기 - 유효날짜 인풋박스 클릭 시.png' | relative_url }}){: .center-image }


* 버튼을 눌러 편지에 파일을 첨부할 수 있다.
    * 각 파일은 최대 10MB 이다.
    * 한 번에 10개의 파일을 첨부할 수 있다.
    * 10개 전체를 합한 크기는 50MB를 넘을 수 없다.
    * 파일선택창에서 파일 선택을 완료하면 업로드를 하며, 메일은 모든 파일의 업로드 완료 후 전송가능하다.
        * 파일 업로드가 완료 되지 않은 상태에서는, 메일 전송 버튼이 비활성화된다.
    
* 편지의 유효기간을 설정할 수 있다.
    * 설정 하지 않거나 과거 날짜일 경우 유효기간이 없다.
    * 유효기간 설정시 설정한 기간이 지나면 받은 사람의 편지함에서 삭제된다.
* 보내기 버튼을 눌렀을 때 모든 조건을 만족한다면 메일을 보내고 메일 전송완료 페이지로 전환한다.
    * 받는 사람 아이디가 비어 있다면 팝업창을 띄워서 알려주고 원래 페이지로 돌아간다
    * 받는사람 중에 아이디나 별명이 없는 아이디라면 해당 계정에는 발송하지 않는다
    * 제목을 입력하지 않았다면 제목을 "제목없음" 으로 설정한다

### 5\. 받은 편지함\, 중요 편지함 \(pp\_501\)

![img]({{ '/assets/images/2018-01-12-mockup/메인 페이지 - 별명 클릭시 드롭다운.png' | relative_url }}){: .center-image }
![img]({{ '/assets/images/2018-01-12-mockup/중요 편지함.png' | relative_url }}){: .center-image }
* 각 편지는 카드뷰 형식으로 나타내고, 페이지당 5개씩 보여준다.
* 페이지네이션은 화면 하단의 페이지 번호와 next, prev 버튼을 이용하여 구성한다.
* 편지마다 보낸 사람, 제목, 수신 시간, 첨부파일 유무, 읽음 유무를 볼 수 있다.
    * 보낸 사람은 상대방의 프로필 아이콘과 별명이 표시된다.
    * 수신 시간에는 날짜와 시간을 표시한다. _ex) 1월 11일 오후 2시 30분_
    * 첨부파일 유무와 읽음 표시는 아이콘을 이용하여 표시한다.
* 각 편지의 휴지통 아이콘을 클릭하여 편지를 삭제할 수 있다.
    * 삭제시 팝업창으로 다시 한번 삭제 의사를 확인한다.
* 각 편지의 별표 아이콘을 클릭하여 편지의 중요도를 설정할 수 있다.
    * 별표를 누르면 해당 편지의 중요도가 설정된다.
* 중요 편지함의 경우 중요도가 설정된 편지만 보여준다.

### 6\. 보낸 편지함 \(pp\_601\)

![img]({{ '/assets/images/2018-01-12-mockup/보낸 편지함 - 상대방이 편지를 안 읽은 경우.png' | relative_url }}){: .center-image }
![img]({{ '/assets/images/2018-01-12-mockup/보낸 편지함 - 상대방이 편지를 읽은 경우.png' | relative_url }}){: .center-image }

* 각 편지는 카드뷰 형식으로 나타내고, 페이지당 5개씩 보여준다.
* 페이지네이션은 화면 하단의 페이지 번호와 next, prev 버튼을 이용하여 구성한다.
* 편지마다 받는 사람, 제목, 발신 시간, 첨부파일 유무, 상대방의 읽음 유무를 볼 수 있다.
    * 받는 사람은 상대방의 프로필 아이콘과 별명이 표시된다.
    * 발신 시간에는 날짜와 시간을 표시한다. _ex) 1월 11일 오후 2시 30분_
    * 첨부파일 유무와 읽음 표시는 아이콘을 이용하여 표시한다.
* 각 편지의 휴지통 아이콘을 클릭하여 편지를 삭제할 수 있다.
    * 삭제시 팝업창으로 다시 한번 삭제 의사를 확인한다.
* 각 편지의 별표 아이콘을 클릭하여 편지의 중요도를 설정할 수 있다.
    * 별표를 누르면 해당 편지의 중요도가 바뀐다.

### 7\. 편지 보기 \(pp\_701\)

![img]({{ '/assets/images/2018-01-12-mockup/메일 확인.png' | relative_url }}){: .center-image }
![img]({{ '/assets/images/2018-01-12-mockup/메일 확인 - 첨부 파일이 있을 경우.png' | relative_url }}){: .center-image }
* 편지의 상세 정보를 보여준다.
    * 제목
    * 중요도
    * 시간
    * 보낸 사람
        * 프로필
        * 별명
    * 첨부파일
    * 내용
* 답장하기를 눌러 보낸 사람에게 바로 편지를 쓸 수 있다.
    * 받는 사람에 대한 정보를 저장한채로, 편지쓰기 페이지로 이동한다.

### 프로젝트 완성 기준

* 기간 내에 기획서의 요구사항(기능)을 성공적으로 구현하는 것

### 추가 기능 고려

* 검색 기능
* 전체 삭제
* 사용자별 태깅
* 읽지 않은 편지 모아보기
* 메일 발신 시 웹상에서 마우스를 이용하여 그림을 그려 전송할 수 있는 기능.
* 메일 확인 시 카드뷰 형식인 메일이 편지처럼 펼쳐지는 기능
* 메일 발신 시 편지지 템플릿을 선택할 수 있는 기능(ex : 생일 파티 초대 메일...)
