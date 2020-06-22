# Scheduler based on the DQN that considers the following tasks to minimize tardiness

본 프로젝트는 VMS Solutions와 협업 프로젝트로 데이터 및 코드는 대외비 입니다. 

데이터, 코드를 제외한 프로젝트 과제 내용만 공유합니다.

### 1. 과제 개발의 목적 및 필요성

#### 1.1 목적 및 필요성

- 현업에서 제품의 생산방식이 고도화 되고 복잡해졌다.
- 일정계획을 효율적으로 세우기가 어려워짐
- 일정계획을 수립하는데 많은 시간이 필요함
- 기존에 존재하는 룰을 이용한 일정계획은 최적의 모델과 거리가 멀다.
- 문제가 단순한 경우에는 기존의 룰도 좋은 해를 구할 수 있지만, 문제가 점차 복잡해짐으로써 좋은 해를 구하기 쉽지 않음
- 산업경영공학에서 배운 일정계획에 대한 지식과 연계전공(인공지능 소프트웨어)에서 배운 딥러닝 지식을 이용하여 일정계획을 수립함으로써 최적의 모델에 근접 할 수 있도록 하며 일정계획에 많은 시간과 비용을 소모하지 않도록 하고자 한다.
- 기존의 존재하는 룰보다 좋은 성능을 가지게 된다면 공정의 자동화에 도움이 될 수 있음을 기대한다.

#### 1.2 활용성 및 기대 효과

- 일정 계획을 수립하는데 소요되는 시간과 비용 절약
- 좋은 일정계획을 통하여 적은 시간 안에 작업을 완료할 수 있으며 비용이 감소
- 유휴시간이 적어짐으로써 더 많은 생산을 할 수 있음
- 시각화 툴을 이용하여 스케줄 테이블을 알기 쉽게 확인
- 공정의 자동화에 도움이 될 수 있음을 기대한다.

---

### 2. 과제 내용

#### 2.1 과제 내용

- 스케줄링은 단순한 문제일 경우 어려움이 없으나, 복잡한 문제의 경우 많은 시간과 비용이 소모됨.
- 강화학습(DDQN)을 이용하여 일정계획을 수립함으로써 시간과 비용 절감
- 장비 제약이 있으며, 주문 분리가 불가능하고, 병렬기계인 경우의 문제를 해결하려고 한다.
- 작업의 타입이 바뀌는 경우 setup time이 발생하며 2시간으로 설정하였다.
- 총 납기 지연 시간을 최소화하는 일정 계획을 수립한다.
- 총 머신의 개수는 18개이며 작업의 타입은 13개, 오더의 개수는 100개를 1세트로 설정하였다.
- 기본 룰(FCFS, LPT, SPT, MOR, LOR, Slack)과의 성능을 비교/분석한다.
- 딥러닝 플랫폼은 keras를 사용하며, 사용 기술로는 강화학습중 DDQN(Double DQN)기법을 사용한다.

#### 2.2 Order 설명

<img src='/img/scheduler1.png' width='500'>

#### 2.3 가정 사항

<img src='/img/scheduler2.png' width='500'>

<img src='/img/scheduler3.png' width='500'>

---

### 3. 실험 내용

#### 3.1 Framework

<img src='/img/scheduler4.png' width='600'>

#### 3.2 Input & Output

<img src='/img/scheduler5.png' width='600'>

#### 3.3 State

<img src='/img/scheduler6.png' width='600'>

#### 3.4 Network 구성

<img src='/img/scheduler7.png' width='600'>

---

### 4. 결과

#### 4.1 학습 결과

<img src='/img/scheduler8.png' width='600'>

Iteration이 증가 할 수록 납기를 어기는 지연시간 감소, setup 감소, 전체적인 스케줄 밀집도 증가  

#### 4.2 DQN, DDQN 비교 (lot 1개 고려, 10개 고려)

<img src='/img/scheduler9.png' width='600'>

#### 4.3 전체 결과

<img src='/img/scheduler10.png' width='600'>

- Setup time과 장비 별 작업 타입 제약(constraint)이 존재하는 강화학습 기법 (DQN, DDQN) 모델 생성
- 기본 룰(SLACK-EDD, SPT, LPT, FIFO)보다 좋은 성능을 보임
- Lot 1개를 고려하는 것 보다 그 다음 Lot들을 고려하는 것이 더 좋은 성능을 보임
- DQN과 DDQN을 비교하였을 때, 비슷한 성능을 보이나 DDQN이 조금 더 좋은 성능을 보임
- 실시간 스케줄링 알고리즘 적용 기대


#### 4.4 Schedule visualization

<img src='/img/scheduler11.png' width='600'>

#### 4.5 Schedule visualization(Density 0.9 order list  1st list)

<img src='/img/scheduler12.png' width='600'>

#### 4.6 video

[![Video Label](https://i.ytimg.com/vi/EA6qoCavDKk/hqdefault.jpg?sqp=-oaymwEZCPYBEIoBSFXyq4qpAwsIARUAAIhCGAFwAQ==&rs=AOn4CLDnZ-pGF_RLROjKioHa6mWqKiWgxA)](https://youtu.be/EA6qoCavDKk)
