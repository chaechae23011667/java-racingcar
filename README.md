# java-racingcar

자동차 경주 미션 저장소

## 설정 사항

- (중요) JDK 17 버전으로 진행한다.

## **기능 요구사항**

- 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다.
- 각 자동차에 이름을 부여할 수 있다. 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다.
- 자동차 이름은 쉼표(,)를 기준으로 구분하며 이름은 5자 이하만 가능하다.
- 사용자는 몇 번의 이동을 할 것인지를 입력할 수 있어야 한다.
- 전진하는 조건은 0에서 9 사이에서 random 값을 구한 후 random 값이 4 이상일 경우 전진하고, 3 이하의 값이면 멈춘다.
- 자동차 경주 게임을 완료한 후 누가 우승했는지를 알려준다. 우승자는 한 명 이상일 수 있다.

## **실행 결과**

- 위 요구사항에 따라 3대의 자동차가 5번 움직였을 경우 프로그램을 실행한 결과는 다음과 같다.

```
경주할 자동차 이름을 입력하세요(이름은 쉼표(,)를 기준으로 구분).
kokodak,kuku,cucu
시도할 회수는 몇회인가요?
5

실행 결과
kokodak : -
kuku : -
cucu : -

kokodak : --
kuku : -
cucu : --

kokodak : ---
kuku : --
cucu : ---

kokodak : ----
kuku : ---
cucu : ----

kokodak : -----
kuku : ----
cucu : -----

kokodak : -----
kuku : ----
cucu : -----

kokodak, cucu가 최종 우승했습니다.
```

## **프로그래밍 요구사항**

- **모든 로직에 단위 테스트를 구현한다. 단, UI(System.out, System.in) 로직은 제외**
- **자바 코드 컨벤션을 지키면서 프로그래밍한다.**
    - 참고문서: https://google.github.io/styleguide/javaguide.html 또는 https://myeonguni.tistory.com/1596
- **`규칙 1: 한 메서드에 오직 한 단계의 들여쓰기(indent)만 한다.`**를 지키며 구현한다.
    - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
    - 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메소드)를 분리하면 된다.
- **`규칙 2: else 예약어를 쓰지 않는다.`**를 지키며 구현한다.
    - 힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.
    - else를 쓰지 말라고 하니 switch/case로 구현하는 경우가 있는데 switch/case도 허용하지 않는다.
- **함수(또는 메소드)의 길이가 15라인을 넘어가지 않도록 구현한다.**
    - 함수(또는 메소드)가 한 가지 일만 잘 하도록 구현한다.

**MVC 패턴으로 리팩터링 후의 main 메소드 예시**

```java
import view.InputView;
import view.ResultView;
import domain.RacingGame;

public class RacingMain {
    public static void main(final String... args) {
        final var carNames = InputView.getCarNames();
        final var tryCount = InputView.getTryCount();

        final var racingGame = new RacingGame(carNames, tryCount);
        racingGame.race();
        
        ResultView.printWinners(racingGame.getWinners());
    }
}
```
