## JSX란 무엇인가?

JSX란 자바스크립트 파일 내에서 HTML을 작성할 수 있도록 자바스크립트를 확장한 문법

## 마운트란?

리액트 컴포넌트가 생성되고 DOM에 삽입되어 브라우저에 나타나는 것을 의미

## 언마운트란?

언마운트는 컴포넌트가 DOM에서 사라지는 것을 의미

## virtual DOM

DOM이나 CSSOM이 수정될 때마다 CRP 과정을 반복하는데 이는 성능의 저하를 일으킬 수 있음. 그래서 리액트는 VritualDOM을 도입해 변화(UI에)가 생겼을 때마다 DOM 조작을 매번하는 것이 아니라, 이전 VirtualDOM과 새로운 virtualDOM을 비교해서 실제로 변경된 부분만 DOM에 적용한다.

> VirtualDOM이란 리액트가 관리하는 DOM과 유사한 객체이다.

## 제어 컴포넌트 / 비제어 컴포넌트

- 제어 컴포넌트(controlled component)
  React에 의해 값이 제어되는 입력 폼 요소를 말함. `setState`에 의해서만 업데이트 되며 입력할 때마다 리렌더링이 발생한다.
- 비제어 컴포넌트(uncontrolled component)
  폼의 값들을 얻을 때 `ref`를 사용하는 것을 말한다. input의 입력 값이 변경되어도 리렌더링 되지 않음.

> form submit 할 때 ref에 등록된 값을 읽어오는 방법

## 리액트의 라이프사이클

리액트의 라이프사이클은 컴포넌트의 생명주기를 의미한다. 컴포넌트의 생명주기는 다음 3가지로 구분할 수 있다.

- Mounting

컴포넌트의 인스턴스가 만들어지고 DOM에 삽입될 때 다음 순서대로 메서드가 실행된다.

1. `constructor()`
2. `static getDerivedStateFromProps()`(잘 사용되지 않음)
3. `render()`
4. `componentDidMount()`
   : 컴포넌트가 마운트된 직후 호출된다. 주로 네트워크 요청을 한다.

- Updating

props나 state에 의해 업데이트가 일어난다. 컴포넌트가 리렌더링될 때 메서드가 사용된다.

1. `static getDerivedStateFromProps()` (잘 사용되지 않음)
2. `shouldComponentUpdate()` (잘 사용되지 않음)
3. `render()`
4. `getSnapshotBeforeUpdate()` (잘 사용되지 않음)
5. `componentDidUpdate()`
   : 업데이트가 발생한 직후에 호출된다. 주로 DOM을 업데이트하거나 사이드 이펙트를 처리한다.

- Unmounting

아래의 메서드는 컴포넌트가 DOM에서 제거될 때 사용된다

1. `componentWillUnmount()`
   : 컴포넌트가 언마운트되고 소멸되기 직전에 호출된다. 타이머나 비동기 API를 제거한다.

## 리렌더링의 조건

- props나 state의 변경

## useEffect와 라이프사이클

useEffect는 `componentDidMount`, `componentDidUpdate()`, `componentWillUnmount()`의 합이다. 함수형 컴포넌트에서는 useEffect를 이용해서 라이프 사이클을 관리할 수 있다.

## props와 state의 차이

- props : 부모 컴포넌트가 자식 컴포넌트에게 전달하는 데이터
  모든 react component는 props와 관련하여 순수 함수처럼 작동해야 한다.
- state : 컴포넌트의 내부 상태를 나타내는 데이터
