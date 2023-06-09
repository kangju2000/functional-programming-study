# Chapter 13 : 함수형 도구 체이닝

```
> 여러 단계를 하나로 조합하는 것을 체이닝이라고 한다.
```

<br />

> 체인을 명확하게 만들기

1. 단계에 이름 붙이기
    - 단계에 이름을 붙이면 훨씬 명확해지고 숨어 있던 두 함수의 구현도 알아보기 쉽다
2. 콜백에 이름 붙이기
    - 호출 그래프의 아래쪽에 위치하므로 재사용하기 좋은 코드라는 것을 알 수 있다
3. 두 방법을 비교
    - 일반적으로 두 번째 방법이 더 명확하고 재사용하기 좋다
    - 하지만 사용하는 언어의 문법과 문맥에 따라 다르니 비교해서 결정하면 된다

<br />

> filter() 나 map() 사용이 비효율적인가?

-   만들어진 배열이 필요 없을 때 가비지 컬렉터가 빠르게 처리하기 때문에 문제가 되지 않는다
-   map() 이나 filter(), reduce() 는 스트림 결합으로 쉽게 최적화가 가능하다

<br />

> 반복문을 함수형 도구로 리팩터링하기

-   전략 1. 이해하고 다시 만들기
-   전략 2. 단서를 찾아 리팩터링

<br />

> 리팩터링 팁

1. 데이터 만들기
2. 배열 전체를 다루기
3. 작은 단계로 만들기

<br />

> 체이닝 디버깅을 위한 팁

-   구체적인 것을 유지하기
    -   의미를 기억하기 쉽게 이름을 붙이면 좋다
-   출력해보기
    -   각 단계 사이에 print 구문을 넣어 코드를 돌려보면서 확인한다
-   타입을 따라가 보기
    -   타입을 따라가면서 단계를 살펴볼 수 있다

<br />

> 데이터를 사용해 창의적으로 만들기

-   인자를 데이터로 표현하면 함수형 도구를 체이닝 하기 좋다

```javascript
const itemOps = [
    ['add', 'shirt'],
    ['remove', 'shirt'],
    ['add', 'hat'],
]
```

<br />

> 정리

-   함수형 도구는 여러 단계의 체인으로 조합할 수 있다
-   기존 데이터를 사용하는 일이 있기 때문에 최대한 암묵적인 정보룰 명시적으로 표현하는 방법을 찾아야 한다
-   새로운 함수형 도구를 찾거나 다른 언어에서 영감을 받을 수 있다
-   언어에 맞는 방법을 찾아 함수형 도구를 사용해야 한다
