---
layout: post
title: "PushKit이란 ?"
date: 2018-03-13 00:40:06
description: PushKit을 분석하고 정리
tags: 
 - IOS
comments: true
---

## 목차 

- [PushKit이란](#PushKit이란)
- [PKPushType](#PkPushType)

## PushKitdlfks

- 푸시 알람을 보내 앱을 업데이트 하는 것.

PushKit 프레임워크는 특정한 종류(VoIP invitations, watchOS complication updates, and file provider change notifications)의 알림을 앱에 전송한다.

PushKit 프레임워크는 UserNotificatios와 달리 배지, 알림, 소리는 표시되지 않는다.

PushKit notifications는 user notifications에 비해 다음과 같은 이점이 있다.
- 앱이 실행 중이지 않으면알림을 받는 즉시 시스템이 자동으로 앱을 시작한다. silent user notifications를 사용할 수도 있지만, notification이 왔을 때 앱이 작동되지 않을 수도 있다.

- 앱이 백그라운드에서 실행 중인 경우에도 알림을 처리하도록 런타임이 제공된다.

- 장치는 PushKit notification을 받을 때에만 깨어난다. 이로 인해 배터리 수명을 개선할 수 있다.

- PushKit notifications에는 user notifications보다 더 많은 data가 포함될 수 있다.





## PkPushType

내가 원하는 것을 지원할 푸시 타입을 반영하는 상수

- watchOS complications를 위한 푸시 타입
    - swift
    ```swift
    static let complication: PKPushType
    ```
    - objectiveC
    ```objectiveC
    const PKPushType PKPushTypeComplication;
    ```



- file provider updates를 위한 푸시 타입
    - swift
    ```swift
    static let fileProvider: PKPushType
    ```
    - objectiveC
    ```objectiveC
    const PKPushType PKPushTypeFileProvider;
    ```

- VoIP를 위한 푸시 타입
    - swift
    ```swift
    static let voIP: PKPushType
    ```

    - objectiveC
    ```objectiveC
    const PKPushType PKPushTypeVoIP;
    ```


