# Chapter 10 : 일급 함수1

> 코드의 냄새와 중복을 없애 추상화를 잘할 수 있는 리팩터링 방법에 대해 알아보는 챕터이다

<br />

> 코드의 냄새 : 함수 이름에 있는 암묵적 인자

- 함수 본문에서 사용하는 어떤 값이 함수 이름에 나타난다면 함수 이름에 있는 암묵적 인자는 코드의 냄새가 된다.
- 특징
  - 거의 똑같이 구현된 함수가 있다
  - 함수 이름이 구현에 있는 다른 부분을 가리킨다

<br/>

> 리팩터링 : 암묵적 인자를 드러내기

- 단계
  - 함수 이름에 있는 암묵적 인자를 확인한다
  - 명시적인 인자를 추가한다
  - 함수 본문에 하드 코딩된 값을 새로운 인자로 바꾼다
  - 함수를 호출하는 곳을 고친다

<br/>

> 리팩터링 : 함수 본문을 콜백으로 바꾸기

- 단계
  - 함수 본문에서 바꿀 부분의 앞부분과 귓부분을 확인한다
  - 리팩터링 할 코드를 함수로 빼낸다
  - 빼낸 함수의 인자로 넘길 부분을 또 다른 함수로 빼낸다

<br/>

> 일급인 것과 일급이 아닌 것을 구별해야 한다

- 자바스크립트에서 일급이 아닌 것
  - 수식 연산자
  - 반복문
  - 조건문
  - try/catch 블록
- 일급으로 할 수 있는 것
  - 변수에 할당
  - 함수의 인자로 넘기기
  - 함수의 리턴값으로 받기
  - 배열이나 객체에 담기

<br />

> 일급은 인자로 전달할 수 있다는 말이다

> 고차는 함수가 다른 함수를 인자로 받을 수 있다는 말이다

- 고차 함수 : 인자로 함수를 받거나 리턴 값으로 함수를 리턴할 수 있는 함수
- 익명 함수 : 이름이 없는 함수이다. 익명 함수는 필요한 곳에 인라인으로 쓸 수 있다

```javascript
함수를 정의하는 세가지 방법
1. 전역으로 정의하기
    - 가장 많이 쓰는 방법

function saveCurrentUserData() {
    saveUserData(user)
}

withLogging(saveCurrentUserData)

2. 지역적으로 정의하기
    - 이름은 가지고 있지만, 범위 밖에서는 쓸 수 없다

function someFunction() {
    const saveCurrentUserData = function () {
        saveUserData(user)
    }

    withLogging(saveCurrentUserData)
}

3. 인라인으로 정의하기

withLogging(function () {saveUserData(user)})

```

<br/>
