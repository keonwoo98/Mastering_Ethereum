# **Chapter 1. 이더리움이란 무엇인가?**
> 본 글은 『Mastering Ethereum』을 읽고 정리한 내용입니다.

이더리움은 종종 `월드 컴퓨터(world computer)`라고 하는데, 그 의미는 무엇일까?

컴퓨터 과학의 관점에서 보자면 이더리움은 결정론적(deterministic)이지만, 사실상 한정되지 않은 상태 머신(unbounded state machine)이며, 이것은 전역적으로(globally) 접근 가능한 싱글톤(singleton) 상태와 그 상태를 변화시킬 수 있는 가상 머신으로 구성되어 있다.

좀 더 실용적인 관점에서 볼 때, 이더리움은 `스마트 컨트랙트(smart contract)`라는 프로그램을 실행하는 오픈 소스에 기반을 둔, 전 세계에 걸쳐 탈중앙화된 컴퓨팅 인프라스트럭처이다. 블록체인을 사용하여 시스템의 상태 변화를 동기화하고 저장하며, `이더(ether)`라고 하는 암호화폐를 이용하여 실행 자원 비용을 측정하고 제한한다.

개발자는 이더리움 플랫폼을 사용해서 경제적 기능들을 내장한 강력하면서도 탈중앙화된 애플리케이션을 개발할 수 있다. 그리고 이더리움 플랫폼은 고가용성, 감사 가능성, 투명성, 중립성을 제공하는 동시에 검열을 줄이거나 없애고, 거래상대방의 위험을 줄인다.

## **1. 비트코인과의 비교**

공통점
* P2P 네트워크
* 비잔틴 결함 허용 합의 (Byzantine fault-tolerant consensus) 알고리즘(작업증명 블록체인)
* 디지털 서명과 해시
* 디지털 화폐(이더) 같은 암호학 기반 기술 사용

차이점
* 단순 디지털 화폐 지급 네트워크가 목적인 비트코인과 달리,
* 이더의 사용 목적은 월드 컴퓨터로서의 이더리움 플랫폼 사용료를 지불하기 위한 `유틸리티 화폐(utility currency)`이다.
* 매우 제한된 스크립트 언어를 사용하는 비트코인과 달리,
* 이더리움은 임의성과 무한 복잡성을 가진 코드를 실행할 수 있는 `가상 머신(virtual machine)`을 운영하는 범용 프로그래밍이 가능한 블록체인이다.
* 비트코인의 스크립트 언어가 의도적으로 지불 조건에 대한 단순한 참/거짓 평가에만 제한되어 있는 반면,
* 이더리움 언어는 `튜링완전(Turing complete)` 언어이다. (이더리움이 범용 컴퓨터로 직접 작동할 수 있음을 의미)

## **2. 블록체인 구성요소**

공개 블록체인(public blockchain)의 구성요소는 일반적으로 다음과 같다.

* 표준화된 `가십(gossip)` 프로토콜을 기반으로 참여자를 연결하고 트랜잭션 및 검증된 트랜잭션 블록을 연결하는 peer-to-peer(P2P) 네트워크
* 상태 전이를 나타내는 트랜잭션 형식의 메시지
* 트랜잭션의 구성 요건과 트랜잭션의 유효성을 판단하는 합의 규칙의 집합
* 합의 규칙에 따라 트랜잭션을 처리하는 상태 머신
* 검증되고 적용된 모든 상태 전이의 장부(journal) 역할을 해줄 수 있는, 암호학적으로 보호된 체인(chain)
* 합의 규칙들을 적용하는 데 모든 참여자가 협력할 수 있도록 강제함으로써 블록체인의 통제 권한을 탈중앙화하는 합의 알고리즘
* 공개된 환경에서 상태 머신에 경제적인 보안성을 제공할 수 있는 게임 이론적으로 유효한 인센티브 메커니즘 (ex: 작업증명 비용 + 블록 보상)
* 위에서 언급된 것들을 구현한 하나 이상의 오픈 소스 소프트웨어 (clients)

일반적으로 이러한 구성요소의 전부 또는 대부분은 단일 소프트웨어 클라이언트로 통홥된다.

예를 들어, 비트코인에서 기준이 되는 구현제(reference implementation)는 `비트코인 코어(Bitcoin Core)` 오픈 소스 프로젝트가 개발하고, 이것은 `bitcoind`라는 클라이언트 소프트웨어로 개발된다.

이와 달리, 이더리움에서는 기준이 되는 구현제가 아닌 `기준 사양(reference specification`)을 사용하는데, 황서(Yellow Paper)에서 밝히고 있는 시스템의 수학적 기술이 바로 그것이다. 그래서 이더리움에는 기준 사양에 따라 만들어진 많은 클라이언트가 있다.

오늘날, 서로 다른 속성을 지닌 많은 종류의 블록체인이 존재하기 때문에 위의 구성요소들을 가지고 다음과 같은 블록체인의 핵심적인 특징들을 지니고 있는지 살펴보아야 한다.

블록체인의 핵심적인 특징
* 개방성 (open)
* 공공성 (public)
* 국제화 (global)
* 탈중앙화 (decentralized)
* 중립성 (neutral)
* 검열 저항성 (censorship-resistant) 등

## **3. 이더리움의 탄생**

사람들이 비트코인 모델의 힘을 인식하고 암호화폐 애플리케이션을 넘어서려고 시도했던 당시 이더리움도 구상되기 시작됐다. 당시 개발자들은 비트코인 기반 위에 구축하거나, 아니면 새로운 블록체인을 시작해야하는 난제에 직면했다. 비트코인 기반 위에 구축한다는 건, 네트워크의 의도적인 제약 조건들을 전제한 상태에서 해결책을 찾아야 한다는 뜻이었다. 제한된 트랜잭션 타입, 제한된 애플리케이션 종류, 공개 블록체인을 사용하는 장점을 없애야하는 문제 등 많은 제약 사항과 수많은 작업을 필요로 했다.

2013년 말 비트코인 지지자 프로그래머인 비탈릭 부테린(Vitalik Buterin)은 튜링 완전한 범용 블록체인인 이더리움의 개념을 설명하는 화이트 페이퍼를 공유했고 수십 명의 사람이 이 초기 초안을 살펴보고 제안서를 발전시킬 수 있도록 의견을 제시했다. 그 중 게빈 우드(Dr. Gavin Wood) 박사는 비탈릭에게 먼저 연락하여 C++ 프로그래밍 기술을 도와주겠다고 제안했고 이후 이더리움의 공동 설립자이자 공동 설계자이자 CTO가 되었다.

2013년 12월부터 비탈릭과 개빈은 아이디어들을 개선하고 진화시켜 지금의 이더리움이 된 프로토콜 계층을 구축했다.

사토시(Satoshi)와 마찬가지로, 비탈릭과 개빈은 단시 새로운 기술을 발명한 것이 아니었다. 발명한 신기술과 기존 기술을 새로운 방식으로 결합했고, 그들의 아이디어를 세상에 증명하기 위해 프로토타입 코드를 배포했다.

창립자들은 수년간 비전을 구축하고 개선했다. 그리고 2015년 7월 30일, 첫 번째 이더리움 블록이 채굴되었다. 드디어 월드 컴퓨터가 세상에 서비스를 제공하기 시작한 것이다.

## **4. 이더리움 개발의 4단계**

이더리움은 `프론티어(Frontier)`, `홈스테드(Homestead)`, `메트로폴리스(Metropolis)`, `세레니티(Serenity)` 이렇게 네 단계로 나누어 진행되었으며, 각 단계에는 이전 버전과 호환되지 않는 방식으로 기능을 변경하는 하드 포크(hard fork)라고 하는 하위 버전이 포함될 수 있다.

**블록 #0**

* `프론티어(Frontier)` : 2015년 7월 30일부터 2016년 3월까지 지속된 이더리움 초기 단계

**블록 #200,000**

* `아이스 에이지(Ice Age)` : 기하급수적으로 증가하는 난의도 증가를 도입하여 지분증명(PoS)으로 전환하도록 동기를 부여하는 하드 포크

**블록 #1,150,000**

* `홈스테드(Homestead)` : 2016년 3월에 시작된 이더리움의 두 번째 단계

**블록 #1,192,000**

* `DAO` : 해킹된 DAO 컨트랙트의 피해자에게 보상금을 지급하고 이더리움 및 이더리움 클래식을 2개의 경쟁 시스템으로 분할하는 하드 포크

**블록 #2,463,000**

* `탠저린 휘슬(Tangerine Whistle)` : 특정 I/O가 많은 작업에 대한 가스 계산을 변경하고, 해당 작업의 가스 비용이 낮은 서비스를 거부(Denial-of-Service, DoS) 공격으로부터 축적된 상태를 지우는 하드 포크

**블록 #2,675,000**

* `스퓨리어스 드래곤(Spurious Dragon)` : 더 많은 DoS 공격 벡터를 처리하고 다른 상태를 지우는 하드 포크. 또한 재생 공격 방지 메커니즘

**블록 #4,370,000**

* `메트로폴리스 비잔티움(Metropolis Byzantium)` : 메트로폴리스는 이더리움의 세 번째 단계로, 2017년 10월에 하드 포크되었으며 이 책을 저술한 시점이기도 하다. 비잔티움은 메트로폴리스를 위해 계획된 2개의 하드 포크 중 첫 번째인 것이다.

비잔티움 이후에 메트로폴리스를 위해 계획된 또 하나의 하드 포크는 콘스탄티노플이다. 메트로폴리스에 이어서 이더리움의 마지막 단계인 세레니티(Serenity)가 나올 것이다.

## **5. 이더리움 : 범용 블록체인**

비트코인은 트랜잭션이 `상태 전이(state transition)`를 일으켜 코인의 소유권을 변경하는 탈중앙화된 합의 `상태 머신(state machine)`이라고 생각할 수 있다. 상태 전이는 여러 블록이 채굴된 후 모든 참가자가 시스템의 공통(합의) 상태로 수렴할 수 있도록 합의 규칙에 의해 제한된다.

이더리움 또한 탈중앙화 상태 머신이긴 하지만 화폐 소유 상태만 추적하는 것이 아니라 범용 데이터 저장소, 즉 `키-밸류 튜플(key-value tuple)`로 표현할 수 있는 모든 데이터를 저장할 수 있는 저장소의 상태 전이를 추적한다.

어떤 면에서는 대부분의 범용 컴퓨터에서 사용되는 `랜덤 액세스 메모리(Random Access Memory, RAM)`의 데이터 스토리지 모델과 비슷한 용도로 사용된다. 이더리움에는 코드와 데이터를 저장하는 메모리가 있으며, 이더리움은 블록체인을 사용하여 이 메모리가 시간에 따라 어떻게 변하는지를 추적한다. 범용 저장 프로그램 컴퓨터와 마찬가지로, 이더리움은 상태 머신에 코드를 로드하고 그 코드를 실행하고 그 결과 상태를 저장할 수 있다. 범용 컴퓨터 대부분과의 가장 큰 차이점은 이더리움의 상태 변화가 합의 규칙에 의해 관리되고 상태가 전체적으로 배포된 다는 것이다. 말하자면, 이더리움은 다음과 같은 질문에 대한 대답이다.

"임의의 상태를 추적하고 상태 머신을 프로그래밍하여 합의로 작동하는 월드-와이드 컴퓨터를 만들 수 있다면 어떨까요?"

## **6. 이더리움의 구성요소**

`피어투피어 네트워크(P2P network)`

* 이더리움은 TCP 포트 3030으로 접속 가능한 `이더리움 메인 네트워크(Ethereum main network)`에서 실행되며, `ÐΞVp2p`라는 프로토콜을 실행한다.

`합의 규칙(consensus rules)`

* 이더리움의 합의 규칙은 기준 사양인 황서(Yello Paper)에 정의되어 있다.

`트랜잭션(transactions)`

* 이더리움 트랜잭션은 보낸 사람, 받는 사람, 값 및 데이터 페이로드가 포함된 네트워크 메시지이다.

`상태 머신(state machine)`

* 이더리움 상태 전이는 `바이트코드(bytedoce, 기계어 명령어)`를 실행하는 스택 기반 가상 머신인 `EVM(Ethereum Virtual Machine)`에 의해 처리된다. `스마트 컨트랙트`라는 `EVM` 프로그램은 고수준 프로그래밍 언어(ex: Solidity)로 작성되고, EVM에서 실행되도록 바이트코드로 컴파일된다.

`데이터 구조(data structures)`

* 이더리움의 상태는 트랜잭션 및 시스템 상태가 `머클 패트리샤 트리(Merkle Patricia Tree)`라고 하는 시리얼라이즈(serialize)된 해시 데이터 구조로, 각 노드의 `데이터베이스(database, 일반적으로 구글의 DB(LevelDB))`에 저장된다.

`합의 알고리즘(consensus algorithm)`

* 이더리움은 비트코인의 합의 모델인 나카모토 합의(Nakamoto Consensus)를 사용한다. 나카모토 합의는 순차 단일 서명 블록을 사용하여 작업증명(PoW)의 중요도 가중치가 가장 긴 체인(현재 상태)을 결정한다. 그러나 조만간 지분증명(PoS) 가중 투표 시스템인 코드명 `캐스퍼(Casper)`로 전환할 계획이다.

`경제적 보안성(economic security)`

* 이더리움은 현재 `이대시(Ethash)`라는 작업증명(PoW) 알고리즘을 사용하지만, 향후엔 결국 지분증명(PoS) 알고리즘을 사용할 예정이다.

`클라이언트(clients)`

* 이더리움은 클라이언트 소프트웨어를 상호운용할 수 있는 몇 가지 구현체를 갖고 있는데, 가장 유명한 것은 `게스(Go-Ethereum, Geth)`와 `패리티(Parity)`이다.

## **7. 이더리움과 튜링 완전**

이더리움에 관해 읽을 때 `튜링 완전`이라는 용어를 많이 접하게 될텐데 이 용어는 컴퓨터 과학의 아버지로 불리는 영국인 수학자 `앨런 튜링(Alan Turing)`이 사용하였다.

1936년 그는 순차적 메모리(무한 길이의 종이 테이프와 유사)에서 기호를 읽고 쓰는 방식으로 기호를 조작하는 상태 머신으로 구성된 컴퓨터의 수학적 모델을 만들었다. 이 구성을 통해 튜링은 모든 문제를 해결할 수 있는지를 나타내는 `보편적 계산 가능성(universal computability)`에 대한 (부정적인) 질문에 답하기 위해 수학적 기초를 제공했다. 그는 계산할 수 없는 문제가 있음을 증명했다. 구체적으로 말하자면, 그는 `정지 문제`(halting, problem, 임의로 주어진 튜링 머신이 주어진 입력 테이프에 대해 정지하는가 정지하지 않는가를 판정하는 알고리즘의 존재 여부를 묻는 문제)가 해결 되지 않는 다는 것을 증명했다.

앨런 튜링은 튜링 머신을 시뮬레이션하는 데 사용할 수 있다면 `튜링 완전하다(Turing complete)`고 정의했다. 이러한 시스템을 `UTM(Universal Turing machine)`이라고 한다.

이더리움 가상 머신이라는 상태 머신상에서 메모리에 데이터를 읽고 쓰면서 저장된 프로그램을 실행할 수 있는 이더리움 기능은 튜링 완전 시스템을 가능하게 하므로 `UTM`이라고 볼 수 있다. 이더리움은 한정된 메모리라는 제한 조건에서 모든 튜링 머신으로 계산될 수 있는 어떠한 알고리즘도 계산할 수 있다.

이더리움의 획기적인 혁신은 저장된 프로그램 컴퓨터의 범용 컴퓨팅 아키텍처와 탈중앙화된 블록체인을 결합하여 탈중앙화된 단일 상태(싱글톤) 월드 컴퓨터를 만든 것이다. 이더리움 프로그램은 `어디에서나` 실행되지만, 합의 규칙에 의해 보장되는 공통 상태를 만들어낸다.

### **7-1. `기능`으로서의 튜링완전**

튜링 불완전한 시스템은 뭔가 빠진 기능이 있을 거라고 생각할 수 있지만 오히려 정반대로 튜링 완전은 아주 쉽게 달성할 수 있다.

그러나 튜링 완전은 특히 개방형 액세스(open access) 시스템에서는 매우 위험하다. 정지 문제 때문이다. 예를 들어, 최신 프린터들은 튜링 완전해서 프린터가 작동 불능 상태가 될 떄까지 인쇄 명령을 받을 수도 있다. 사실, 튜링 완전은 이더리움이 어떠한 복잡한 프로그램이라도 계산할 수 있음을 의미한다. 그러나 이러한 유연성은 보안과 자원 관리에 몇 가지 어려운 문제를 야기한다. 응답이 없는 프린터는 껐다가 다시 켜야 하지만, 이는 공개 블록체인에서는 불가능하다.

### **7-2. 튜링 완전의 함축적 의미**

튜링은 컴퓨터에서 프로그램을 시뮬레이션하여 프로그램 종료 여부를 예측할 수 없음을 증명했다. 간단히 말하자면, 프로그램을 실행하지 않고서는 프로그램의 경로를 예측할 수 없다. 튜링 완전 시스템은 종료되지 않는 프로그램을 설명하기 위해 무한 루프에서 실행될 수 있다. 시작 조건과 코드 간의 복잡한 상호작용으로 인해 의도하지 않은 무한 반복 루프가 경고 없이 발생할 수 있다. 이더리움에서 이것은 하나의 도전 과제다. 모든 참여 노드(클라이언트)는 모든 트랜잭션을 검증하고 그 트랜잭션이 호출하는 스마트 컨트랙트를 실행해야 한다. 그러나 튜링이 증명한 것처럼, 이더리움은 스마트 컨트랙트가 종료될지 혹은 실제로 스마트 컨트랙트를 실행하지 않고 얼마나 오랫동안 실행될지를 예측할 수 없다. (경우에 따라서는 무한 실행의 가능성도 있음) 노드가 유효성 검사를 시도할 때 우연히 또는 의도적으로 스마트 컨트랙트가 영원히 지속하도록 만들 수도 있다. 이것은 사실상 서비스 거부 공격이다. 월드 컴퓨터에서 자원을 남용하는 프로그램은 세계의 자원을 남용한다. 이더리움이 사전에 자원 사용을 예측할 수 없다면 스마트 컨트랙트가 사용하는 자원을 어떻게 제한할까?

이 질문에 대답하기 위해 이더리움은 `가스(gas)`라는 과금 메커니즘을 도입힌다. EVM이 스마트 컨트랙트를 실행하게 되면, 가스는 각 명령어(계산, 데이터, 접근 등)의 비용을 일일히 계산한다. 각 명령어는 가스 단위로 미리 정해진 비용이 있다. 스마트 컨트랙트를 실행시킬 때 트랜잭션은 스마트 컨트랙트를 실행하는 데 사용할 수 있는 가스의 최대 사용량을 가지고 있어야 한다. 만약 계산에 소비되는 가스의 총량이 트랜잭션에서의 가스 가용량을 초과한다면 EVM은 실행을 중지할 것이다. 가스는 각 프로그램이 사용할 수 있는 리소스를 제한해서 이더리움 튜링 완전 계산을 허용하게 하는 메커니즘이다.

다음으로 물어볼 수 있는 질문은 `"이더리움 월드 컴퓨터에서 계산 비용을 지급하기 위한 가스를 어떻게 얻는가?"`이다. 어떠한 거래소에서도 가스를 직접 취급하는 곳은 찾을 수 없다. 오직 트랜잭션의 부분 구성요소로서만 구매할 수 있으며, 이더로만 살 수 있다. 이더는 트랜잭션과 홤께 보내야 하고, 가스 구매를 위해서 허용 가능한 가격을 명시적으로 지정해야 한다. 주유소처럼 가스의 가격은 정해져 있지 않다. 트랜잭션을 위해 가스가 구매되고, 계산을 수행하고, 사용하지 않은 가스는 발신자에게 반환된다.

## **8. 범용적인 블록체인에서 탈중앙화 애플리케이션(DApp)으로**

`DApp`은 공개되고 탈중앙화된 peer-to-peer 기반 서비스 위에 제공되는 웹 애플리케이션이다.

`DApp`의 최소 구성
* 블록체인 스마트 컨트랙트
* 웹 프런트엔드 사용자 인터페이스

`DApp`의 탈중앙화 구성요소
* 탈중앙화(P2P) 스토리지 프로토콜과 플랫폼
* 탈중앙화(P2P) 메시지 프로토콜과 플랫폼

`DApp`의 철자가 `ÐApp`으로 표시될 수 있다. `Ð` 문자는 이더리움을 암시하는 `ETH`라는 라틴문자이다.

## **9. 제3세대 인터넷**

2004년에 `Web 2.0`은 사용자 생성 콘텐츠, 반응형 인터페이스 및 상호작용성에 대한 웹의 진화를 설명하는 용어로 부각되었다. `Web 2.0`은 기술 사양이 아니라 웹 애플리케이션의 새로운 초점을 설명하는 용어이다.

`DApp`의 개념은 웹 애플리케이션의 모든 측면에서 peer-to-peer 프로토콜로 탈중앙화를 도입하여, `World Wid Web`을 자연스럽게 다음 단계로 발전시키기 위한 것이다. 웹의 세 번째 버전을 의미하는 `Web 3`은 이러한 진화를 설명하기 위해 사용하는 용어이다. 개빈 우드 박사가 처음 제안한 것으로, `Web 3`는 웹 애플리케이션에 초점을 두는 새로운 비전을 말한다. (중앙 집중적으로 관리되는 애플리케이션으로부터 탈중앙화 프로토콜에 의해 구축된 애플리케이션으로의 전환)

이후의 내용에서 이더리움 `web3.js` 라이브러리를 살펴볼 것인데 `web3.js`는 브라우저 안에서 실행되는 자바스크립트 애플리케이션과 이더리움 블록체인을 연결한다. `web3.js` 라이브러리는 또한 `스웜(Swarm)`이라는 P2P 스토리지 네트워크와 `위스퍼(Whisper)`라는 P2P 메시징 서비스를 포함한다. 이 세 가지 구성요소는 웹 브라우저에서 동작하는 자바스크립트 라이브러리에 포함되어서 개발자들은 `Web 3 DApp`을 구축할 수 있는 완전한 애플리케이션 개발 세트를 갖게 된다.

## **10. 이더리움의 개발 문화**

비트코인에서 개발은 매우 보수적인 원칙을 따른다. 모든 변경사항은 기존 시스템이 중단되지 않도록 신중하게 검토된다. 대부분의 경우 변경은 이전 변경사항과 호환이 되는 경우에만 구현된다. 기존 클라이언트는 선택적으로 새로운 변경사항의 적용 여부를 결정(opt-in)할 수 있지만, 업그레이드를 원하지 않을 때는 기존 방식 그대로 운용할 수 있다.

그에 비해 이더리움은에서는 커뮤니티의 개발 문화가 과거보다는 미래에 초점이 맞추어져 있다. 이더리움의 구호는(완전히 공식적이지는 않지만) `빨리 움직이고 파괴하라`는 것이다. 만약 변화가 필요하다면 때로는 이 변화가 이전에 설정했던 가정들을 무효화하거나, 호환성을 깨거나, 혹은 강제적인 업그레이드가 필요해지더라도 강행한다. 이더리움의 개발 문화는 이전 호환성을 다소 희생하더라도 빠른 혁신, 빠른 진화, 미래 지향적인 개선을 전개하는 것이 특징이다.

이는 개발자가 유연함을 유지하고 기본 가정의 일부가 변경되는 것에 따른 인프라스트럭처를 다시 구축할 준비를 해야 한다는 뜻이다. 이더리움에서 개발자가 직면한 가장 큰 과제 중 하나는 변경 불가능한 시스템에 코드를 배포하는 것과 여전히 진화 중인 개발 플랫폼 사이에 존재하는 본질적인 모순이다. 스마트 컨트랙트는 단순하게 '업그레이드'할 수 없다. 새로운 애플리케이션을 배포하고, 사용자와 앱, 자금을 이전하고 다시 시작할 준비가 되어야 한다.

역설적으로, 이것은 좀 더 자율적이고 덜 중앙화된 통제권을 가진 시스템을 만들겠다는 목표가 아직은 완전히 실현되지 않았다는 것을 의미한다. 자율성과 탈중앙화의 실현은 1~2년 내에 완성될 수 있을 정도의 수준보다는 더 큰 안정성이 요구된다. 플랫폼을 '진화'시키기 위해서는 스마트 컨트랙트를 폐기하고 재시작할 준비가 되어야 한다. 즉, 스마트 컨트랙트를 어느 정도 통제할 수 있어야 한다는 뜻이다.

그러나 긍정적인 측면에서 이더리움은 매우 빠르게 앞으로 나아가고 있다. 원자력 발전소 뒤에 자전거 보관소를 어떻게 만드는지와 같은 사소한 논쟁으로 개발을 지연하는 것을 의미하는 `바이크 셰딩(bike-shedding)`을 할 기회는 없다. 만약 바이크 셰딩을 시작한다면, 한눈파는 동안 나머지 개발팀이 자율 호버크래프트(hovercraft)를 위해 계획을 변경하고 자전거를 버렸음을 어느 순간 알게 될지도 모른다.

궁극적으로, 이더리움 플랫폼 역시 발전 속도가 느려지고 인터페이스들이 고정되기 시작할 것이다. 그러는 동안에도 혁신은 추진의 원천이다. 누구도 나를 위해 속도를 늦추지 않기 때문에 열심히 쫓아가야 한다.

## **11. 왜 이더리움을 배우나?**

블록체인은 하나의 도메인 내에 여러 분야를 조합함으로써(프로그래밍, 정보 보안, 암호학, 경제학, 분산 시스템, 피어투피어 네트워크 등) 학습 곡선이 매우 가파르다. 이더리움은 학습 곡선을 좀 덜 가파르게 만들어서 아주 빨리 시작할 수 있다. 그러나 언뜻 보면 매우 단순해 보이는 환경의 표면 아래에는 훨씬 더 많은 것이 놓여 있다. 공부하고 좀 더 깊이 있게 들여다보면, 복잡하고 놀라운 또 다른 계층이 늘 있다.

이더리움은 블록체인을 학습할 수 있는 훌륭한 플랫폼이고 여타 블록체인 플랫폼보다 빠르게 대규모 개발자 커뮤니티를 구축해 가고 있다. 또한 다른 어떤 블록체인보다 이더리움은 개발자가 개발자를 위해 만든 `개발자의 블록체인(developer's blockchain)`이다. 자바스크립트 애플리케이션에 익숙한 개발자라면, 작동 가능한 이더리움 코드들을 매우 빠르게 생산해 낼 수 있다. 이더리움의 초기 몇 년 동안은 '단지 5줄의 코드로 토큰을 만들 수 있다'라고 홍보하는 티셔츠를 흔히 볼 수 있었다. 물론, 이것은 양날의 검이다. 코드를 작성하는 것은 쉽다. 그러나 '좋고 안전한' 코드를 작성하기란 매우 어렵다.
