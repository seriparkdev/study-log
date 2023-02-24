# node.js

브라우저 밖에서도 자바스크립트를 실행할 수 있는 환경

# NPM(Node Package Manager)

자바스크립트 라이브러리를 설치하고 관리할 수 있는 패키지 매니저

=> `npm init`: package.json 생성

CDN 방식으로 라이브러리를 HTML 중간에 삽입하는 방식은 버전 관리, 라이브러리 의존성 관리가 어렵습니다. 태그를 매번 찾아야 하는 번거로움도 있는데 이를 해결해주는 것이 NPM입니다.

# AMD & Common.js

- Common.js : (require, module exports)
- AMD: 비동기 모듈에 대한 표준안. 모듈이 로딩될 때까지 기다리지 않는 비동기 모듈 방식. (define, require)

전역적으로 범위를 갖는 자바스크립트의 특성상 어느 위치에서든지 어떤 변수를 참조할 수 있다면 위험성이 커질 것이다. 이를 위해 이러한 모듈화가 필요한 것.

# ES6 Modules

자바스크립트 코드를 모듈화(다른 파일에 있는 자바스크립트 기능을 특정 파일에서 사용) 가능

- `import` : export 된 변수나 함수를 가져올 수 있음
- `export` : 다른 파일에서 가져다 쓸 함수, 변수에 사용

# WAI-ARIA

## role

어떠한 role은 특정 키보드 인터랙션을 가지기 때문에 role에 기대되는 키보드 인터렉션이 존재한다면 구현해야 한다(JavaScript).

> `role="button"`이라면 스페이스키, 엔터키로 활성화시킬 수 있어야 함.

**role을 적용했다면 해당하는 키보드 인터랙션이 있는지 확인하자.**

## ARIA를 조심해서 쓰자

```javascript
// 보조 기술 사용자는 이 엘리먼트를 메뉴의 항목으로 인지
<a role="menuitem">😂</a>
// 보조 기술 사용자는 이 링크를 MUSIC이 아닌 aria-label의 글자로만 인식한다.
<a aria-label="보조 기술 사용자는 링크 텍스트가 아니라 이 aria-label의 콘텐트만을 인식할 수 있습니다">MUSIC</a>
```

## 랜드마크를 잘 설계하기

한 페이지에 랜드마크 role이 두 번 이상 사용된다면 각 랜드마크에는 고유한 레이블을 지정해줘야 식별이 쉬워진다.

영역이 헤딩 엘리먼트로 시작 -> `aria-labelledby`

영역에 레이블 필요, 헤딩 엘리먼트 없음 -> `aria-label`

## 접근 가능

- 레이블: 사용자에게 직접 가시적으로 표현된 식별자
- 접근 가능한 이름: 소프트웨어(스크린리더)를 통해 사용자에게 레이블의 정보를 전달해주는 것
- 접근 가능한 설명: 비밀번호 경고문 같은 것(8자 이상으로 입력해주세요.)

### 스크린리더

낭독 순서: 엘리먼트의 이름 -> 역할 -> 상태 -> (설명)

- 엘리먼트의 이름 : 대화 음소거
- 역할 : 버톤
- 상태 : 꺼짐
- 설명: 대화에 대한 경고와 알림 소리를 없앱니다.

=> 대화 음소거 버튼 꺼짐 대화에 대한 경고와 알림 소리를 없앱니다

### 접근 가능한 이름

- 가시적으로 보이는 텍스트를 접근 가능한 이름으로 사용하라
- 접근 가능한 이름을 지정하지 않을 시 브라우저는 자동 생성으로 fallback을 시도함. 품질 낮은 이름 적용.
- 간단하고 유용한 이름 설정

**📌 방법**

1. 자식 콘텐츠로 이름 지정

다음과 같은 역할을 가지는 엘리먼트는 컨텐츠로부터 접근 가능한 이름을 가져온다.

`button
cell
checkbox
columnheader
gridcell
heading
link
menuitem 
menuitemcheckbox
menuitemradio
option
radio
row
rowheader
switch
tab
tooltip
treeitem`

```html
<a href="/">컨텐츠</a>
```

2. aria-lable

시각적으로 노출된 컨텐츠가 없을 경우 사용할 수 있는 방법. 이름을 강제하여 지정해줄 수 있다. (자식 콘텐츠로부터 이름이 지정되는 역할을 가지는 요소만)

```html
<button type="button" aria-label="Close">X</button>
```

> 랜드마크를 가지는 요소에도 aria-lable을 지정할 수 있다! 랜드마크의 이름이 aria-lable로 지정된다.

[📗 이름 지정 지침](https://mulder21c.github.io/aria-practices/#names_and_descriptions)

3. aria-lablelledby
   A라는 요소에 B 요소의 id 값을 aria-labelledby 값으로 사용하면 A 요소의 접근 가능한 이름은 B 요소의 컨텐츠가 된다

```html
<span id="night-mode-label">야간 모드</span>
<span
  role="switch"
  aria-checked="false"
  tabindex="0"
  aria-labelledby="night-mode-label"
></span>
```

=> switch role을 가진 요소는 내부 컨텐츠가 없기 때문에 접근 가능한 이름이 없어야 하지만 aria-labelledby가 첫 번째 span요소를 참조하기 때문에 야간 모드가 접근 가능한 이름이 된다

- 접근 가능한 이름 계산에서 가장 높은 우선 순위를 가짐
- 여러 요소 참조 가능

```html
<h2 id="bees-heading">벌을 구할 수 있는 7가지 방법</h2>
<p>벌이 빠르게 사라지고 있습니다. 여기 당신이 도울 수 있는 7가지가 있습니다.</p>
<p>
  <a id="bees-read-more" aria-labelledby="bees-read-more bees-heading"
    >더 보기...</a
  >
</p>
```

- 숨겨진 텍스트도 참조 됨
- textfield. input(type="text")요소의 값도 참조 됨

4.  label 엘리먼트로 폼 컨트롤 이름 지정
5.  legend 엘리먼트로 필드셋 이름 지정
6.  캡션으로 표 및 삽화 이름 지정

: table 엘리먼트가 aria-label나 aria-labelledby를 가지지 않은 경우, caption을 접근 가능한 이름으로 사용 / table이 aria-label나 aria-labelledby를 사용하여 이름이 지정되고, caption 엘리먼트가 있다면 이는 접근 가능한 설명으로 사용
