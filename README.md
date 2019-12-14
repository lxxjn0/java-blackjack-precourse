# Precourse Week 3 - 블랙잭

## 미션 요구사항

> ### 기능 요구사항
>
> 1. 블랙잭 게임을 진행하는 프로그램을 구현한다. 블랙잭 게임은 딜러와 플레이어 중 카드 합이 21 또는 21에 가장 가까운 숫자를 가지는 쪽이 이기는 게임이다.
>
> 2. 플레이어는 게임을 시작할 때 배팅 금액을 정해야 한다. 카드의 숫자 계산은 카드 숫자를 기본으로 하며, 예외로 Ace는 1 또는 11로 계산할 수 있으며, King, Queen, Jack은 각각 10으로 계산한다.
>
> 3. 게임을 시작하면 플레이어는 두 장의 카드를 지급받으며, 두 장의 카드 숫자를 합쳐 21을 초과하지 않으면서 21에 가깝게 만들면 이긴다. 21을 넘지 않을 경우 원한다면 얼마든지 카드를 계속 뽑을 수 있다. 단, 카드를 추가로 뽑아 21을 초과할 경우 베팅 금액을 모두 잃게 된다.
>
> 4. 처음 두 장의 카드 합이 21일 경우 블랙잭이 되면 베팅 금액의 1.5배를 딜러에게 받는다. 딜러와 플레이어가 모두 동시에 블랙잭인 경우 플레이어는 베팅한 금액을 돌려받는다.
>
> 5. 딜러는 처음에 받은 2장의 합계가 16이하이면 반드시 1장의 카드를 추가로 받아야 하고, 17점 이상이면 추가로 받을 수 없다. 딜러가 21을 초과하면 그 시점까지 남아 있던 플레이어들은 가지고 있는 패에 상관없이 승리해 베팅 금액을 받는다.
>
> ### 프로그램 실행 결과
>
> ![프로그램 실행 결과](/images/result_image.jpg "프로그램 실행 결과")
>
> ### 프로그래밍 요구사항
>
> #### 객체1
>
> ```java
> package domain.card;
>
> /**
>  * 카드 한장을 의미하는 객체
>  */
> public class Card {
>     private final Symbol symbol;
>
>     private final Type type;
>
>     public Card(Symbol symbol, Type type) {
>         this.symbol = symbol;
>         this.type = type;
>     }
>
>     // TODO Card 관련 추가 기능 구현
> }
> ```
>
> - 다음 Card 객체를 활용해 구현해야 한다.
>
> - Card 기본 생성자를 추가할 수 없다.
>
> - 필드(인스턴스 변수)인 symbol과 type의 접근 제어자 private을 변경할 수 없다.
>
> - Card에 필드(인스턴스 변수)를 추가할 수 없다.
>
> #### 객체2
>
> ```java
> package domain.user;
>
> import domain.card.Card;
>
> import java.util.ArrayList;
> import java.util.List;
>
> /**
>  * 게임 참여자를 의미하는 객체
>  */
> public class Player {
>     private final String name;
>     private final double bettingMoney;
>     private final List<Card> cards = new ArrayList<>();
>
>     public Player(String name, double bettingMoney) {
>         this.name = name;
>         this.bettingMoney = bettingMoney;
>     }
>
>     public void addCard(Card card) {
>         cards.add(card);
>     }
>
>     // TODO 추가 기능 구현
> }
> ```
>
> - 다음 Player 객체를 활용해 구현해야 한다.
>
> - Player 기본 생성자를 추가할 수 없다.
>
> - 필드(인스턴스 변수)인 name, bettingMoney, cards의 접근 제어자 private을 변경할 수 없다.
>
> - Card에 필드(인스턴스 변수)를 추가할 수 없다.
>
> #### 객체3
>
> ```java
> package domain.user;
>
> import domain.card.Card;
>
> import java.util.ArrayList;
> import java.util.List;
>
> /**
>  * 게임 딜러를 의미하는 객체
>  */
> public class Dealer {
>     private final List<Card> cards = new ArrayList<>();
>
>     public Dealer() {}
>
>
>     public void addCard(Card card) {
>         cards.add(card);
>     }
>
>     // TODO 추가 기능 구현
> }
> ```
>
> - 다음 Dealer 객체를 활용해 구현해야 한다.
>
> - Dealer 기본 생성자 이외 다른 생성자를 추가할 수 없다.
>
> - 필드(인스턴스 변수)인 cards의 접근 제어자 private을 변경할 수 없다.
>
> - Dealer에 필드(인스턴스 변수)를 추가할 수 없다.
>
> #### 추가 선택사항
>
> - 기본으로 제공하는 Card, Player, Dealer 객체에 예외 처리가 되어 있지 않다. 예외 처리를 한다.
>
> - Player와 Dealer를 구현하다보면 중복 코드가 발생할 수 있다. 중복 코드를 제거해 본다.
>
>   - 힌트 : 자바의 상속을 활용해 중복을 제거해 본다.
>
> #### 1, 2주차와 동일
>
> - 자바 코드 컨벤션을 지키면서 프로그래밍 한다.
>
>   - [좀 더 개선된 컨벤션 참고 문서](https://naver.github.io/hackday-conventions-java/)
>
> - 3항 연산자를 쓰지 않는다.
>
> - else 예약어를 쓰지 않는다.
>
>   - 힌트 : if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.
>
>   - else를 쓰지 말라고 하니 switch/case로 구현하는 경우가 있는데 switch/case도 허용하지 않는다.
>
> #### 3주차 변경 및 추가
>
> - 함수(또는 메소드)의 길이가 10라인을 넘어가지 않도록 구현한다.
>
>   - 최대한 10라인을 넘지 않기 위해 노력하고, 정말 힘든 경우 15라인까지 허용한다.
>
>   - 함수(또는 메소드)가 한 가지 일만 잘 하도록 구현한다.
>
> - indent(인덴트, 들여쓰기) depth를 2가 넘지 않도록 구현한다. 1까지만 허용한다.
>
>   - 최대한 1을 유지하기 위해 노력하고, 정말 힘든 경우 2까지 허용한다.
>
>   - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
>
> - 함수(또는 메소드)의 인자 수를 3개까지만 허용한다. 4개 이상은 허용하지 않는다.

<br>

## 구현해야 할 기능 목록

1. (UI) 게임 참여자 이름을 입력받는 기능.

2. (Util) 게임 참여자 이름 입력을 쉼표(,)를 기준으로 분리하는 기능.

3. (Util) 게임 참여자 이름 앞, 뒤로 불필요한 여백을 제거하는 기능.

4. (Business) 게임 참여자 이름이 유효한지 확인하는 기능.

5. (UI) 게임 참여자 개별로 배팅 금액을 입력받는 기능.

6. (Business) 배팅 금액이 유효한지 확인하는 기능.

7. (Business) 게임 참여자 이름과 배팅 금액으로 Player를 생성하는 기능.

8. (Business) 모든 Player가 생성 완료된 후, Dealer를 생성하는 기능.

9. (Business) 카드를 생성하는 기능.

10. (Business) Dealer와 모든 Player에게 카드를 2장씩 나눠주는 기능.

11. (UI) Dealer는 처음 받은 1장, 나머지 Player들은 2장씩 출력하는 기능.

12. (UI) 각 Player별로 카드를 더 받을지 여부를 입력받는 기능.

13. (Business) 카드를 더 받는지 여부에 대한 입력이 유효한지 확인하는 기능.

14. (Business) 모든 Player가 더 이상 카드를 받지 않는 경우, 규칙에 따라 Dealer에게 카드를 주는 기능.

15. (UI) Dealer가 카드를 더 받아야 하는 상황인지를 출력하는 기능.

16. (UI) Dealer가 카드를 모두 받은 다음 Dealer와 모든 Player의 결과를 출력하는 기능.

17. (Business) 게임 결과에 따라 Dealer와 각 Player의 수익을 계산하는 기능.

18. (UI) 최종 게임 결과(수익)을 출력하는 기능.

<br>

## 개발 진행 계획

1. [프로젝트(미션) 요구사항](##-미션-요구사항)들과 [구현해야 할 기능 목록](##-구현해야-할-기능-목록)을 대략적으로 작성.

   - 과제의 진행에 필요한 내용들을 [README.md](/README.md)에서 모두 볼 수 있도록 작성.

   - 최대한 객체지향적으로 간략히 설계해보고 기능들을 작성할 수 있도록 진행.

     - [생각해라, 객체지향처럼](http://woowabros.github.io/study/2016/07/07/think_object_oriented.html) 글을 참고하여 진행.

2. [구현해야 할 기능 목록](##-구현해야-할-기능-목록)에 대한 세부적인 기능 분류 및 예외 처리 작성.