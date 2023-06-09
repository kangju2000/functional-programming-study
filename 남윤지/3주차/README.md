# Chapter 6 : 변경 가능한 데이터 구조를 가진 언어에서 불변성 유지하기

> 불변성 원칙은 카피-온-라이트 copy-on-write 라고 한다

- 자바스크립트는 기본적으로 변경 가능한 구조를 사용하기 때문에 불변성 원칙 적용을 위해 직접 구현해야 한다
- 카피-온-라이트는 쓰기를 읽기로 바꾼다

> 동작을 읽기, 쓰기로 분류하기

- 읽기 : 데이터를 바꾸지 않고 정보를 꺼내는 것
	- 인자에만 의존해 정보를 가져오는 읽기 동작은 계산이다
- 쓰기 : 데이터를 바꾼다

<br/>

> 카피 온 라이트 원칙 세 단계

1. 복사본 만들기
2. 복사본 변경하기(원하는 만큼)
3. 복사본 리턴하기

<br/>

> 배열 (Array)

- 자바스크립트의 기본 컬렉션으로 순서가 있는 값을 나타낸다
- 다른 타입의 항목을 동시에 가질 수 있다
- 인덱스(index) 로 요소에 접근할 수 있고 크기를 늘리거나 줄일 수 있다

> 배열 (Array)에 대한 연산

    > 인덱스로 값 찾기 [idx] : idx 위치에 있는 값 가져온다
    > 값 할당하기 [] = : 값을 할당하는 동작은 배열을 변경한다
    > 길이 .length : 배열 항목의 개수를 알려준다
    > 끝에 추가하기 .push(el) : 배열 끝에 el 을 추가해 배열을 변경한다 새로운 길이를 리턴한다
    > 끝에 있는 값 지우기 .pop() : 끝에 있는 값을 지워 배열을 변경한다 지운 값을 리턴한다
    > 앞에 추가하기 .unshift(el) : 배열 앞에 el 을 추가해 배열을 변경한다 새로운 길이를 리턴한다
    > 앞에 있는 값을 지우기 .shift() : 맨 앞에 있는 값을 지우고 배열을 변경한다 지운 값을 리턴한다
    > 배열 복사하기 .slice() : 배열을 얕게 복사해서 새로운 배열을 리턴한다
    > 항목 삭제하기 .splice(idx, num) : idx 위치에서 num 개 항목을 지워 배열을 변경한다 지운 항목을 리턴한다

<br/>

> 쓰기를 하면서 읽기도 하는 동작 분리에는 두가지 접근 방법이 있다

- 읽기와 쓰기 함수로 각각 분리한다
- 함수에서 값을 두 개 리턴하기

<br/>

> 불변 데이터 구조를 읽는 것은 계산이다

    > 변경 가능한 데이터를 읽는 것은 액션이다
		- 값을 읽을 때마다 다른 값을 읽을 수 있음 - 액션은 시점에 의존하기 때문
    > 쓰기는 데이터를 변경 가능한 구조로 만든다
    > 어떤 데이터에 쓰기가 없다면 데이터는 변경 불가능한 데이터이다
    > 불변 데이터 구조를 읽는 것은 계산이다
    > 쓰기를 읽기로 바꾸면 코드에 계산이 많아진다

<br/>

> 불변 데이터 구조는 충분히 빠르다

    > 언제든 최적화할 수 있다
    > 가비지 콜렉터는 매우 빠르다
    > 생각보다 많이 복사하지 않는다
		- 데이터 구조의 최상위 단계만 복사하는 것을 얕은 복사라고 한다
		- 얕은 복사는 같은 메모리를 가리키는 참조에 대한 복사본을 만든다 - 구조적 공유
    > 함수형 프로그래밍 언어에는 빠른 구현체가 있다

<br/>

> 얕은 복사(shallow copy) 는 중첩된 데이터 구조에 최상위 데이터만 복사한다<br/>
> 구조적 공유(structural sharing) 는 두 개의 중첩된 데이터 구조가 어떤 참조를 공유하는 것을 말한다<br/>
	- 데이터가 바뀌지 않는 불변 데이터 구조라면 구조적 공유는 안전하다<br/>
	- 구조적 공유는 메모리를 적게 사용하고 모든 것을 복사하는 것 보다 빠르다

<br/>

> 객체 (Object)

- 다른 언어의 해시 맵이나 연관 배열과 비슷하다

> 객체에 대한 연산

    > 키로 값 찾기 [key] : key 로 값을 찾는다 없으면 undefined 가 나온다
    > 키로 값 찾기 .key : 점 연산자로 값을 찾을 수 있다
    > 키로 값 설정하기 .key 또는 [key] = : 만약 키가 있다면 값을 바꾸고 없다면 값을 추가한다
    > 키/값 쌍 지우기 delete : 주어진 키로 해당 키/값 쌍을 지운다
    > 객체 복사하기 Object.assign(a,b) : b 객체의 모든 키 값을 a 객체로 복사한다
    > 키 목록 가져오기 Object.keys() : 모든 키를 가져온다
