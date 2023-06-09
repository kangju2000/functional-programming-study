# Chapter 9 : 계층형 설계 2

> 계층형 설계 패턴은 4가지가 있다

1. 직접 구현
2. 추상화 벽
3. 작은 인터페이스
4. 편리한 계층

<br/>

> 패턴 2: 추상화 벽 abstract barrier

- 팀 간 책임을 명확하게 나눈다
- 세부 구현을 감춘 함수로 이루어진 계층이다 - 추상화 벽에 있는 함수를 사용할 때는 구현을 몰라도 사용할 수 있다
- 추상화 벽은 흔하게 사용하는 라이브러리나 API 와 비슷하다
- 추상화 벽으로 벽 위에 있는 코드와 아래 있는 코드의 의존성을 없앨 수 있다

```
추상화 벽은 언제 사용하면 좋을까

1. 쉽게 구현을 바꾸기 위해
    - 구현에 대한 확신이 없는 경우
    - 프로토타이핑과 같이 최선의 구현을 확신할 수 없는 작업의 경우
    - 임시 데이터를 줘야하는 경우와 같이 뭔가 바뀔 것을 알고 있지만 아직 준비되지 않은 경우

2. 코드를 읽고 쓰기 쉽게 만들기 위해
    - 세부적인 것을 신경 쓰지 않아도 된다

3. 팀 간에 조율해야 할 것을 줄이기 위해
    - 각 팀에 관한 구체적인 내용을 서로 신경 쓰지 않아도 일할 수 있어 더 빠르게 일할 수 있다

4. 주어진 문제에 집중하기 위해
    - 해결하려는 문제의 구체적인 부분을 무시할 수 있다 그렇기 때문에 코드에 실수를 줄이고, 만들면서 지치지 않을 수 있다
```

<br/>

> 패턴 3: 작은 인터페이스 minimal interface

- 새로운 코드를 추가할 위치에 관한 것이다
- 인터페이스를 최소화하면 하위 계층에 불필요한 기능이 쓸데없이 커지는 것을 막을 수 있다
- 새로운 기능을 만들 때 하위 계층에 기능을 추가하거나 고치는 것보다 상위 계층에 만드는 것이 작은 인터페이스 패턴이라고 할 수 있다

```
추상화 벽을 작게 만들어야 하는 이유
> 추상화 벽에 코드가 많을수록 구현이 변경되었을 때 고쳐야 할 것이 많다
> 추상화 벽에 있는 코드는 낮은 수준의 코드이기 때문에 더 많은 버그가 있을 수 있다
> 낮은 수준의 코드는 이해하기 더 어렵다
> 추상화 벽에 코드가 많을수록 팀 간 조율해야 할 것도 많아진다
> 추싱화 벽에 인터페이스가 많으면 알아야 할 것이 많아 사용하기 어렵다
```

<br/>

> 패턴 4: 편리한 계층 comfortable layer

- 언제 패턴을 적용하고 또 언제 멈춰야 하는지 실용적인 방법을 알려준다

<br/>

> 그래프로 알 수 있는 코드에 대한 정보

```
> 기능적 요구사항 (functional requirements) 은 소프트웨어가 정확히 해야 할 일을 말한다
> 비기능적 요구사항 (nonfunctional requirements, NFRs) 은 테스트를 어떻게 할 것인지, 재사용을 잘할 수 있는지, 유지보수하기 어렵지 않은지와 같은 요구사항들이다
비기능적 요구사항은 소프트웨어 설계를 하는 중요한 이유이다
```

  <br/>

> 호출 그래프로 알 수 있는 세 가지 비기능적 요구사항

1. 유지보수성 (maintainability) : 요구 사항이 바뀌었을 때 가장 쉽게 고칠 수 있는 코드는 어떤 코드인가요?
2. 테스트성 (testability) : 어떤 것을 테스트하는 것이 가장 중요한가요?
3. 재사용성 (reusability) : 어떤 함수가 재사용하기 좋나요?

<br/>

> 그래프의 가장 위에 있는 코드가 고치기 쉽다

- 코드를 적절한 위치에 두면 유지보수 비용을 많이 줄일 수 있다
- 함수는 그래프 위에서 멀어질수록 더 고치지 어렵다
- 자주 바뀌는 코드는 그래프 위에 있을수록 쉽게 일할 수 있다 하지만 바뀌는 것이 많은 가장 높은 곳은 적게 유지하는 것이 좋다

<br/>

> 아래에 있는 코드는 테스트가 중요하다

- 하위 계층으로 코드를 추출하거나 상위 계층에 함수를 만드는 일은 테스트의 가치를 결정한다

  <br/>

> 아래에 있는 코드가 재사용하기 더 좋다

- 아래쪽으로 가리키는 화살표가 많은 함수는 재사용하기 어렵다
