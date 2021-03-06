# **Chapter 7. 스마트 컨트랙트와 솔리디티**
> 본 글은 『Mastering Ethereum』을 읽고 정리한 내용입니다.

이더리움에는 외부 소유 계정(EOA)과 컨트랙트 계정이라는 두 가지 유형의 계정이 있다. EOA는 이더리움 플랫폼의 외부에 있는 지갑 애플리케이션 같은 소프트웨어를 통해 사용자가 제어한다. 반대로, 컨트랙트 계정은 이더리움 가상 머신에 의해 실행되는 프로그램 코드(일반적으로 '스마트 컨트랙트'라고 함)가 제어한다. 즉, EOA는 관련 코드나 데이터 저장소가 없는 간단한 계정이지만, 컨트랙트 계정은 관련 코드와 데이터 저장소를 모두 갖고 있다. 컨트랙트 계정은 개인키를 갖지 않으므로 스마트 컨트랙트에 규정된 미리 결정된 방식으로 '스스로 제어' 하는 반면, EOA는 프로토콜 외부에 있어서 프로토콜에 독립적인 '실제 세계'의 개인키로 생성되고 암호로 서명된 거래에 의해 제어된다. 두 가지 유형의 계정은 모두 이더리움 주소로 식별된다. 이 장에서는 컨트랙트 계정과 이를 제어하는 프로그램 코드에 대해 설명한다.

## **1. 스마트 컨트랙트란 무엇인가?**

`스마트 컨트랙트(smart contract)`라는 용어는 다양한 것들을 설명하기 위해 수년 동안 사용되어 왔다. 1990년대 암호학자 닉 사보(Nick Szabo)는 이 용어를 "당사자들이 다른 약속에 따라 수행하는 프로토콜을 포함하여 디지털 형식으로 지정된 일련의 약속"이라고 정의했다. 그 이후로 스마트 컨트랙트의 개념은, 특히 2009년 비트코인의 발명으로 탈중앙화 블록체인 플랫폼이 도입된 후에 진화했다. 이더리움의 컨텍스트에서 이더리움 스마트 컨트랙트는 스마트하지도 않고 법적 컨트랙트도 아니기 때문에 다소 잘못된 이름임에도 이미 확고하게 자리를 잡았다. 이 책에서는 '스마트 컨트랙트'라는 용어를 불변적인(immutable) 컴퓨터 프로그램을 지칭하는데, 이 프로그램은 이더리움 네트워크 프로토콜(즉, 탈중앙화된 이더리움 월드 컴퓨터)의 일부인 이더리움 가상 머신의 컨텍스트상에서 결정론적으로(deterministically) 작동한다. 이제 스마트 컨트랙트의 정의를 살펴보자.

**컴퓨터 프로그램(computer programs)**

* 스마트 컨트랙트는 단순히 컴퓨터 프로그램이다. '컨트랙트(contract)'라는 단어는 이런 맥락에서 법적인 의미는 없다.

**불변의(immutable)**

* 스마트 컨트랙트 코드는 일단 배포되면, 변경할 수 없다. 기존 소프트웨어와 달리 스마트 컨트랙트를 수정하는 유일한 방법은 새로운 인스턴스를 배포하는 것이다.

**결정론적(deterministic)**

* 스마트 컨트랙트를 실행한 결과물은 그것을 실행한 모든 이에게 동일한데, 실행을 시작한 트랜잭션의 컨텍스트와 실행 시점에 이더리움 블록체인의 상태가 동일하다는 전제가 있기 때문이다.

**EVM 컨텍스트(EVM context)**

* 스마트 컨트랙트는 매우 제한적인 실행 컨텍스트에서 작동한다. 이들은 자신의 상태, 호출한 트랜잭션의 컨텍스트 및 가장 최근 블록의 일부 정보에 접근할 수 있다.

**탈중앙화된 월드 컴퓨터(decentralized world computer)**

* EVM은 모든 이더리움 노드에서 로컬 인스턴스로 실행되지만, EVM의 모든 인스턴스는 동일한 초기 상태에서 작동하고 동일한 최종 상태를 생성하기 때문에 시스템 전체가 단일 '월드 컴퓨터'로 작동한다.

## **2. 스마트 컨트랙트의 생명주기**

스마트 컨트랙트는 일반적으로 솔리디티 같은 고급 언어로 작성된다. 그러나 컨트랙트를 실행하려면 EVM에서 실행되는 저수준의 바이트코드로 컴파일되어야 한다. 일단 컴파일되면 고유한 `컨트랙트 생성(contract creation)` 트랜잭션을 사용하여 이더리움 플랫폼에 배포되며, 이 트랜잭션은 고유한 컨트랙트 생성 주소, 즉 0x0으로 전송된다('특별 트랜잭션: 컨트랙트 생성'절 참고). 각 컨트랙트는 이더리움 주소로 식별되며, 이 주소는 원래 계정 및 논스의 함수로 컨트랙트 생성 트랜잭션에서 파생된다. 컨트랙트의 이더리움 주소는 트랜잭션에서 수신자로 사용되거나 컨트랙트에 자금을 보내거나 컨트랙트 함수를 호출하는 데 사용할 수 있다. EOA와 달리 새 스마트 컨트랙트를 위해 생성한 계정과 관련된 키는 없다. 컨트랙트 작성자는 프로토콜 수준에서 특별한 권한을 얻지 못한다(명시적으로 스마트 컨트랙트로 코드를 작성할 수는 있지만). 여러분은 분명히 컨트랙트 계정을 위한 개인키(실제 존재하지 않음)를 받지 못한다. 여기서 우리는 스마트 컨트랙트 계정은 그들 자체를 소유하고 있다고 말할 수 있다.

중요한 것은 컨트랙트가 `트랜잭션에 의해 호출된 경우에만 실행된다`는 것이다. 이더리움의 모든 스마트 컨트랙트는 EOA에서 시작된 트랜잭션으로 인해 실행된다. 컨트랙트는 다른 컨트랙트를 호출할 수 있고 그 컨트랙트는 또 다른 컨트랙트를 호출할 수 있지만, 이러한 체인에서 첫번째 컨트랙트 실행은 항상 EOA로부터 트랜잭션에 의해 호출된다. 컨트랙트는 '자체적으로' 또는 '백그라운드'에서 실행되지 않는다. 스마트 컨트랙트는 체인의 일부분으로 트랜잭션에 의해 직접 혹은 간접적으로 호출되기 전까지는 대기 상태에 놓여 있다. 스마트 컨트랙트가 '병렬적으로' 실행되지 않는다는 점도 주목할 만하다. 이런 의미에서 이더리움 월드 컴퓨터가 단일 스레드 컴퓨터라 할 수 있다.

트랜잭션은 호출하는 컨트랙트 수 또는 호출 시 해당 컨트랙트가 수행하는 작업과 상관없이 `원자성(atomic)`의 특징을 지닌다. 트랜잭션은 모든 실행이 성공적으로 종료된 경우에만 글로벌 상태(컨트랙트, 계정 등)의 모든 변경사항이 기록되고 전체가 실행된다. 성공적인 종료는 프로그램이 오류 없이 실행되었고 실행의 끝까지 도달했음을 의미한다. 오류로 인해 실행이 실패하면 모든 영향(상태 변경)은 트랜잭션이 실행되지 않은 것처럼 '롤백(roll back)'된다. 실패한 트랜잭션은 여전히 시도된 것으로 기록되며, 실행을 위해 가스로 소비된 이더는 원 계정에서 차감되지만, 컨트랙트 또는 계좌 상태에는 영향을 미치지 않는다.

이전에 언급했듯이, 컨트랙트 코드는 변경할 수 없다는 사실을 기억하는 것이 중요하다. 그러나 컨트랙트를 '삭제'하여 해당 주소에서 코드와 내부 상태(스토리지)를 제거하고 빈 계정으로 남길 수 있다. 컨트랙트가 삭제된 후 해당 계정 주소로 전송된 트랜잭션은 더 이상 코드가 실행되지 않는다. 컨트랙트를 삭제하려면 SELFDESTRUCT(이전에는 SUICIDE라고 불림)라는 EVM 연산코드를 실행해야 한다. 이 작업은 '음의 가스(negative gas)', 즉 가스 환불이 일어나기 때문에 저장된 상태의 삭제로 인한 네트워크 클라이언트 자원을 반환하도록 하는 동기부여를 만든다. 이 방법으로 컨트랙트를 삭제해도 컨트랙트의 트랜잭션 내역(과거)이 제거되지는 않는다. 그 이유는 블록체인 자체를 변경하는 것은 불가능하기 때문이다. 또한 SELFDESTRUCT 기능은 컨트랙트 작성자가 해당 기능을 갖기 위해 스마트 컨트랙트를 프로그래밍한 경우에만 사용할 수 있다는 점도 중요하다. 컨트랙트 코드에 SELFDESTRUCT 연산코드가 없거나 접근할 수 없는 경우 스마트 컨트랙트는 삭제할 수 없다.

## **3. 이더리움 고급 언어의 소개**

EVM은 x86_64 같은 머신 코드를 실행하는 컴퓨터의 CPU와 유사한 `EVM 바이트코드`라는 특수한 형태의 코드를 실행하는 가상 머신이다. 13장에서 EVM의 작동 및 언어를 자세히 살펴볼 것이다. 이 장에서는 EVM에서 스마트 컨트랙트가 실행된느 방법을 살펴보겠다.

스마트 컨트랙트를 바이트코드로 직접 프로그래밍할 수는 있지만, EVM 바이트코드는 다루기가 까다로워서 프로그래머가 잃고 이해하기가 매우 어렵다. 대신, 대부분의 이더리움 개발자는 프로그램을 작성하는 데 고급 언어를 사용하고 바이트코드로 변환하는 컴파일러를 사용한다.

모든 고급 언어가 스마트 컨트랙트를 작성하는 데 적합할 수는 있지만, EVM 바이트코드에 컴파일할 수 있도록 임의의 언어를 적용하는 것은 일반적으로 상당히 번거롭고 혼란스럽다. 스마트 컨트랙트는 고도로 제한된 최소 실행 환경(EVM)에서 작동한다. 또한 EVM 관련 세부 시스템 변수 및 기능 세트를 사용할 수 있어야 한다. 따라서 스마트 컨트랙트를 작성하는 데 적합한 범용 언어를 만드는 것보다 스마트 컨트랙트 언어를 처음부터 만드는 것이 더 쉽다. 그 결과로 스마트 컨트랙트를 프로그래밍하기 위해 많은 특수 용도의 언어가 등장했다. 이더리움에는 EVM 실행 가능 바이트코드를 생성하는 데 필요한 컴파일러와 여러 언어가 있다.

일반적으로 프로그래밍 언어는 `선언형(declarative)` 프로그래밍과 `명령형(imperative)` 프로그래밍이라는 두 가지 프로그래밍 패러다임으로 분류할 수 있다. `함수형(functional)` 프로그래밍과 `절차적(procedural)` 프로그래밍이라고도 한다. 선언형 프로그래밍에서는 프로그램의 `논리(logic)`를 표현하지만, 그 `흐름(flow)`은 표현하지 않는 함수를 작성한다. 선언형 프로그래밍은 `부작용(side effect)`이 없는 프로그램을 만드는 데 사용된다. 다시 말하면, 프로그램에 의해 함수 외부의 상태는 변경되지 않는다. 선언형 프로그래밍 언어에는 하스켈(Haskell)과 SQL이 포함된다. 반대로, 명령형 프로그래밍은 프로그래머가 프로그램의 논리와 흐름을 결합하는 일련의 절차를 작성한다. 명령형 프로그래밍 언어에는 C++ 및 자바가 포함된다. 일부 언어는 '하이브리드(hybrid)'로서 선언형 프로그래밍을 권장하지만, 명령형 프로그래밍 패러다임을 표현하는 데 사용할 수도 있다. 이러한 하이브리드에는 리스프(Lisp), 자바스크립트(JavaScript), 파이썬(Python)이 포함된다. 일반적으로 선언형 패러다임 작성에 명령형 언어를 사용할 수는 있지만, 종종 어색한 경우가 있다. 반면, 순수한 선언형 언어에는 '변수(variable)'가 없다. 즉, 이 언어는 명령형 패러다임 작성에 사용할 수 없다.

명령형 프로그래밍은 프로그래머가 일반적으로 사용하지만, '예상대로 정확하게' 실행되는 프로그램을 작성하는 것은 매우 어려울 수 있다. 프로그램의 모든 부분이 다른 프로그램의 상태를 변경하는 기능은 프로그램 실행에 관한 추론을 어렵게 만들고 버그 발생률도 높다. 이와 달리 선언형 프로그래밍은 프로그램이 어떻게 작동하는지 쉽게 이해할 수 있게 한다. 부작용이 없으므로 프로그램의 모든 부분을 독립적으로 이해할 수 있다.

스마트 컨트랙트에서 버그는 말 그대로 비용을 발생시킨다. 따라서 부작용 없는 스마트 컨트랙트를 작성하는 것이 중요하다. 그렇게 하기 위해서는 프로그램 동작에 대해 명확하게 추론할 수 있어야 한다. 따라서 선언형 언어는 범용 소프트웨어에서보다 스마트 컨트랙트에서 훨씬 더 큰 역할을 한다. 그럼에도 불구하고 스마트 컨트랙트에 가장 널리 사용되는 언어(솔리디티)는 명령형 언어다. 프로그래머는 대부분의 사람과 마찬가지로 변화를 쉽게 받아들이지 않기 때문이다.

스마트 컨트랙트에 대해 현재 지원되는 고급 프로그래밍 언어는 다음과 같다(개발 순서에 따라).

**LLL(Low-level Lisp-like Language)**

* 리스프(Lisp)와 유사한 구문을 사용하는 함수형(선언형) 프로그래밍 언어다. 이더리움 스마트 컨트랙트의 첫 번째 고급 언어였지만 지금은 거의 사용되지 않는다.

**서펀트(Serpent)**

* 파이썬과 유사한 구문을 사용하는 절차적(명령형) 프로그래밍 언어다. 부작용이 전혀 없는 것은 아니지만 함수형(선언형) 코드를 작성하는 데도 사용할 수 있다.

**솔리디티(Solidity)**

* 자바스크립트, C++, 자바와 유사한 구문을 사용하는 절차적(명령형) 프로그래밍 언어이며, 이더리움 스마트 컨트랙트에서 가장 널리 사용되고 자주 사용되는 언어다.

**바이퍼(Vyper)**

* 최근에 개발된 언어로서 서펀트나 파이썬과 비슷한 구문을 사용하며, 서펀트보다 파이썬과 비슷한 순수한 언어에 가깝지만 서펀트를 대체하지는 않는다.

**밤부(Bamboo)**

* 얼랭(Erlang)의 영향을 받았으며, 명시적 상태 전이와 반복 흐름(루프)이 없는 새로 개발된 언어다. 부작용을 줄이고 감사 기능을 높이기 위한 것으로, 아주 새롭지만 아직 널리 채택되지는 않는다.

보다시피, 선택할 수 있는 언어가 많이 있다. 그러나 이러한 언어 중 솔리디티는 이더리움을 비롯해 비슷한 EVM 시스템을 사용하는 블록체인들의 사실상의 표준 고급 언어라고 할 수 있을 만큼 가장 인기가 높다. 우리는 대부분 솔리디티를 사용하지만, 다른 고급 언어의 철학에 대한 이해를 얻기 위해 다른 언어도 탐구할 것이다.

## **4. 솔리디티로 스마트 컨트랙트 생성**

솔리디티는 개빈 우드에 의해 창안되었으며, 명시적으로 스마트 컨트랙트 작성을 위해 만들어진 언어인데, 이더리움 월드 컴퓨터의 탈중앙화된 환경에서의 실행을 직접적으로 지원한다. 그 결과, 언어의 속성이 매우 일반적이어서 다른 여러 블록체인 플랫폼에서 스마트 컨트랙트를 코딩하는 데 사용된다. 솔리디티는 크리스티안 라이티웨스너(Christian Reitiwessner)와 알렉스 베레그자시(Alex Beregszaszi), 리아나 후시키안(Liana Husikyan), 요이치 히라이(Yoichi Hirai)와 몇몇의 전 이더리움 코어 개발자들에 의해 개발되었다. 솔리디티는 이제 [깃허브](https://bit.ly/2rzgKTE)에서 독립적인 프로젝트로 개발되고 유지된다.

솔리디티 프로젝트의 주된 '제품(product)'은 솔리디티 언어로 작성된 프로그램을 EVM 바이트코드로 변환하는 솔리디티 컴파일러 solc이다. 이 프로젝트는 또한 이더리움 스마트 컨트랙트를 위한 중요한 애플리케이션 바이너리 인터페이스(Application Binary Interface, ABI) 표준을 관리한다. 솔리디티 컴파일러의 각 버전은 솔리디티 언어의 특정 버전에 해당하며, 해당 버전의 솔리디티 언어를 컴파일한다.
