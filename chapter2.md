# **Chapter 2. 이더리움 기초**
> 본 글은 『Mastering Ethereum』을 읽고 정리한 내용입니다.

## **1. 이더 화폐 단위**

이더리움의 화폐 단위는 `이더(ether)`라고 불리며, `ETH` 또는 기호 `Ξ`(대문자 E처럼 보이는 그리스 문자 'Xi'에서 유래) 또는 자주 쓰이진 않지만 
`♦`를 사용한다.

이더는 더 작은 단위로 세분화되어 `웨이(wei)`라는 가능한 가장 작은 단위까지 내려간다. 1개의 이더는 100경(quintillion) 웨이 (1 * 10^18)다. 사람들이 '이더리움' 화폐라고 언급하는 경우도 있는데, 이더리움은 시스템이고 이더가 화폐이다.

이더의 가치는 항상 이더리움 내부에서 웨이로 표시된 부호 없는 정숫값으로 표현된다. 1이더를 거래할 때, 그 트랜잭션은 1000000000000000000웨이 값으로 인코딩해서 표기한다.

이더의 다양한 단위에는 `SI(International System of Units)`를 이용한 `학명(scientific name)`뿐만 아니라 컴퓨터와 암호학 분야의 위대한 인물들에게 경의를 표하는 구어체 이름도 함께 사용한다.

|값(웨이)|멱지수|일반 이름|SI 이름|
|:--|:--|:--|:--|
|1|1|웨이|웨이|
|1,000|10^3|배비지|킬로웨이 또는 펨토이더|
|1,000,000|10^6|러브레이스|메가웨이 또는 피코이더|
|1,000,000,000|10^9|사넌|기가웨이 또는 나노이더|
|1,000,000,000,000|10^12|사보|마이크로이더 또는 마이크로|
|1,000,000,000,000,000|10^15|피니|밀리이더 또는 밀리|
|1,000,000,000,000,000,000|10^18|이더|이더|
|1,000,000,000,000,000,000,000|10^21|그랜드|킬로이더|
|1,000,000,000,000,000,000,000,000|10^24||메가이더|

## **2. 이더리움 지갑 선택하기**

이더리움 지갑은 이더리움 시스템의 관문(gateway)이다. 지갑은 사용자의 키를 보유하고, 사용자를 대신하여 트랜잭션을 생성하고 브로드캐스트(broadcast)할 수 있다. 이더리움 지갑은 그 기능과 디자인이 다양하기 때문에 선택하기 어려울 수 있다. 이더리움 플랫폼 자체는 여전히 개선되고 있으며, '최상의' 지갑은 종종 플랫폼 업그레이드와 함께 발생하는 변화에 잘 적응하는 지갑이다.

한 지갑에서 다른 지갑으로 변경하는 방법은 (지갑이 마음에 들지 않아서 등) 아주 쉽다. 이전 지갑에서 새 지갑으로 자금을 보내거나 개인키를 내보내고 새 키로 가져오는 트랜잭션만 수행하면 된다.

지갑 애플리케이션이 작동하려면 개인키에 대한 접근 권한이 있어야 하므로 신뢰하는 소스에서 지갑 애플리케이션을 다운로드해서 사용하는 것이 중요하다. 일반적으로 지갑 애플리케이션의 인기가 높을수록 더 신뢰할 수 있다. 그럼에도 한 지갑에 몰아넣기보단 이더리움 계정을 2개의 지갑에 분산시켜 놓는 방법이 안전할 것이다.

**메타마스크(MetaMask)**
* 브라우저 확장 지갑, 웹 기반 지갑 (크롬, 파이어폭스, 오레파, 브레이브 브라우저)
* 다양한 이더리움 노드와 테스트 블록체인에 연결할 수 있어서 사용하기 쉽고 테스트하기 편리

**잭스(Jaxx)**
* 안드로이드, iOS, 윈도우, 맥OS, 리눅스를 비롯한 다양한 운영체제에서 실행되는 다중 플랫폼 및 다중 화폐 지갑
* 단순하고 사용하기 쉽도록 설계
* 어디에 설치하느냐에 따라 모바일 또는 데스크톱 지갑이 됨

**마이이더월렛(MyEtherWallet, MEW)**
* 모든 브라우저에서 실행되는 웹 기반 지갑
* 정교한 기능

**에메랄드 지갑(Emerald Wallet)**
* 이더리움 클래식 블록체인과 함께 작동하도록 설계되었지만, 그 밖의 이더리움 기반 블록체인과도 잘 작동함
* 오플 소스 데스크톱 애플리케이션
* 윈도우, 맥OS, 리눅스에서 작동
* 풀 노드를 실행하거나 '가벼운' 모드에서 작동하는 공개 원격 노드에 연결할 수 있음
* 커맨드 라인에서 모든 작업을 수행할 수 있는 보조 도구가 있음

## **3. 통제와 책임**

이더리움 같은 개방형 블록체인은 탈중앙화된 시스템으로 작동하기 때문에 중요하다. 이것이 뜻하는 바는 많지만, 한 가지 중요한 측면은 이더리움의 각 사용자가 자금 및 스마트 컨트랙트에 대한 접근을 제어하는 자체 개인키를 관리하고 제어할 수 있어야 한다는 것이다. 때로는 자금 및 스마트 컨트랙트에 대한 접근 조합을 '계정' 또는 '지갑'이라고도 한다. 기본 원칙은 하나의 개인키가 하나의 '계정'과 동일한 것이라고 생각하면 쉽다. 일부 사용자는 온라인 거래소 같은 제3자 관리인을 이용하고 직접 개인키를 관리하지 않으려 한다. 이 책에서는 개인키를 제어하고 관리하는 방법을 알려줄 것이다.

통제에는 큰 책임이 따른다. 개인키를 분실하면 자금 및 컨트랙트에 대한 접근 권한을 잃게 된다. 어느 누구도 접근 권한을 회복하도록 도와줄 수 없으며, 자금은 영원히 잠겨 있을 것이다.


## **4. 메타마스크 설치 및 사용법 실습**

__*실습 내용 생략*__

## **5. 월드 컴퓨터 소개**

많은 사람들은 이더리움을 단지 암호화폐로 취급한다. 그러나 이더리움은 이보다 훨씬 더 많은 기능을 갖고 있다. 사실, 암호화폐 기능은 탈중앙화된 월드 컴퓨터로서 이더리움의 기능에 부차적인 것이다. 이더는 이더리움 가상 머신(Ethereum Virtual Machine, EVM)이라고 하는 에뮬레이트된 컴퓨터에서 실행되는 컴퓨터 프로그램인 스마트 컨트랙트를 실행하는 데 사용되기 위한 것이다.

EVM은 글로벌 싱글톤으로, 마치 전 세계에 걸친 단일 인스턴스 컴퓨터인 것처럼 작동하며 세상 어디서든 실행된다. 이더리움 네트워크의 각 노드는 컨트랙트 실행을 확인하기 위해 EVM의 로컬 사본을 실행하고, 이더리움 블록체인은 트랜잭션과 스마트 컨트랙트를 처리할 때 월드 컴퓨터의 변화하는 상태(state)를 기록한다.

## **6. 외부 소유 계정(EOA) 및 컨트랙트**

메타마스크 지갑에서 생성한 계정의 유형을 `외부 소유 계정(Externally Owned Account, EOA)`이라고 한다. 외부 소유 계정은 개인키가 있는 계정이다. 개인키를 갖는다는 건, 지금 또는 컨트랙트에 대한 접근을 제어한다는 뜻이다. 또 다른 유형의 계정은 `컨트랙트 계정(contract account)`이다. 컨트랙트 계정에는 단순한 EOA가 가질 수 없는 스마트 컨트랙트 코드가 있다. 또한 컨트랙트 계정에는 개인키가 없다. 컨트랙트 계정은 스마트 컨트랙트 코드의 로직으로 제어한다. 여기서 스마트 컨트랙트 코드는 컨트랙트 계정 생성 시 이더리움 블록체인에 기록되고 EVM에 의해 실행되는 소프트웨어 프로그램이다.

컨트랙트에는 EOA와 마찬가지로 주소가 있으며, 이더를 보내고 받을 수 있다. 그러나 트랙잭션 목적지가 컨트랙트 주소일 때 트랜잭션과 트랜잭션 데이터를 입력으로 사용하여 컨트랙트가 EVM에서 `실행된다(run).` 이더 외에도 트랜잭션에는 실행할 컨트랙트의 특정 함수와 해당 함수에 전달할 파라미터를 나타내는 `데이터(data)`가 포함될 수 있다. 이렇게 해서 트랜잭션은 컨트랙트 내의 함수를 `호출(call)`할 수 있다.

컨트랙트 계정에는 개인키가 없으므로 트랜잭션을 시작할 수 없다. EOA만 트랜잭션을 `시작(initiate)`할 수 있지만, 컨트랙트는 복잡한 실행 경로를 구축하여 다른 컨트랙트를 호출해서 컨트랙트에 `반응(react)`할 수 있다. 이것을 사용하는 전형적인 방법은 다중 서명 스마트 트랜잭션 지갑에 지급요청 트랜잭션을 전송하여 일부 ETH를 다른 주소로 보내는 것이다. 일반적인 댑(DApp) 프로그래밍 패턴은 컨트랙트 A가 컨트랙트 B를 호출하게 하는 것인데, 이렇게 하면 컨트랙트 A의 사용자들 간에 공유된 상태를 유지할 수 있게 된다.

## **7. 간단한 컨트랙트: 테스트 이더 Faucet**

이더리움에는 많은 고급 언어가 있으며, 모두 컨트랙트를 작성하고 EVM 바이트코드를 생성하는 데 사용할 수 있다. 이 중 하나의 고급 언어가 스마트 컨트랙트 프로그래밍에서 가장 많이 사용되고 있는데, 솔리디티가 바로 그것이다. 솔리디티는 개빈 우드 박사가 창안했으며, 이더리움(그리고 그 너머)에서 가장 널리 사용되는 언어가 되었다.

다음 예제에서는 `Faucet`을 제어하는 컨트랙트를 작성할 것이다. 이미 롭스텐 테스트 네트워크에서 테스트 이더를 얻기 위해 Faucet을 사용했다. Faucet은 비교적 간단한데, 요청하는 모든 주소에 이더를 제공하고 주기적으로 다시 채워진다. 여러분은 Faucet을 사람이나 웹 서버가 관리하는 지갑으로 구현할 수 있다.

**Faucet.sol: Faucet을 구현하는 솔리디티 컨트랙트**

```sol
// 우리의 첫 번째 컨트랙트는 Faucet이다.
contract Faucet {
    // 요청하는 사람에게 이더 주기
    function withdraw(uint withdraw_amount) public {
        // 출금 액수 제한
        require(withdraw_amount <= 100000000000000000);
        // 요청한 주소로 금액 보내기
        msg.sender.transfer(withdraw_amount);
    }
    // 입금 금액 수락
    function () public payable {}
}
```

위 코드는 우리가 만들 수 있는 매우 간단 컨트랙트이면서 여러 가지 나쁜 습관과 보안 취약성을 보여주는, `결함을 가진(flawed)` 컨트랙트다. 이 컨트랙트가 하는 일과 작동 방식을 한 줄씩 살펴보자.

다음 줄은 실제 컨트랙트가 시작하는 곳이다.
```sol
contract Faucet {
```
이 줄은 다른 객체 지향 언어의 class 선언과 비슷하게 contract 객체를 선언한다. 컨트랙트는 `범위(scope)`를 정의하는 중괄호(`{}`) 사이의 모든 줄을 포함해서 정의하는데, 다른 많은 프로그래밍 언어에서 중괄호가 사용되는 방식과 같다.

다음으로 Faucet 컨트랙트의 첫 번째 함수를 선언한다.

```sol
function withdraw(uint withdraw_amount) public {
```

이 함수의 이름은 withdraw이며, withdraw_amount라는 부호 없는 정수(uint) 인수 하나를 갖는다. 이 함수는 다른 함수에 의해 호출될 수 있는 공개(public) 함수로 선언된다. 함수 정의는 중괄호 사이에 온다. withdraw 함수의 첫 번째 부분은 출금에 대한 제한을 설정한다.

```sol
require(withdraw_amount <= 100000000000000000);
```

전제 조건을 테스트하기 위해 내장된 솔리디티 함수 require를 사용한다. 즉, withdraw_amount는 100,000,000,000,000,000웨이보다 작거나 같으며, 0.1이더에 해당한다. 해당 금액보다 큰 withdraw_amount로 withdraw 함수가 호출되면 여기의 require 함수는 컨트랙트 실행을 중지하고 `예외(exception)`로 실패 처리한다. 솔리디티에서 명령문은 세미콜론으로 끝나야 한다.

컨트랙트의 이 부분은 Faucet의 주요 로직이다. 출금에 한도를 두어 컨트랙트에서 자금 흐름을 제어한다. 매우 간단한 제어이지만 프로그래밍 가능한 블록체인의 힘을 볼 수 있다. 탈중앙화된 소프트웨어로 돈을 제어한다.

다음을 실제 출금이다.

```sol
msg.sender.transfer(withdraw_amount);
```

여기서 몇 가지 재미있는 일이 일어나고 있다. msg 객체는 모든 컨트랙트에서 접근할 수 있는 입력 중 하나로, 이 컨트랙트의 실행을 시작한 트랜잭션을 나타낸다. sender 속성을 해당 트랜잭션의 발신자 주소다. transfer 함수는 이더를 현재 컨트랙트에서 발신자의 주소로 전송하는 내장 함수다. 다시 말하자면, 이 컨트랙트 실행을 트리거한 msg의 sender(발신자)에게 transfer(전달)한다는 뜻이다. transfer 함수는 유일한 인수로서 양(amount)을 받는다. 몇 줄 앞에 선언된 withdraw 함수의 파라미터의 withdraw_amount 값을 전달한다.

다음으로 함수를 하나 더 선언한다.

```sol
function () public payable {}
```

이 함수는 소위 `폴백(fallback)` 또는 `기본(default)` 함수로, 컨트랙트를 실행한 트랜잭션이 컨트랙트에 선언된 함수 또는 어떠한 함수도 지정하지 않았거나 데이터를 포함하지 않은 경우에 호출된다. 컨트랙트에는 하나의 기본 함수(이름 없음)를 가질 수 있으며, 일반적으로 이더를 받는 함수다. 이런 이유로 기본 함수는 public(공개형)이고 payable 함수로 정의되며, 이는 이더를 컨트랙트에 받아들일 수 있음을 의미한다. 중괄호({}) 안의 비어 있는 정의가 나타내듯이, 이더를 받는 일 외에는 아무것도 하지 않는다. 이더를 지갑 같은 컨트랙트 주소로 보내는 트랜잭션을 발생시키면 이 함수가 처리한다.

## **8. Faucet 컨트랙트 컴파일**

첫 번째 예제 컨트랙트를 만들었으니 솔리디티 컴파일러를 사용하여 솔리디티 코드를 EVM 바이트코드로 변환해야 한다. EVM은 바이트코드를 블록체인 자체에서 실행할 수 있다.

솔리디티 컴파일러는 독립 실행 파일, 다양한 프레임워크의 일부 그리고 통합 개발 환경(Integrated Development Environment, IDE)에 번들로 제공된다. 여기서는 유명한 IDE 중 하나인 `리믹스(Remix)`를 사용할 것이다.

## **9. 블록체인에 컨트랙트 생성하기**

컨트랙트를 바이트코드로 컴파일 했다면 이제 이더리움 블록체인에 컨트랙트를 등록해야 한다. 여기서는 롭스텐 테스트넷을 사용하여 컨트랙트를 테스트할 것이고, 이 테스트넷 블록체인에 올리게 될 것이다.

블록체인에 컨트랙트를 등록하는 것은 목적지 주소가 0x0000000000000000000000000000000000000000(제로 어드레스(zero address)라고도 함)인 특수 트랜잭션을 만드는 것이다. 제로 어드레스는 컨트랙트를 등록하고자 하는 이더리움 블록체인에 알리는 특별한 주소다. 다행히도 리믹스 IDE가 이 모든 것을 처리하고 메타마스크에 트랜잭션을 보낸다.

__*실습 내용 생략*__

## **10. 컨트랙트 사용하기**

지금까지 배운 내용을 요약해 보자. 이더리움 컨트랙트는 EVM이라고 하는 가상 시스템에서 실행되는 돈을 제어하는 프로그램이다. 컨트랙트는 블록체인에 바이트코드를 등록하는 특별한 트랜잭션에 의해 생성된다. 컨트랙트가 블록체인에서 생성되면 지갑과 마찬가지로 이더리움 주소를 갖게된다. 누군가가 컨트랙트 주소로 트랜잭션을 보낼 때마다 그 트랜잭션을 입력값으로 하여 컨트랙트가 EVM에서 실행된다. 컨트랙트 주소로 보내지는 트랜잭션에는 이더, 데이터 또는 둘 다를 포함할 수 있다. 트랜잭션이 이더를 포함하면, 이는 컨트랙트 잔액에 '예치된다'. 데이터가 포함되어 있으면 데이터에서는 컨트랙트에서 명명된 함수를 지정하고 호출하여 함수에 인수를 전달할 수 있다.

__*실습 내용 생략*__

## **11. 결론**

이 장에서는 메타마스크를 사용하여 지갑을 설정했으며, 롭스텐 테스트 네트워크의 Faucet을 사용하여 자금을 조달했다. 이더를 지갑의 이더리움 주소로 가져온 다음, Faucet 이더리움 주소로 보냈다.

다음으로 솔리디티 Faucet 컨트랙트를 작성했다. 리믹스 IDE를 사용하여 컨트랙트를 EVM 바이트코드로 컴파일했다. 트랜잭션을 형성하기 위해 리믹스를 사용했고, 롭스텐 블록체인에서 Faucet 컨트랙트를 만들었다. 마지막으로, withdraw 함수를 호출하는 트랜잭션으로 0.1이더를 보냈다.

별로 대단해 보이지 않을 수도 있지만, 우리는 탈중앙화된 월드 컴퓨터에서 돈을 통제하는 소프트웨어와 성공적으로 상호작용했다.
