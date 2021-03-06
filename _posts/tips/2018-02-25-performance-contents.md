---
layout: post
title: "Performance Testing Guidance for Web Applications를 읽고 정리"
date: 2018-02-25 19:40:06
description: Performance Testing Guidance for Web Applications를 읽고 정리
tags: 
 - tips
comments: true
---


## 전체 목록
- [Chapter 1을 읽고 성능 테스트의 정의를 정리하시오](#Chapter1을-읽고-성능-테스트의-정의를-정리하시오)
- [Chapter 2 를 읽고 성능 테스트의 종류를 정리하고, 해당 테스트가 어떤 상황에서 필요한지 직접 생각하여 정리하시오](#Chapter2를-읽고-성능-테스트의-종류를-정리하고,-해당-테스트가-어떤-상황에서-필요한지-직접-생각하여-정리하시오)
- [3장 운영체제](#3장-운영체제)
- [4장 네트워크](#4장-네트워크)
- [5장 스토리지](#5장-스토리지)
- [6장 구매 및 상담](#6장-구매-및-상담)
- [7장 데이터 센터](#7장-데이터-센터)
- [8장 솔루션과 보안](#8장-솔루션과-보안)
- [9장 인프라 운영](#9장-인프라-운영)
- [10장 대규모 인프라](#10장-대규모-인프라)
- [11장 인프라 엔지니어의 성장](#11장-인프라-엔지니어의-성장)

<hr>

## Chapter1을 읽고 성능 테스트의 정의를 정리하시오.

Chapter 1 - Fundamentals of Web Application Performance Testing

성능 테스트란 주어진 작업부하에서의 시스템의 응답성, 처리량, 안정성 및 확장성을 결정하기 위한 테스트 유형.

성능테스트는 일반적으로 아래의 여섯가지 경우를 수행하기 위해 수행 된다.
- 생산 준비 여부 평가
- 성과 기준에 대한 평가
- 여러 시스템 또는 시스템 구성의 성능 특성 비교
- 성능 문제의 원인 찾기
- 시스템 튜닝 지원
- 처리량 수준 찾기

### Core Activities of Performance Testing
성능 테스트는 일반적으로 시스템의 병목 현상을 파악하고 향후 테스트를위한 기준을 수립하고 성능 튜닝 노력을 지원하며 성과 목표 및 요구 사항을 준수하는지 확인하고 기타 성과 관련 데이터를 수집하여 이해 관계자가 정보에 근거한 의사 결정을 내릴 수 있도록 돕기 위해 수행. 
테스트중인 애플리케이션의 전반적인 품질 또한 성능 테스트 및 분석 결과를 통해 프로덕션 운영에 "적용"할 때 응용 프로그램을 지원하는 데 필요한 하드웨어 구성을 예측할 수 있습니다.


### Core Perpormance Testing Activities
1. 테스트 환경 식별
    - 실제 테스트 환경과 프로덕션 환경은 물론 테스트 팀에서 사용할 수있는 도구와 리소스를 확인. 물리적 환경에는 하드웨어, 소프트웨어 및 네트워크 구성이 포함. 처음부터 전체 테스트 환경을 철저히 이해하면보다 효율적인 테스트 설계 및 계획이 가능하며 프로젝트 초기에 테스트 문제를 파악하는 데 도움이 된다. 경우에 따라이 프로세스는 프로젝트의 수명주기 전체에 걸쳐 정기적으로 재검토되어야 한다.
2. 성과 수용 기준 파악
    - 응답 시간, 처리량 및 리소스 사용 목표 및 제약 조건을 식별. 일반적으로 응답 시간은 사용자의 관심사이며 처리량은 비즈니스 관심사이며 리소스 사용은 시스템 관련 사항. 또한 목표 및 제약 조건에 포착되지 않을 수도있는 프로젝트 성공 기준을 확인해야한다. 예를 들어 성능 테스트를 사용하여 가장 바람직한 성능 특성을 초래할 구성 설정 조합을 평가할 수 있다.
3. 계획 및 설계 테스트
    - 주요 시나리오를 식별하고 대표 사용자 간의 다양성을 결정하며 그 변동성을 시뮬레이션하는 방법, 테스트 데이터를 정의하는 방법 및 수집 할 메트릭을 설정하는 방법. 이 정보를 하나 이상의 시스템 사용 모델로 통합하여 구현, 실행 및 분석.
4. 테스트 환경 구성
    - 기능 및 구성 요소를 테스트 할 수있게됨에 따라 각 전략을 실행하는 데 필요한 테스트 환경, 도구 및 리소스를 준비. 필요에 따라 테스트 환경이 자원 모니터링을 위해 인스트루먼트되었는지 확인.
5. 테스트 디자인 구현
    - 테스트 디자인에 따라 성능 테스트 개발
6. 테스트 실행
    - 테스트를 실행하고 모니터링해야된다. 테스트, 테스트 데이터 및 수집 결과의 유효성을 검사한다. 테스트 및 테스트 환경을 모니터링 하면서 분석을 위해 검증된 테스트를 실행한다.
7. 분석, 보고 및 리테스트
    - 결과 데이터를 통합하고 공유하자. 모든 메트릭 값이 허용 된 한도 내에 있고 설정된 임계 값 중 하나도 위반되지 않았으며 원하는 모든 정보가 수집 된 경우 해당 특정 구성에 대한 특정 시나리오 테스트를 완료했습니다.

### Why Do Performance Testing?
가장 높은 수준에서 비용, 기회 비용, 연속성 및 기업 평판과 관련된 하나 이상의 위험을 해결하기 위해 성능 테스트가 거의 항상 수행된다. 
- 출시 준비 여부 평가
    - 프로덕션 환경에서 응용 프로그램의 성능 특성을 예측 또는 예측하고 이러한 예측을 기반으로 성능 문제를 해결할지 여부를 평가할 수 있다. 이러한 예측은 응용 프로그램의 릴리스 준비 여부 또는 향후 성장을 처리 할 수 있는지 여부 또는 릴리스 전에 성능 향상 / 하드웨어 업그레이드가 필요한지 여부를 결정하는 이해 관계자에게 유용하다.
    - 시스템의 성능 특성에 대한 사용자 불만의 가능성을 나타내는 데이터를 제공한다.
    - 확장 성 또는 안정성 문제 또는 사용자가 애플리케이션 응답 시간에 만족하지않는 문제로 인한 매출 손실 또는 브랜드 신뢰도 손상 예측에 도움이되는 데이터를 제공합니다.
- 인프라 적합성 평가
    - 현재 용량의 적절성 평가
    - 안정성의 수용성 결정
    - 응용 프로그램의 인프라 용량을 결정하고 수용 가능한 응용 프로그램 성능을 제공하는 데 필요한 향후 자원을 결정.
    - 서로 다른 시스템 구성을 비교하여 응용 프로그램과 비즈니스 모두에 가장 적합한 프로그램을 결정.
    - 예산에 따른 리소스 사용 제약 내에서 애플리케이션이 원하는 성능 특성을 나타내는 지 확인.
- 개발 된 소프트웨어 성능의 적절성 평가 
    - 소프트웨어 변경 전후의 응용 프로그램의 원하는 성능 특성 결정.
    - 애플리케이션의 현재 및 원하는 성능 특성을 비교.
- 성능 튜닝의 효율성 향상
    - 다양한 부하 수준에서 애플리케이션의 동작 분석.
    - 애플리케이션의 병목 현상 식별.
    - 프로덕션 릴리스 전에 제품의 속도, 확장 성 및 안정성과 관련된 정보를 제공하므로 시스템을 조정할지 여부와시기에 대한 정보에 근거한 결정을 내릴 수 있다.


### Project Context
성능 테스트 프로젝트가 성공하려면 성능 테스트 방법과 테스트 자체가 프로젝트 컨텍스트와 관련이 있어야합니다. 프로젝트 컨텍스트에 대한 이해가 없으면 성능 테스터는 성능 테스터 또는 테스트 팀이 중요하다고 생각하는 항목에만 집중할 수밖에 없으며 종종 중요한 시간과 시간 낭비, 좌절, 갈등으로 이어집니다.

프로젝트 컨텍스트는 프로젝트 성공을 달성하는 데 관련이 있거나 앞으로 나아갈 수있는 것들입니다. 여기에는 다음 사항이 포함될 수 있습니다.
- 프로젝트의 전반적인 비전 또는 의도
- 성능 테스트 목적
- 성과 달성 기준
- 개발 라이프 사이클
- 프로젝트 일정
- 프로젝트 예싼
- 사용 가능한 도구 및 환경
- 성능 테스터와 팀의 기술 세트
- 감지 된 성능 문제의 우선 순위
- 제대로 수행되지 않는 응용 프로그램 배포의 비즈니스 영향

### 성능 테스트와 튜닝의 관계
용인 할 수없는 것으로 간주되는 시스템 또는 애플리케이션 특성을 종단 간 성능 테스트에서 확인할 때 많은 팀이 성능 테스트에서 성능 튜닝으로 초점을 전환하여 응용 프로그램을 정상적으로 수행하는 데 필요한 것을 발견합니다. 팀은 성능 기준이 충족되었지만 팀이 플랫폼 헤드 룸을 높이고 필요한 하드웨어의 양을 줄이며 더 나아가 시스템 성능을 향상시키기 위해 사용되는 리소스의 양을 줄이기를 원할 때 초점을 조정할 수도 있습니다.

### 튜닝 프로세스 개요
튜닝은 일반적으로 프로젝트가 따르는 성능 테스트 접근법과는 별도로 반복되는 반복적인 프로세스를 따릅니다. 다음은 일반적인 튜닝 과정에 대한 간략한 개요입니다.

- 테스트 프로세스의 시작시 구성 및 테스트 결과를 알고 재현 할 수 있도록 잘 정의되고 제어 된 테스트 환경에 시스템 또는 응용 프로그램을 배포하여 테스트를 수행합니다.
- 테스트에서 허용 할 수없는 것으로 간주되는 성능 특성이 밝혀지면 성능 테스트 및 조정 팀은 테스트 환경 및 / 또는 응용 프로그램에 변경 사항을 적용해야하는 진단 및 치료 단계 (조정)를 시작합니다. 진단 목적으로 문제를 확대하기 위해 의도적으로 고안된 임시 변경을 수행하거나 테스트 환경을 변경하여 이러한 변경으로 인해 성능이 향상되는지 여부를 확인하는 것은 흔하지 않습니다.
- 협력 테스트 및 조정 팀은 일반적으로 조정 단계의 효과를 극대화하기 위해 테스트 환경에 대해 완전하고 독점적 인 제어를받습니다.
- 수정 테스트의 영향을 측정하기 위해 테스트 환경을 변경할 때마다 성능 테스트가 실행되거나 다시 실행됩니다.
- 튜닝 프로세스는 일반적으로 신속한 변경과 테스트를 거칩니다. 이 프로세스는 협업 테스트 및 조정 팀이 완전히 사용 가능하지 않고 조정 단계에서이 작업에 전념 할 경우 기하 급수적으로 더 많은 시간이 걸릴 수 있습니다.
- 조정 단계가 완료되면 일반적으로 테스트 환경이 초기 상태로 재설정되고 성공적으로 수정 된 변경 사항이 다시 적용되며 실패한 수정 사항 (임시 계측 및 진단 변경 사항 포함)은 무시됩니다. 그런 다음 올바른 테스트가 이루어 졌음을 입증하기 위해 성능 테스트를 반복해야합니다. 최소한의 생산 환경에 대한 새로운 기대치를 반영하기 위해 테스트 환경 자체가 변경되는 경우도있을 수 있습니다. 이것은 드물지만 튜닝 작업의 잠재적 인 결과입니다.

### 성능, 부하 및 스트레스 테스트
- Performance Testing(성능 시험)
    - 이 유형의 테스트는 테스트중인 시스템 또는 응용 프로그램의 속도, 확장 성 및 / 또는 안정성 특성을 결정하거나 유효성을 검사합니다. 성과는 프로젝트 또는 제품의 성능 목표를 충족시키는 응답 시간, 처리량 및 자원 활용 수준 달성과 관련됩니다. 이 가이드에서 성능 테스트는 성능 관련 테스트의 다른 모든 하위 범주의 상위 집합을 나타냅니다.
- Load testing(부하 테스트)
    - 성능 테스트의 하위 범주는 생산 작업 중에 예상되는 작업로드 및로드 볼륨에 종속 될 때 테스트중인 시스템 또는 응용 프로그램의 성능 특성을 결정하거나 유효성을 검증하는 데 초점을 맞춥니다.
- Stress testing(스트레스 테스트)
    - 성능 테스트의 하위 범주는 생산 운영 중에 예상되는 조건을 초과 할 경우 테스트중인 시스템 또는 응용 프로그램의 성능 특성을 결정하거나 검증하는 데 초점을 맞 춥니 다. 스트레스 테스트에는 제한된 메모리, 불충분 한 디스크 공간 또는 서버 장애와 같은 다른 스트레스 상황에 처했을 때 테스트중인 시스템 또는 애플리케이션의 성능 특성을 결정하거나 검증하는 데 중점을 둔 테스트가 포함될 수도 있습니다. 이 테스트는 응용 프로그램이 실패하는 조건, 실패하는 방법 및 임박한 실패를 경고하기 위해 모니터링 할 수있는 표시기를 결정하도록 설계되었습니다.


## Baselines (기준선)
기준선을 만드는 것은 시스템 또는 응용 프로그램의 성능 향상을위한 후속 변경의 효과를 평가할 목적으로 성능 메트릭 데이터를 캡처하기 위해 일련의 테스트를 실행하는 프로세스입니다. 기준선의 중요한 측면은 비교를 위해 특별히 변형 된 것을 제외한 모든 특성 및 구성 옵션이 불변 상태를 유지해야한다는 것입니다. 기준선과의 비교를 위해 의도적으로 변경되지 않은 시스템의 일부가 변경되면 기준선 측정이 더 이상 유효한 비교 근거가되지 않습니다.
웹 응용 프로그램과 관련하여 기준선을 사용하여 성능이 향상되는지 또는 감소 하는지를 결정하고 다른 빌드 및 버전에서 편차를 찾을 수 있습니다. 예를 들어로드 시간, 시간당 처리 된 트랜잭션 수, 시간당 처리 된 웹 페이지 수 및 메모리 사용량 및 프로세서 사용량과 같은 리소스 사용률을 측정 할 수 있습니다. 기준선 사용에 대한 몇 가지 고려 사항은 다음과 같습니다.

- 시스템, 구성 요소 또는 응용 프로그램에 대한 기준선을 만들 수 있습니다.
    -  베이스 라인은 데이터베이스, 웹 서비스 등 응용 프로그램의 여러 계층에 대해 만들 수도 있습니다.
- 기준선은 미래의 최적화 또는 회귀를 추적하기 위해 비교 기준을 설정할 수 있습니다.
    - 환경 및 작업 부하 특성으로 인해 테스트 결과에서 상당한 변동이 발생할 수 있으므로 기준 결과를 반복해서 확인할 수 있어야합니다.
- 베이스 라인은 성과 변화를 파악하는 데 도움이 될 수 있습니다.
    - 베이스 라인은 개발 팀이 개발 수명주기 동안 성능 저하 또는 최적화를 반영하는 성능 변화를 식별하는 데 도움을 줄 수 있습니다. 잘 알려진 상태 또는 구성과 비교하여 이러한 변경 사항을 확인하면 성능 문제를보다 쉽게 ​​해결할 수 있습니다.
- 기준선 자산은 재사용 가능해야합니다.
    - 베이스 라인은 재사용 가능한 테스트 자산 집합을 사용하여 생성되는 경우 가장 가치가 있습니다. 이러한 테스트가 반복 가능하고 실행 가능한 작업 부하 특성을 정확하게 시뮬레이션하는 것이 중요합니다.
- 베이스 라인은 메트릭입니다.
    - 기본 결과는 응답 시간, 프로세서 용량, 메모리 사용량, 디스크 용량 및 네트워크 대역폭과 같은 광범위한 주요 성능 지표를 사용하여 명확히 나타낼 수 있습니다.
- 베이스 라인은 공유 참조 프레임의 역할을합니다.
    - 기본 결과를 공유하면 팀이 애플리케이션 또는 구성 요소의 성능 특성에 대한 지식을 습득 할 수있는 공통 저장소를 구축 할 수 있습니다.
- 기준선을 지나치게 일반화하지 마십시오.
    - 프로젝트에서 응용 프로그램의 주요 리엔지니어링이 필요하면 해당 응용 프로그램을 테스트하기위한 기준을 다시 설정해야합니다. 기준선은 응용 프로그램에 따라 다르며 다른 버전의 성능을 비교하는 데 가장 유용합니다. 때로는 후속 버전의 응용 프로그램이 너무 다르기 때문에 이전 기준선이 더 이상 유효하지 않습니다.
- 응용 프로그램의 동작을 파악합니다.
    - 기준선을 만들 때 응용 프로그램의 동작을 완전히 이해하는 것이 좋습니다. 최적화 목표에 초점을 맞춘 시스템을 변경하기 전에 그렇게하지 않으면 종종 비생산적입니다.
- 베이스 라인이 진화합니다.
    - 베이스 라인을 처음 캡처 한 이후로 변경된 사항 때문에베이스 라인을 재정의해야 할 때가 있습니다.

### Terminology

1. Capacity
    - 시스템의 용량은 미리 결정된 핵심 성능 수용 기준을 위반하지 않고 처리 할 수있는 총 작업량입니다.
2. Capacity Test
    - 용량 테스트는 서버의 궁극적 인 오류 지점을 결정하여 부하 테스트를 보완하는 반면 부하 테스트는 다양한 수준의로드 및 트래픽 패턴에서 결과를 모니터링합니다. 용량 테스트는 용량 계획과 함께 수행되며 사용자 기반 증가 또는 데이터 증가와 같은 미래의 성장을 계획하는 데 사용됩니다. 예를 들어 향후로드를 수용하려면 추가 리소스 (예 : 프로세서 용량, 메모리 사용량, 디스크 용량 또는
네트워크 대역폭)은 향후 사용 수준을 지원하는 데 필요합니다. 용량 테스트를 통해 스케일 업 전략을 식별하여 스케일 업 또는 스케일 아웃해야하는지 여부를 결정할 수 있습니다.
3. Component test
    - 구성 요소 테스트는 응용 프로그램의 아키텍처 구성 요소를 대상으로하는 성능 테스트입니다. 일반적으로 테스트되는 구성 요소에는 서버, 데이터베이스, 네트워크, 방화벽 및 저장 장치가 포함됩니다.
4. Endurance test
    - 내구성 테스트는 장기간에 걸쳐 생산 작업 중에 예상되는 작업량 모델 및 부하량에 노출 될 때 테스트중인 제품의 성능 특성을 결정하거나 검증하는 데 중점을 둔 성능 테스트 유형입니다. 내구성 테스트는 부하 테스트의 하위 집합입니다.
5. Investigation
    - 조사는 제품 품질을 결정하거나 향상시키는 데 가치가있을 수있는 테스트중인 제품의 속도, 확장 성 및 / 또는 안정성 특성과 관련된 정보 수집에 기반을 둔 활동입니다. 조사는 하나 이상의 관측 된 성능 문제의 근본 원인에 관한 가설을 입증하거나 반증하기 위해 자주 사용됩니다.
6. Latency
    - 대기 시간은 요청 실행을 완료하는 데 걸리는 시간을 나타내는 응답의 측정 단위입니다. 대기 시간은 여러 대기 시간 또는 하위 작업의 합계를 나타낼 수도 있습니다.
7. Metrics
    - 메트릭은 일반적으로 이해되는 척도로 표현 된 성능 테스트를 실행하여 얻은 측정입니다. 성능 테스트를 통해 일반적으로 얻어지는 일부 메트릭에는 시간 경과에 따른 프로세서 사용률 및로드 별 메모리 사용량이 포함됩니다.
8. Performance
    - 성능이란 응용 프로그램의 응답 시간, 처리량 및 자원 사용률 수준에 관한 정보를 말합니다.
9. Performance test 
    - 성능 테스트는 테스트중인 제품의 속도, 확장 성 및 / 또는 안정성 특성을 확인하거나 검증하기 위해 수행 된 기술 조사입니다. 성능 테스트는이 장에 설명 된 성능 테스트의 다른 모든 하위 범주를 포함하는 수퍼 셋입니다.
10. Performance budgets or allocations
    - 성능 예산 (또는 할당)은 개발자가 구성 요소에 허용되는 리소스 소비량과 관련하여 개발자에게 부여되는 제약 사항입니다.
11. Performance goals
    - 성과 목표는 특정 상황에서 협상 할 수 있지만 팀이 제품 출시 전에 만나기를 원하는 기준입니다. 예를 들어 특정 트랜잭션에 대해 응답 시간 목표를 3 초로 설정했지만 실제 응답 시간이 3.3 초인 경우 이해 관계자가 응용 프로그램을 릴리스하고 향후 릴리스에서 해당 트랜잭션의 성능 조정을 연기 할 가능성이 있습니다.
12. Performance objectives 
    - 성능 목표는 대개 응답 시간, 처리량 (초당 트랜잭션) 및 자원 활용도 수준으로 지정되며 일반적으로 사용자 만족도와 직접적으로 관련된 지표에 초점을 둡니다.
13. Performance requirements
    - 성능 요구 사항은 계약상의 의무, SLA (Service Level Agreement) 또는 고정 된 비즈니스 요구로 인해 절대적으로 협상 할 수없는 기준입니다. 조건이 통과 될 때까지 릴리스를 지연시키려는 결정에 의문의 여지없이 발생할 수있는 성능 기준은 절대적으로 요구되는 것은 아니므로 요구 사항은 아닙니다.
14. Performance targets 
    - 성능 목표는 일반적으로 응답 시간, 처리량 및 리소스 사용 수준 측면에서 지정된 특정 조건 집합에서 프로젝트에 대해 확인 된 메트릭에 대해 원하는 값입니다. 리소스 사용 수준에는 응용 프로그램에서 사용하는 프로세서 용량, 메모리, 디스크 I / O 및 네트워크 I / O의 양이 포함됩니다. 성과 목표는 일반적으로 프로젝트 목표와 동일합니다.
15. Performance testing objectives
    - 성능 테스트 목적은 제품 품질을 결정하거나 향상시키는 데 가치가 있다고 예상되는 성능 테스트 프로세스를 통해 수집 된 데이터를 의미합니다. 그러나 이러한 목표는 반드시 정량적이거나 성능 요구 사항, 목표 또는 명시된 서비스 품질 (QoS) 사양과 직접 관련이있는 것은 아닙니다.
16. Performance thresholds
    - 성능 임계 값은 일반적으로 응답 시간, 처리량 (초당 트랜잭션) 및 자원 활용 수준의 측면에서 지정된 프로젝트에 대해 식별 된 메트릭의 최대 허용 값입니다. 리소스 사용 수준에는 응용 프로그램에서 사용하는 프로세서 용량, 메모리, 디스크 I / O 및 네트워크 I / O의 양이 포함됩니다. 성능 임계 값은 일반적으로 요구 사항과 동일합니다.
17. Resource utilization
    - 리소스 사용률은 시스템 리소스 측면에서 프로젝트 비용입니다. 주요 리소스는 프로세서, 메모리, 디스크 I / O 및 네트워크 I / O입니다.
18. Response time
    - 응답 시간은 응용 프로그램이나 서브 시스템이 클라이언트 요청에 얼마나 반응하는지 측정하는 것입니다.
19. Saturation
    - 채도는 자원이 완전히 활용 된 시점을 나타냅니다.
20. Scalability
    - 확장 성은 프로세서, 메모리 및 저장소 용량과 같은 리소스를 추가하여 성능에 악영향을 미치지 않으면 서 추가 작업 부하를 처리 할 수있는 응용 프로그램의 기능을 나타냅니다.
21. Scenarios
    - 성능 테스트의 맥락에서 시나리오는 응용 프로그램의 일련의 단계입니다. 시나리오는 제품 카탈로그 검색, 장바구니에 항목 추가 또는 주문하기와 같은 유스 케이스 또는 비즈니스 기능을 나타낼 수 있습니다.
22. Smoke test
    - 스모크 테스트는 애플리케이션이 정상 부하 상태에서 작업을 수행 할 수 있는지 확인하기위한 성능 테스트의 초기 실행입니다.
23. Spike test
    - 스파이크 테스트는 예상되는 생산 작업을 넘어 단기간 동안 반복적으로 증가하는 워크로드 모델 및로드 볼륨에 종속 될 때 테스트중인 제품의 성능 특성을 결정하거나 검증하는 데 중점을 둔 성능 테스트 유형입니다. 스파이크 테스트는 스트레스 테스트의 하위 집합입니다.
24. Stability
    - 성능 테스트와 관련하여 안정성은 다양한 조건에서 시스템의 전반적인 신뢰성, 견고성, 기능 및 데이터 무결성, 가용성 및 일관성을 나타냅니다.
25. Stress test
    - 스트레스 테스트는 정상 또는 최대로드 조건을 초과하여 푸시 될 때 응용 프로그램의 동작을 평가하기 위해 설계된 성능 테스트 유형입니다. 스트레스 테스트의 목표는 높은 부하 조건에서만 나타나는 응용 프로그램 버그를 밝히는 것입니다. 이러한 버그에는 동기화 문제, 경쟁 조건 및 메모리 누수 같은 것들이 포함될 수 있습니다. 스트레스 테스트를 통해 응용 프로그램의 약점을 식별하고 극단적 인 부하 조건에서 응용 프로그램이 어떻게 작동 하는지를 보여줍니다.
26. Throughput
    - 처리량은 시간당 처리 할 수있는 작업 단위 수입니다. 예를 들어, 초당 요청, 하루 당 호출, 초당 히트 수, 일년 보고서 등
27. Unit test
    - 성능 테스트의 컨텍스트에서 단위 테스트는 성능 특성에 중점을 둔 상태에서 응용 프로그램의 기존 코드 전체의 논리적 하위 집합 인 코드 모듈을 대상으로하는 테스트입니다. 일반적으로 테스트되는 모듈함수, 프로 시저, 루틴, 객체, 메소드 및 클래스를 포함합니다. 성능 단위 테스트는 테스트중인 코드 모듈을 작성한 개발자가 자주 만들고 수행합니다. 
28. Utilization
    - 성능 테스트의 컨텍스트에서 사용률은 리소스가 사용자 요청을 처리하는 데 소요되는 시간의 백분율입니다. 나머지 시간 비율은 유휴 시간으로 간주됩니다.
29. Validation test
    - 유효성 검사 테스트는 테스트중인 제품의 속도, 확장 성 및 / 또는 안정성 특성을 해당 제품에 대해 설정되거나 추정 된 기대치와 비교합니다.
30. Workload
    - 작업량은 동시성 및 / 또는 데이터 입력과 관련하여 사용 패턴을 시뮬레이션하기 위해 시스템, 응용 프로그램 또는 구성 요소에 적용되는 자극입니다. 작업 부하에는 총 사용자 수, 동시 활성 사용자, 데이터 볼륨 및 트랜잭션 볼륨이 트랜잭션 믹스와 함께 포함됩니다. 성능 모델링을 위해 작업 부하를 개별 시나리오와 연관시킵니다.

### 요약

성능 테스트는 시스템의 병목 현상을 파악하고 향후 테스트를위한 기준을 수립하며 성능 조정 노력을 지원하고 성능 목표 및 요구 사항을 준수하는지 확인하는 데 도움이됩니다. 개발 수명주기 초반에 성능 테스트를 포함하면 프로젝트에 상당한 가치를 부여하는 경향이 있습니다.
성능 테스트 프로젝트가 성공하려면 테스트가 프로젝트의 컨텍스트와 관련이 있어야하며, 이는 실제로 중요한 항목에 집중하는 데 도움이됩니다.
성능 특성을 수용 할 수없는 경우 일반적으로 성능 테스트에서 성능 조정으로 초점을 이동하여 응용 프로그램을 정상적으로 수행 할 수 있습니다. 사용중인 자원의 양을 줄이고 시스템 성능을 더 향상시키려는 경우 조정에 중점을 둘 것입니다.
성능, 부하 및 스트레스 테스트는 성능 테스트의 하위 범주이며 각각 다른 목적으로 사용됩니다.
성능 향상을위한 시스템 또는 응용 프로그램의 변경 효과를 평가하기위한 기준선을 작성하면 일반적으로 프로젝트 효율성이 향상됩니다.

## Chapter2를 읽고 성능 테스트의 종류를 정리하고, 해당 테스트가 어떤 상황에서 필요한지 직접 생각하여 정리하시오

### Chapter 2 – Types of Performance Testing

### 목표
- 다양한 유형의 성능 테스트에 대해 알아보십시오.
- 각 유형의 성능 테스트와 관련된 가치와 이점을 이해하십시오.
- 각 유형의 성능 테스트의 잠재적인 단점을 이해하십시오.

### 개요
성능 테스트는 다양한 유형의 성능 관련 테스트를 지칭 할 수있는 일반적인 용어입니다. 각 테스트는 특정 문제 영역을 다루고 자체 이점, 위험 및 문제점을 제공합니다.
이 장에서는 몇 가지 일반적인 유형 또는 성능 관련 테스트 범주와 관련된 혜택 및 프로젝트 위험을 정의하고 설명하고 설명합니다. 이 장을 사용하면 확립 된 팀 내에서도 이러한 용어의 오용과 오해를 극복 할 수 있습니다.

### 이 챕터를 사용하는 방법
이 장을 사용하여 다양한 유형의 성능 관련 테스트를 이해하십시오. 이를 통해 팀은 현재 위험, 우려 사항 또는 테스트 결과를 기반으로 특정 프로젝트에 가치를 더할 수있는 성과 관련 테스트 유형을 결정하는 데 도움을줍니다. 이 장을 최대한 활용하려면 다음을 수행하십시오.
- "주요 성능 유형 테스트"섹션을 사용하여 특정 유형의 테스트가 특정 관심사와 가장 관련이 있는지에 대한 정보에 입각 한 결정을 내리고 다양한 테스트 유형 간의 균형을 맞춰보십시오.
- "핵심 성과 테스트 유형별 혜택 요약표"섹션을 사용하여 특정 유형의 테스트의 이점뿐만 아니라 해당 유형의 전문성 테스트 팀이 적절하게 해결하지 못할 수있는 문제점 및 우려 영역을 고려하도록하십시오. .
- "추가 개념 / 용어"섹션을 사용하여 프로젝트에 가치를 더할 수있는 추가 성능 테스트 유형을 파악하고 특정 컨텍스트 외부의 사람들과 성능 테스트에 대한 대화에 참여할 수있는 능력을 향상 시키십시오.

### Performance Testing
성능 테스트는 테스트중인 제품의 속도, 확장 성 및 / 또는 안정성 특성을 결정하거나 검증하기 위해 수행 된 기술 조사로 정의됩니다. 테스트 및 튜닝과 같은 성능 관련 활동은 테스트중인 애플리케이션의 성능 목표를 충족시키는 응답 시간, 처리량 및 리소스 사용 수준 달성과 관련이 있습니다. 성능 테스트는 다양한 하위 집합 전체를 포괄하는 일반적인 용어이므로이 장의 다른 성능 테스트 유형에 나열된 모든 가치와 이점은 일반적으로 성능 테스트의 잠재적 이점으로 간주 될 수 있습니다.


### 성능 테스트의 주요 유형
다음은 웹 응용 프로그램의 가장 일반적인 유형의 성능 테스트입니다.

1. Performance test 
- Purpose
    - 속도, 확장 성 및 / 또는 안정성을 결정하거나 검증합니다.
- Notes
    - 성능 테스트는 테스트중인 제품의 응답 성, 속도, 확장 성 및 / 또는 안정성 특성을 결정하거나 검증하기 위해 수행 된 기술 조사입니다  

2. Load test 
- Purpose 
    - 정상 및 최대로드 조건에서 응용 프로그램 동작을 확인합니다. 
- Notes
    - 부하 테스트는 응용 프로그램이 원하는 성능 목표를 충족시킬 수 있는지 확인하기 위해 수행됩니다. 이러한 성능 목표는 SLA (서비스 수준 계약)에서 지정되는 경우가 많습니다. 부하 테스트를 사용하면 응답 시간, 처리 속도 및 자원 사용 수준을 측정하고 중단 점이 최대로드 조건 아래에서 발생한다고 가정하여 응용 프로그램의 중단 점을 식별 할 수 있습니다. 
    - 내구성 테스트는 부하 테스트의 하위 집합입니다. 내구성 테스트는 장기간에 걸쳐 생산 작업 중에 예상되는 작업량 모델 및 부하량에 노출 될 때 테스트중인 제품의 성능 특성을 결정하거나 검증하는 데 중점을 둔 성능 테스트 유형입니다.
    - 내구성 시험은 MTBF (Mean Time Between Failure), MTTF (Mean Time To Failure) 및 유사한 측정법을 계산하는 데 사용될 수 있습니다.

3. Stress test
- Purpose
    - 응용 프로그램의 동작이 정상 또는 최대로드 조건을 초과하여 푸시 될 때 응용 프로그램의 동작을 확인하거나 확인합니다.
- Notes
    - 스트레스 테스트의 목표는 높은 부하 조건에서만 나타나는 응용 프로그램 버그를 밝히는 것입니다. 이러한 버그에는 동기화 문제, 경쟁 조건 및 메모리 누수 같은 것들이 포함될 수 있습니다. 스트레스 테스트를 통해 응용 프로그램의 약점을 식별하고 극단적 인 부하 조건에서 응용 프로그램이 어떻게 작동 하는지를 보여줍니다.
    - 스파이크 테스트는 스트레스 테스트의 하위 집합입니다. 스파이크 테스트는 짧은 시간 동안 예상되는 생산 작업 이상으로 반복적으로 증가하는 워크로드 모델 및로드 볼륨에 종속 될 때 테스트중인 제품의 성능 특성을 결정하거나 검증하는 데 중점을 둔 성능 테스트 유형입니다.

4. Capacity test
- Purpose
    - 주어진 시스템이 얼마나 많은 사용자 및 / 또는 트랜잭션을 지원하는지 결정하고 성능 목표를 달성합니다.
- Notes
    - 용량 테스트는 용량 계획과 함께 수행되며 사용자 기반 증가 또는 데이터 증가와 같은 미래 성장을 계획하는 데 사용됩니다. 예를 들어 향후로드를 수용하려면 향후 사용 수준을 지원하기 위해 추가 리소스 (예 : 프로세서 용량, 메모리 사용량, 디스크 용량 또는 네트워크 대역폭)가 얼마나 필요한지 알아야합니다.
    용량 테스트를 통해 스케일 업 전략을 식별하여 스케일 업 또는 스케일 아웃해야하는지 여부를 결정할 수 있습니다.



웹 응용 프로그램과 관련된 가장 일반적인 성능 문제는 "충분히 빠를까요?", "모든 고객을 지원합니까?", "문제가 발생하면 어떻게됩니까?", "언제 계획을 세워야합니까? 나는 더 많은 고객을 얻는다? ". 일상 대화에서 대부분의 사람들은 성능 테스트에 "충분히 빠름"을 연결하고 "현재 / 예상 사용자 기반을"부하 테스트 ","스트레스 테스트와 함께 잘못 처리 "및"용량 확장 테스트를 통해 향후 성장 계획 "과 관련시킵니다. 집합 적으로 이러한 위험은 웹 응용 프로그램의 네 가지 핵심 
성능 테스트 유형의 기초를 형성합니다.

### 주요 성능 테스트 유형별 혜택 요약 매트릭스

| Term | Benefits | Challenges and Areas Not Addressed |
|------|----------|------------------------------------|

1. Performance test
- Benefits
    - 애플리케이션의 속도, 확장 성 및 안정성 특성을 결정함으로써 올바른 비즈니스 결정을 내리는 데 필요한 정보를 제공합니다.
    - 성과와 관련된 기대와 현실의 불일치를 확인합니다.
    - 시스템의 사용자가 응용 프로그램의 성능 특성에 만족하는지 판단하는 데 중점을 둡니다.
    - 튜닝, 용량 계획 및 최적화 작업을 지원합니다.
- Challenges and Areas Not Addressed
    - 로드시에만 나타나는 일부 기능 결함을 감지하지 못할 수 있습니다.
    - 신중하게 설계되고 검증되지 않으면 매우 적은 수의 생산 시나리오에서만 성능 특성을 나타낼 수 있습니다.
    - 테스트가 프로덕션 하드웨어에서 수행되지 않는 한 사용자가 사용할 동일한 시스템에서 결과에 항상 어느 정도의 불확실성이 있습니다.

2. Load test
- Benefits
    - 예상 최대 생산로드를 지원하는 데 필요한 처리량을 결정합니다.
    - 하드웨어 환경의 적합성을 결정합니다.
    - 로드 밸런서의 적합성을 평가합니다.
    - 동시성 문제를 감지합니다.
    - 로드 중 기능 오류를 감지합니다.
    - 확장 성 및 용량 계획 목적으로 데이터를 수집합니다.
    - 성능이 저하되기 전에 애플리케이션이 처리 할 수있는 사용자 수를 결정할 수 있습니다.
    - 자원 활용 한도를 초과하기 전에 하드웨어에서 처리 할 수있는로드의 양을 결정하는 데 도움을줍니다.
- Challenges and Areas Not Addressed
    - 주로 응답 속도에 집중하도록 설계되지 않았습니다.
    - 결과는 다른 관련 부하 테스트와 비교할 때만 사용해야합니다.

3. Stress test
- Benefits
    - 시스템에 과부하로 인해 데이터가 손상 될 수 있는지를 판별합니다.
    - 속도 저하뿐만 아니라 오류 및 오류를 유발하기 전에 응용 프로그램이 얼마나 많은 대상 부하를 초과하는지 평가합니다.
    - 임박한 장애를 경고하기 위해 응용 프로그램 모니터링 트리거를 설정할 수 있습니다.
    - 스트레스가 많은 환경에서 보안 취약점이 열리지 않는지 확인합니다.
    - 일반 하드웨어 또는 지원 응용 프로그램 오류의 부작용을 확인합니다.
    - 어떤 종류의 실패가 가장 중요한 계획인지 결정하는 데 도움이됩니다.
- Challenges and Areas Not Addressed
    - 스트레스 테스트는 설계 상 비현실적이기 때문에 일부 이해 관계자는 테스트 결과를 기각 할 수 있습니다.
    - 얼마나 많은 스트레스가 적용 가치가 있는지 아는 것은 종종 어렵습니다.
    - 테스트 환경으로 격리되지 않으면 심각한 혼란을 야기 할 수있는 애플리케이션 및 / 또는 네트워크 장애를 일으킬 수 있습니다.

4. Capacity test
- Benefits
    - 비즈니스 요구 사항을 충족하기 위해 작업 부하를 처리하는 방법에 대한 정보를 제공합니다.
    - 용량 계획자가 모델 및 / 또는 예측을 검증하거나 향상시키는 데 사용할 수있는 실제 데이터를 제공합니다.
    - 용량 계획 모델 및 / 또는 예측을 비교하기위한 다양한 테스트를 수행 할 수 있습니다.
    - 용량 계획을 돕기 위해 기존 시스템의 현재 사용량 및 용량을 결정합니다.
    - 용량 계획을 돕기 위해 기존 시스템의 사용 및 용량 동향을 제공합니다.
- Challenges and Areas Not Addressed
    - 용량 모델 유효성 검사 테스트는 작성하기가 복잡합니다.
    - 이러한 측면이 가장 가치가있는 시점에서 테스트를 통해 용량 계획 모델의 모든 측면을 검증 할 수있는 것은 아닙니다.

잠재적 인 이점이 성능 테스트와 관련된 문제를 훨씬 능가하지만 결과 데이터의 관련성에 대한 불확실성 - 변수, 시나리오 및 상황의 합리적인 조합을 모두 테스트 할 수 없음을 기반으로 - 일부 조직에서는 성능 수행의 가치에 대해 질문합니다 전혀 테스트. 그러나 실제 (특히 엄격한 테스트는 아니지만) 합리적인 테스트를 거쳐 시스템에서 발생하는 치명적인 성능 장애의 가능성은 극적으로 감소합니다. 특히 성능 테스트를 사용하여 프로덕션 환경에서 모니터링 할 대상을 결정하면 팀 응용 프로그램이 중요한 성능 관련 오류로 표류하기 시작하면 조기 경고 신호가 표시됩니다.

### Additional Concepts / Terms
성능 테스트를 수행 할 때 종종 다음 용어를 보거나들을 것입니다. 이러한 용어 중 일부는 조직, 산업 또는 피어 네트워크에서 공통적으로 나타나는 경우도 있지만 그렇지 않은 경우도 있습니다. 이 용어와 개념은 빈번하게 사용되기 때문에 혼란을 야기 할 수 있기 때문에 포함되었습니다.

1. Component test
- 구성 요소 테스트는 응용 프로그램의 아키텍처 구성 요소를 대상으로하는 성능 테스트입니다. 일반적으로 테스트되는 구성 요소에는 서버, 데이터베이스, 네트워크, 방화벽, 클라이언트 및 저장 장치가 포함됩니다.

2. Investigation
- 조사는 제품 품질을 결정하거나 향상시키는 데 가치가있을 수있는 테스트중인 제품의 속도, 확장 성 및 / 또는 안정성 특성과 관련된 정보 수집에 기반을 둔 활동입니다. 조사는 하나 이상의 관측 된 성능 문제의 근본 원인에 관한 가설을 입증하거나 반증하기 위해 자주 사용됩니다.

3.Smoke test
- 스모크 테스트는 응용 프로그램이 정상 부하 상태에서 작업을 수행 할 수 있는지 확인하기위한 성능 테스트의 초기 실행입니다.

4. Unit test
- 성능 테스트의 컨텍스트에서 단위 테스트는 성능 특성에 중점을 둔 상태에서 응용 프로그램의 기존 코드 전체의 논리적 하위 집합 인 코드 모듈을 대상으로하는 테스트입니다. 일반적으로 테스트 된 모듈에는 함수, 프로 시저, 루틴, 객체, 메서드 및 클래스가 포함됩니다. 실적 단위
테스트는 테스트중인 코드 모듈을 작성한 개발자가 자주 작성하고 수행합니다.

5. Validation test
- 유효성 검사 테스트는 테스트중인 제품의 속도, 확장 성 및 / 또는 안정성 특성을 해당 제품에 대해 설정되거나 추정 된 기대치와 비교합니다.

### 요약
성능 테스트는 다양한 형태를 취할 수 있고, 많은 위험을 처리하며, 조직에 다양한 가치를 제공 할 수있는 광범위하고 복잡한 활동입니다.
위험을 줄이고 비용을 최소화하며 주어진 성능 테스트 프로젝트 과정에서 적절한 테스트를 적용해야하는시기를 파악하기 위해서는 다양한 성능 테스트 유형을 이해하는 것이 중요합니다. 성능 테스트를 통해 다양한 테스트 유형을 적용하려면 다음 주요 사항을 평가해야합니다.

- 성능 테스트의 목적.
- 성능 테스트의 컨텍스트. 예를 들어 관련 리소스, 비용 및 테스트 노력에 대한 잠재적 수익 등이 있습니다.




## Chapter3을 읽고 성능테스트시에 어떤 위험사항이 있는지 정리하시오

### Chapter 3 – Risks Addressed Through Performance Testing

### 목적
- 성능 테스트의 관점에서 속도, 확장 성 및 안정성을 확인하는 방법 이해
- 성능 테스트를 사용하여 속도, 확장 성 및 안정성과 관련된 위험을 완화하는 방법에 대해 알아보십시오.
- 성능 테스트에서 적절하게 다루지 못하는 이러한 위험 요소에 대해 알아보십시오.

### 개요
성능 테스트는 중요한 비즈니스 위험을 관리하는 데 필수적입니다. 예를 들어 웹 사이트가 수신 트래픽 양을 처리 할 수없는 경우 고객은 다른 곳에서 쇼핑하게됩니다. 명백한 위험을 식별하는 것 외에도 성능 테스트는 다른 많은 잠재적 인 문제를 탐지하는 유용한 방법이 될 수 있습니다. 성능 테스트는 다른 유형의 테스트를 대체하지는 않지만 사용성, 기능성, 보안 및 기업 이미지와 관련된 정보를 다른 방법으로는 얻을 수없는 것으로 나타낼 수 있습니다.

많은 기업 및 성능 테스터는 성능 테스트에서 속도, 확장 성 및 안정성의 세 가지 범주로 해결할 수있는 위험을 생각하는 것이 중요하다고 생각합니다.

### 성능 테스트 유형별로 해결 된 위험 요약 매트릭스
1. Capacity
- 정상 및 최대로드 조건에서 시스템 용량이 비즈니스 볼륨을 충족합니까?

2. Component
- 이 구성 요소는 기대에 부합합니까?
- 이 구성 요소가 합리적으로 잘 최적화되어 있습니까?
- 관찰 된 성능 문제가이 구성 요소로 인해 발생합니까?

3. Endurance
- 성능은 시간이 지남에 따라 일관됩니까?
- 느리게 성장하는 문제가 아직 발견되지 않았습니까?
- 설명되지 않은 외부 간섭이 있습니까?

4. Investigation
- 시간 경과에 따른 실적 추이는 어느 방법입니까?
- 미래의 테스트를 어떻게 비교해야합니까?

5. Load
- 응용 프로그램이 특정 작업 부하를받을 때 바람직하지 않은 동작이 발생하기 전에 응용 프로그램에서 처리 할 수있는 사용자 수는 몇 명입니까?
- 데이터베이스 / 파일 서버에서 처리 할 수있는 데이터의 양은 어느 정도입니까?
- 네트워크 구성 요소가 적절합니까?

6. Smoke
- 추가 성능 테스트를 위해이 빌드 / 구성을 사용할 준비가 되었습니까?
- 다음에 어떤 유형의 성능 테스트를 수행해야합니까?
- 이 빌드가 마지막 것보다 성능이 좋든 나쁘 던가요?

7. Spike
- 생산 부하가 예상 최대 부하를 초과하면 어떻게됩니까?
- 어떤 종류의 실패를 계획해야합니까?
- 우리는 어떤 지표를 찾아야합니까?

8. Stress
- 생산 부하가 예상 부하를 초과하면 어떻게됩니까?
- 어떤 종류의 실패를 계획해야합니까?
- 실패 이전에 개입하기 위해 우리는 어떤 지표를 찾아야합니까?

9. Unit
- 이 코드 세그먼트가 비교적 효율적입니까?
- 실적 예산 내에서 머물렀습니까?
- 이 코드가로드가 예상대로 수행됩니까?

10. Validation
- 신청서가 목표와 요구 사항을 충족합니까?
- 이 버전이 마지막 버전보다 빠르거나 느린가요?
- 내가 계약을 맺으면 계약 / 서비스 수준 계약 (SLA)을 위반하게됩니까?


### 속도 관련 위험

속도 관련 위험은 대부분의 사람들이 먼저 생각하는 것 일지라도 최종 사용자 만족도에 국한되지 않습니다. 속도는 특정 비즈니스 및 데이터 관련 위험 요인이기도합니다. 성능 테스트에서 해결할 수있는 가장 일반적인 속도 관련 위험 중 일부는 다음과 같습니다.

- 응용 프로그램이 최종 사용자를 만족시킬만큼 충분히 빠릅니까?
- 비즈니스가 데이터가 오래되기 전에 애플리케이션에서 수집 한 데이터를 처리하고 활용할 수 있습니까? 예를 들어, 월말 보고서는 24 시간 이내에 만기가됩니다.
데이터를 처리하는 데 48 시간이 소요됩니다.)
- 애플리케이션이 사용자에게 최신 정보 (예 : 주식 시세)를 제공 할 수 있습니까?
- 오류가 발생하기 전에 최대 예상 응답 시간 내에 웹 서비스가 응답합니까?

### 속도 관련 위험 완화 전략
다음 전략은 속도와 관련된 위험을 완화하는 데 중요합니다.

- 실적 요구 사항과 목표가 다른 사람이 아닌 사용자의 요구와 욕구를 나타내는 지 확인하십시오.
- 속도 측정을 이전 버전 및 경쟁 응용 프로그램과 비교하십시오.
- 정상 및 예상 피크 시간에 실제 워크로드를 복제하는로드 테스트를 설계하십시오.
- 실제 생산 중에 비즈니스 운영에 사용되는 것과 유사한 데이터 유형, 배포 및 볼륨 (예 : 제품 수, 보류 상태의 주문, 사용자 기반 크기)으로 성능 테스트를 수행하십시오. 로드 테스트 실행 전에 데이터베이스 및 파일 서버에 데이터를 누적하거나 데이터 볼륨을 추가로 만들 수 있습니다.
- 성능 테스트 결과를 사용하면 이해 관계자가 정보에 입각 한 아키텍처 및 비즈니스 의사 결정을 내릴 수 있습니다.
- 사용자가 예상되는 최고 부하를 받고있는 동안 시스템에 대한 사용자 만족도에 대한 대표적인 피드백을 요청합니다.
- 성능 테스트에 시간이 중요한 트랜잭션을 포함하십시오.
- 정기적 인 시스템 프로세스가 실행되는 동안 (예 : 바이러스 정의 업데이트 다운로드 또는 매주 백업 중) 적어도 일부 성능 테스트가 수행되는지 확인하십시오.
- 다양한 조건, 부하 수준 및 시나리오 혼합에서 속도를 측정합니다. (사용자는 일관된 속도를 중요시합니다.)
- 성능 테스트 중에 모든 올바른 데이터가 표시되고 저장되었는지 확인하십시오. 예를 들어 사용자가 정보를 업데이트하지만 트랜잭션이 데이터베이스에 쓰기 작업을 완료하지 않았기 때문에 확인 화면에 이전 정보가 계속 표시됩니다.


### 확장성 관련 위험

확장 성 위험은 응용 프로그램이 지원할 수있는 사용자 수뿐만 아니라 응용 프로그램이 포함하고 처리 할 수있는 데이터의 양과 응용 프로그램의 용량이 언제 다가오고 있는지 식별 할 수있는 기능도 포함합니다. 성능 테스트를 통해 해결할 수있는 일반적인 확장 성 위험은 다음과 같습니다.

- 애플리케이션이 전체 사용자 기반에 대해 일관되고 수용 가능한 응답 시간을 제공 할 수 있습니까?
- 응용 프로그램이 응용 프로그램 수명 동안 수집되는 모든 데이터를 저장할 수 있습니까?
- 응용 프로그램이 최고 용량에 다다 랐음을 나타내는 경고 신호가 있습니까?
- 과도한 사용으로도 응용 프로그램의 보안이 유지됩니까?
- 과도한 사용으로 인해 기능이 손상됩니까?
- 애플리케이션이 예상치 못한 최고 부하를 견딜 수 있습니까?

### 확장성 관련 위험 완화 전략

다음 전략은 확장 성 관련 위험을 완화하는 데 중요합니다.

- 다양한 부하에서 측정 된 속도를 비교하십시오. (최종 사용자는 얼마나 많은 사람들이 응용 프로그램을 동시에 사용하고 있는지 알지 못하거나 신경을 쓰지 않습니다.)
- 정상 및 예상 피크 시간에 실제 워크로드를 복제하는로드 테스트를 설계하십시오.
- 실제 생산 중에 비즈니스 운영에 사용되는 것과 유사한 데이터 유형, 배포 및 볼륨 (예 : 제품 수, 보류 상태의 주문, 사용자 기반 크기)으로 성능 테스트를 수행하십시오. 로드 테스트 실행 전에 데이터베이스 및 파일 서버에 데이터를 누적하거나 데이터 볼륨을 추가로 만들 수 있습니다.
- 성능 테스트 결과를 사용하면 이해 관계자가 정보에 입각 한 아키텍처 및 비즈니스 의사 결정을 내릴 수 있습니다.
- 실제 요구 사항에 매핑되는 의미있는 성능 테스트를 수행하십시오.
- 확장 성 한계를 찾으면 부하를 점차적으로 줄이고 재검사하여 응용 프로그램이 대책을 적용 할 수있는 충분한 시간 내에 한계에 도달했다는 신뢰할 수있는 지표가 될 수있는 메트릭을 식별하도록 도와줍니다.
- 특정 사용자 요청에 응답하여 생성 된 데이터베이스 항목을 확인하거나 반환 된 내용의 유효성을 검사하여 다양한로드에서 응용 프로그램의 기능적 정확성을 검증합니다.
- 기대되는 최대로드를 초과하는 성능 테스트를 수행하고 성능 테스트 도중 또는 후에 대표적인 사용자 및 이해 관계자가 수동으로 응용 프로그램에 액세스하도록함으로써 동작을 관찰합니다.

### 안정성 관련 위험

안정성은 신뢰성, 가동 시간 및 복구 가능성과 같은 영역을 포괄하는 포괄적 용어입니다. 고부하, 내구성 및 스트레스 테스트에서는 안정성 위험이 일반적으로 해결되지만 가장 기본적인 성능 테스트에서는 안정성 문제가 종종 감지됩니다. 성능 테스트를 통해 해결 된 몇 가지 일반적인 안정성 위험은 다음과 같습니다.

- 데이터 손상, 지연 또는 서버를 재부팅 할 필요없이 오랜 시간 동안 응용 프로그램을 실행할 수 있습니까?
- 응용 프로그램이 예기치 않게 작동하지 않으면 부분적으로 완료된 트랜잭션은 어떻게됩니까?
- 예약 된 또는 예정되지 않은 중단 시간 이후에 응용 프로그램이 다시 온라인 상태로 전환되면 사용자는 예상 한 모든 것을보고 / 할 수 있습니까?
- 예정되지 않은 중단 시간 이후에 응용 프로그램이 다시 온라인 상태가되면 올바른 시점에 다시 시작됩니까? 특히, 취소 된 트랜잭션을 재개하려고하지 않습니까?
- 오류 또는 반복되는 기능 오류의 조합으로 인해 시스템 충돌이 발생할 수 있습니까?
- 시스템 전체에 부작용을 일으키는 트랜잭션이 있습니까?
- 로드 밸런싱 환경의 한쪽 다리를 내리고 사용자에게 중단없는 서비스를 제공 할 수 있습니까?
- 시스템을 패치하지 않고 업데이트 할 수 있습니까?

### 안정성 관련 위험 완화 전략

다음 전략은 안정성 관련 위험을 완화하는 데 중요합니다.

- 현실적인 지구력 테스트를 위해 시간을 투자하십시오.
- 주요 시나리오로 스트레스 테스트를 수행하십시오. 주요 성능 지표 (네트워크, 디스크, 프로세서, 메모리) 및 손실 된 주문 수, 사용자 로그인 실패 등과 같은 비즈니스 지표로 작업하십시오.
- 실제 생산 환경 (예 : 제품 수, 보류 상태의 주문, 사용자 기반 크기)에서와 유사한 비즈니스 운영을 복제하는 데이터 피드로 스트레스 테스트를 수행합니다. 스트레스 테스트를 실행하기 전에 데이터베이스 및 파일 서버에 데이터를 축적하거나 데이터 볼륨을 추가로 생성 할 수 있습니다. 이렇게하면 데이터베이스 또는 응용 프로그램 교착 상태 및 기타 스트레스 장애 패턴과 같은 치명적인 오류를 복제 할 수 있습니다.
- 테스트 중에 서버를 오프라인으로 가져와 나머지 시스템의 기능, 성능 및 데이터 무결성 동작을 관찰합니다.
- 시스템 재부팅 직전과 직후에 동일한 테스트를 실행합니다. 결과를 비교하십시오. 서비스 또는 프로세스를 재활용하는 데 동일한 접근 방식을 사용할 수 있습니다.
- 성능 테스트 시나리오 (예 : 부적절한 자격 증명을 사용하여 로그온하려는 사용자)에 오류 또는 예외 사례를 포함시킵니다.
- 성능 테스트 중에 시스템에 패치를 적용하십시오.
- 성능 테스트 중에 백업 및 / 또는 바이러스 정의 업데이트를 강제 실행합니다.

### Summary

거의 모든 응용 프로그램 및 비즈니스 관련 위험은 사용자 만족도 및 응용 프로그램의 비즈니스 목표 달성 능력을 포함하여 성능 테스트를 통해 해결할 수 있습니다.
일반적으로 성능 테스트에서 다루는 위험은 속도, 확장 성 및 안정성 측면에서 분류됩니다. 속도는 일반적으로 최종 사용자의 우려 사항이며 확장 성은 비즈니스 관심사이며 안정성은 기술 또는 유지 관리 문제입니다.
프로젝트 관련 위험 및 성능 테스트를 사용할 수있는 관련 완화 전략을 식별하는 것은 거의 보편적으로 가치 있고 시간을 절약하는 방법으로 간주됩니다.

## Part2를 읽고 성능테스트시 어떤 작업들이 필요한지 정리하시오

### PART2 Exemplar Performance Testing Approaches(예시적인 성능 테스트 접근법)

### Chapter 4 – Web Application Performance Testing Core Activities

### 목표
- 대다수의 성능 테스트 프로젝트에 필수적인 7 가지 핵심 활동에 대해 알아보십시오.
- 작업 및 프로세스가 이러한 활동에 어떻게 매핑되는지 식별 할 수 있도록 7 가지 주요 활동을 충분히 자세히 이해합니다.
- 핵심 활동을 중심으로 구축 할 수있는 다양한 성능 테스트 접근법을 이해합니다.

### 개요
- 이 장에서는 응용 프로그램 및 해당 응용 프로그램을 지원하는 시스템을 테스트하는 성능과 관련된 가장 일반적인 핵심 활동을 자세히 소개합니다. 성능 테스트는 "일률적 인"또는 "일면 크기의 가장 적합한"접근 방식으로 효과적으로 형성 될 수없는 복잡한 활동입니다. 프로젝트, 환경, 비즈니스 동인, 수용 기준, 기술, 일정, 법적 의미 및 사용 가능한 기술과 도구는 공통적 인 보편적 접근 방법을 비현실적으로 만듭니다.

- 즉, 거의 모든 프로젝트 수준의 성과 테스트 노력의 일부인 일부 활동이 있습니다. 이러한 활동은 서로 다른시기에 발생할 수도 있고, 다른 일로 부름되거나, 초점의 정도가 다르며, 암묵적으로 또는 명시 적으로 수행 될 수도 있지만, 모두 말하고 완료하면 성능 테스트 프로젝트가 이 가이드 전체에서 확인되고 참조 된 7 가지 핵심 활동에 관한 결정을 내리는 데 가장 적게 걸립니다. 이 7 가지 핵심 활동은 그 자체로 성능 테스트 접근법을 구성하지 않습니다. 오히려 프로젝트에 적합한 접근 방식을 구축 할 수있는 토대를 제공합니다.

## 이 챕터를 사용하는 방법

이 장을 사용하여 성능 테스트의 핵심 활동과 이러한 활동이 수행하는 작업을 이해하십시오. 이 장을 최대한 활용하려면 다음을 수행하십시오.

- "핵심 성과 활동 요약 표"섹션을 사용하여 성능 테스트의 핵심 활동에 대한 개요를 얻고, 귀사와 팀을위한 빠른 참조 안내서를 얻으십시오.
- 다양한 활동 섹션을 사용하여 가장 중요한 성능 테스트 작업의 세부 사항과 각 활동에 대한 고려 사항을 이해하십시오.

### Overview of Activities(활동 개요)
다음 섹션에서는 성공적인 성능 테스트 프로젝트에서 가장 일반적으로 발생하는 7 가지 활동에 대해 설명합니다. 이러한 활동을 효과적으로 수행하는 핵심은 수행 할 때, 호출 한 내용, 중복 여부 또는 반복 패턴이 아니라 이해하고 신중하게 고려하는 것입니다
자신의 프로젝트 컨텍스트에서 가장 중요한 방식으로 개념을 적용 할 수 있습니다.
<br>
프로젝트 컨텍스트에 대한 최소한의 지식으로 시작하여 대부분의 팀은 테스트 환경과 성능 수용 기준을 어느 정도 병렬로 식별하기 시작합니다. 이는 나머지 모든 활동이 활동 1과 2에서 수집 된 정보의 영향을 받기 때문입니다. 일반적으로 사용자와 팀이 응용 프로그램, 사용자, 기능 및 성능 관련 위험이있을 수 있습니다.
<br>
프로젝트 컨텍스트, 테스트 환경 및 성능 허용 기준을 충분히 이해하면 성능 테스트 계획 및 설계를 시작하고 성능 테스트의 종류를 수행하고 종류를 수집하는 데 필요한 도구로 테스트 환경을 구성하게됩니다 다시 말해, 대부분의 경우, 더 많은 정보가 이용 가능할 때마다 이러한 활동을 주기적으로 다시 방문하게됩니다.
<br>
최소한 활동 1 ~ 4의 관련 측면을 달성하면 대부분의 팀은 반복적 인 테스트주기 (활동 5-7)로 이동하여 일부 유형의로드 생성 도구를 사용하여 설계 테스트를 구현하고 구현 된 테스트를 실행하며 이러한 테스트의 결과는 해당 시점에 테스트 할 수있는 구성 요소 및 기능과의 관계로 분석 및보고됩니다.
<br>
To the degree that performance testing begins before the system or application to be tested has been completed, there is a naturally iterative cycle that results from testing features and components as they become available and continually gaining more information about the application, its users, its features, and any performance-related risks that present themselves via testing.

### Summary Table of Core Performance-Testing Activities(핵심 성과 테스트 활동 요약표)
다음 표는 각 활동에 대한 가장 일반적인 입력 및 출력과 함께 7 가지 핵심 성능 테스트 활동을 요약합니다. 프로젝트 컨텍스트는 각 활동의 중요한 입력 항목 임에도 불구하고 나열되지 않습니다.

1. Identify the Test Environment 
- Input 
    - 논리적 및 물리적 생산 아키텍처
    - 논리적 및 물리적 테스트 아키텍처
    - 사용 가능한 도구
- Output
    - 테스트 환경과 프로덕션 환경 비교
    - 환경 관련 문제
    - 추가 공구가 필요한지 여부 결정

2. Identify Performance Acceptance Criteria
- Input 
    - 고객의 기대
    - 완화해야 할 위험
    - 비즈니스 요구 사항
    - 계약 상 의무
- Output
    - 성능 테스트 성공 기준
    - 성과 목표 및 요구 사항
    - 조사 주요 분야
    - 핵심 성과 지표
    - 주요 비즈니스 지표

3. Plan and Design Tests
- Input 
    - 사용 가능한 응용 기능 및 / 또는 구성 요소
    - 응용 프로그램 사용 시나리오
    - 단위 테스트
    - 성능 수용 기준
- Output
    - 개념적 전략
    - 테스트 실행 전제 조건
    - 필요한 도구 및 리소스
    - 시뮬레이션 할 응용 프로그램 사용 모델
    - 테스트 구현에 필요한 테스트 데이터
    - 구현 준비가 된 테스트

4. Configure the Test Environment
- Input 
    - 개념적 전략
    - 사용 가능한 도구
    - 설계된 테스트
- Output 
    - 구성된로드 생성 및 리소스 모니터링 도구
    - 성능 테스트를위한 환경 준비

5. Implement the Test Design
- Input 
    - 개념적 전략
    - 사용 가능한 도구 / 환경
    - 사용 가능한 응용 기능 및 / 또는 구성 요소
    - 설계된 테스트
- Output 
    - 검증되고 실행 가능한 테스트
    - 검증 된 리소스 모니터링
    - 검증 된 데이터 수집

6. Execute the Test
- Input 
    - 작업 실행 계획
    - 유효한 도구 / 환경
    - 사용 가능한 응용 기능 및 / 또는 구성 요소
    - 검증되고 실행 가능한 테스트
- Output 
    - 실행 결과 테스트

7. Analyze Results, Report, and Retest
- Input 
    - 작업 실행 결과
    - 성능 수용 기준
    - 위험, 관심사 및 문제
- Output 
    - 결과 분석
    - 권장 사항
    - 보고서
## Part3를 읽고 테스트 환경에 대해 정리하시오

## Part4를 읽고 성능테스트의 목적에 대해 정리하시오

## Part5를 읽고 테스트의 계획과 디자인에 대해 정리하시오

## Part6을 읽고 테스트 실행에 대해 정리하시오

## Part 7 을 읽고 테스트 결과 분석에 대해 정리하시오

## Part 8 을 읽고 Load 테스트와 Stress 테스트의 차이를 정리하시오


