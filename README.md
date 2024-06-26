# 미니과제2 - 자동차 경주
## 목차
[1. 코드 소개](#코드-소개)<br>
[2. 자동차 경주 룰](#자동차-경주-룰)<br>
[3. 구현 기능](#구현-기능)<br>
[4. 코드 제한조건](#코드-제한-기능)<br>
[5. 기능 목록](#기능-목록)<br>
## 코드 소개
- 자동차 경주를 java 코드로 구현한 것이다.
## 자동차 경주 룰
- 사용자의 입력
  - 최초 사용자는 경주할 자동차의 이름을 쉼표(,)로 구분하여 입력한다
  - 전진을 시도할 횟수를 입력한다
- 전진하는 조건은 0에서 9사이 무작위 값을 구한 후 무작위 값이 4이상일 경우이다
- 자동차 경주 게임을 완료한 후 누가 우승했는지 알려준다(공동 우승 가능)
## 구현 기능
- 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다
- 각 자동차에 이름을 부여할 수 있다.
- 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다
- 자동차 이름은 쉼표(,)를 기준으로 구분하고 5자이하로 띄어쓰기는 없다
- 사용자는 몇 번의 이동을 할 것인지 입력할 수 있어야 한다
- 우승자가 여러 명일 경우 쉼표(,)를 이용하여 구분한다
- 사용자가 잘못된 값을 입력할 경우 'IllegalArgumentException'을 발생시키고, "[ERROR]"로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다
  - Exception이 아닌 IllegalArgumentException, IllegalStateException등과 같은 명확한 유형을 처리한다
## 코드 제한 기능
- JDK 17 버전에서 실행이 가능해야 함
- 프로그램 실행의 시작점은 Application의 main()
- 프로그램 종료시 System.exit() 호출 X
- 프로그래밍 요구 사항에서 달리 명시하지 않은 한 파일, 패키지 등의 이름을 바꾸거나 이동하지 않음
- 자바 코드 컨벤션을 따른다.
  - Google Java Style Guide 원칙
  - 단, 들여쓰기는 4 space
- indent(인덴트, 들여쓰기) depth는 3이 넘지 않도록(2까지 허용)
- 3항 연산자 금지
- 함수는 오직 한 가지 일만 해야 한다.
- 함수의 길이는 15라인 이하
- JUnit 5와 AssertJ를 이용하여 정리한 기능 목록이 정상적으로 작동하는지 테스트 코드로 확인
- else 예약어 금지 (switch/case도 X)
- 도메인 로직 단위 테스트 구현. 단, UI(System.out, System.in, Scanner)로직은 제외
  - 핵심 로직을 구현하는 코드와 UI를 담당하는 로직을 분리해 구현
## 기능 목록
### Car.java
- Car 객체를 설계해 놓은 클래스
  - **String name**: 자동차의 이름
  - **String position**: 자동차의 위치(경주 중 위치)
  - **getName()**: 자동차 이름 반환
  - **getPosition()**: 현재 자동차 위치 반환(전진 횟수만큼 "-"되어 있음)
  - **forward()**: 자동차가 전진에 성공함
### Application.java
- 자동차 경주를 시작하는 Main 클래스
### RacingGame.java
- 자동차 경주에 대한 Model 클래스
  - playRacingGame(): 경주를 진행하는 메서드
  - randNum(): 경주에서 전진의 기준이 되는 난수를 생성하는 메서드
  - lineUp(): 경주 결과에 따라 배열을 정렬하는 메서드
  - winner(): 우승 차량을 선정하는 메서드
  - racing(): 경주중인 자동차의 전진 시도를 진행하는 메서드
  - isForward(): 경주에서 전진을 시도하는 메서드
### RacingMonitor.java
- 자동차 경주에 대한 View 클래스
  - enterRacingCars(): 자동차 경주에 참여할 자동차를 입력하는 메서드
  - enterTryNum(): 자동차 경주에서 전진을 시도해 볼 수 있는 횟수를 입력받는 메서드
  - startRace(): 경주가 시작되면 진행 상황을 출력하는 메서드
  - printPosition(): 전진 시도 차시별로 진행 상황을 출력하는 메서드
  - printRacingResult(): 최종 우승한 자동차를 출력하는 메서드
### RacingController.java
- 자동차 경주에 대한 Controller 클래스
  - createList(): 자동차 경주에 참가하는 자동차 리스트를 생성하는 메서드
  - carVerify(): 사용자가 경주에 참가하는 자동차의 이름을 올바르게 입력했는지 확인하는 메서드
  - tryNumVerify(): 사용자가 경주에서 전진 시도의 횟수를 올바르게 입력하였는지 확인하는 메서드