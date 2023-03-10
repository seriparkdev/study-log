# 목차

- 기술 문서를 읽을 때
- 인강 효과적으로 듣기
- 프론트엔드에서의 상태관리

## 기술 문서를 읽을 때

- 목차, 소제목, 핵심 요약을 먼저 들여다보고 큰 흐름을 잡은 다음에 읽기 시작하자

- 실제 경험과 연관시키며 읽자. 비교하고, 대조해보면서 능동적으로 읽자.

- 어떤 단어가 사용 됐을 때의 맥락에 대해 잘 기억해두자 (기술 문서의 단어들은 토익, 수능과는 다른 맥락과 의미를 가진다)

- 끊어 읽으면서 문장에 의미를 붙여보자

## 인강 효과적으로 듣기

- 시뮬레이션 하기

목차를 보면서 시뮬레이션을 해보자. 강의 흐름이 어떤지 훑어보면서 궁금증을 가지자. 검색도 한번 해보자.

- 강사분과 생각 비교

내 생각과 강사분의 생각을 적극적으로 비교하자!

- 과거의 경험에 적극적으로 대입해보기

배운 내용을 과거의 경험에 최대한 적용시켜보자. 예전에는 내가 이렇게 했었는데, 지금 배운 내용을 적용해보면 어떻게 될까?

> 아는 게 아니라 사용하기 위해 인강을 듣자!

> 사용하지 않으면 기억에서 사라진다.

## 프론트엔드에서의 상태관리

데이터가 변할 때마다 관련 DOM을 직접 찾아 조작하지 않고 싶다면, 데이터를 한 곳에서 효율적으로 관리하고 싶다면 상태관리에 대해 알아야 한다

- 상태란? 데이터
- 상태가 예측한 값으로 변해야 의도대로 동작한다

어떻게 예측가능하게 만들까?

- 예측 범위를 최소화 해야 한다
- 상태에 대해 일관적으로 READ하는 로직 만들기
- Write는 최소화하는 로직 만들기
  - 상태를 여러 곳에서 수정하면 예측하기 어려워지니 수정하는 부분을 제한하자. 수정을 담당하는 곳에서 분명하게 역할을 가진다면 write는 최소화 할 수 있다.

부모 컴포넌트에서 데이터를 수정하는 메서드를 관리하면 자식 컴포넌트는 그 메서드를 사용하도록 만든다. 이렇게 하면 데이터를 한 곳에서 효율적으로 관리할 수 있다.

> 정리

- 프론트엔드에서 상태관리는 한 곳에서 하는 게 효율적이다.
- 보통은 최상위 컴포넌트나 storage를 따로 두어 관리한다.
- 자식 컴포넌트들은 최상위 컴포넌트에서 상태를 받아 렌더링하는 역할을 수행한다
