<h1 align="center"><img width="355" alt="icon_logo" src="https://github.com/Dev-One-Project/ONF-client/assets/91879417/b2157ac3-86b1-4b89-b595-706fac0cd183"></h1>
<div>
<img width="50%" alt="스크린샷 2023-01-17 오후 4 58 17" src="https://github.com/Dev-One-Project/ONF-client/assets/91879417/7133f982-1a79-4a34-b105-bbcd47509e9d"><img width="50%" alt="img_on off" src="https://github.com/Dev-One-Project/ONF-client/assets/91879417/e09b189a-081d-47ea-acfe-755192af5296">
</div>

## 📖 소개

웹 기반 출퇴근 기록 서비스.  
대부분 앱으로 만들어진 출퇴근 서비스를 웹 기반으로 재구성했다. HTML5에서 등장한 geolocation, 곳곳에서 사용하는 공통 컴포넌트, 전역 상태 관리를 위한 Recoil, 프로젝트 시 프론트엔드와 백엔드 일정 우선순위 조율 등 다양한 기능과 협업에 익숙해지고자 시작한 사이드프로젝트.

</br>

## 🛠️ 기술

Stack  
[![My Skills](https://skillicons.dev/icons?i=html,css,js,ts,react,nextjs,emotion,apollo,git)](https://skillicons.dev)

Deploy  
[![My Skills](https://skillicons.dev/icons?i=gcp,docker)](https://skillicons.dev)

Communication  
[![My Skills](https://skillicons.dev/icons?i=github,discord)](https://skillicons.dev)

## 🗓️ 기간

- 전체 : 2022년 11월 28일 ~ (진행중)
  - 1차 기능 : 2022년 11월 28일 ~ 2023년 1월 20일
  - 2차 기능 : 2023년 1월 21일 ~ (진행중)

</br>

## 👥 프론트엔드 구성원

김민겸, 신미연, 이다은, 이상현, 이정우, 홍민우

</br>

## 😎 기여 사항

### 관리자 페이지

#### 관리 탭(퍼블리싱, 기능)

<img width="100%" alt="스크린샷gif" src="https://github.com/Dev-One-Project/ONF-client/assets/91879417/ead6aee7-2eff-4fca-89ca-cc13b6d63b0a">

<br>

관리자 페이지의 관리 탭 내부 `모든 탭들의 UI를 구현`하고 `API를 연결`했습니다.

각 탭들에 중복 사용되는 부분(`테이블`, `항목 추가하기 버튼` 등)이 많아서 `하나의 컴포넌트로 사용`하되, `선택된 탭을 식별할 수 있는 변수를 props`로 내려주어 내부 콘텐츠를 변경하는 식으로 설계했습니다.

#### 프로필 탭(퍼블리싱)

<img width="1680" alt="스크린샷gif" src="https://github.com/Dev-One-Project/ONF-client/assets/91879417/ec005b96-77f2-4c70-989a-ce122e6635c1">

<br>

관리자의 프로필을 보여주는 탭이며, API 연결은 되어있지 않고 퍼블리싱만 진행된 상태입니다.

#### 공통 컴포넌트

- **Toggle Button + Select Box**
  <img width="100%" alt="스크린샷gif" src="https://github.com/Dev-One-Project/ONF-client/assets/91879417/ca1521e7-e93a-4dff-8007-a0b5e24c12da">
  <br>

  직접 제작한 `Custom Select Box + Toggle Button` 컴포넌트 입니다. 선택 항목으로 들어갈 데이터를 배열로 넣어주면 위와 같이 항목들이 생성됩니다.

  프로젝트 전반에 결쳐 사용되는 곳이 많았기에, 다양한 기능들을 구현했습니다.

  - `단일 선택 모드`
  - `복수 선택 모드`
  - `모두 선택`(복수 선택 모드에서)
  - `항목 검색`
  - `left, center, right 정렬`(토글 버튼 기준)
  - `항목 defaultChecked`
  - 선택된 항목 `갯수로 표시`
  - 선택된 항목 `이름으로 표시`

<br>

- **Animated Modal**
  <img width="100%" alt="스크린샷gif" src="https://github.com/Dev-One-Project/ONF-client/assets/91879417/5238af8c-45bc-4a89-89ed-9970d17f9c3a">
  <br>
  프로젝트의 모티브인 Shiftee의 Modal UI와 비슷한 애니메이션 효과를 가진 커스텀 모달 입니다.

  `onAnimationEnd` 속성과 `react state` 그리고 `emotion`을 적절히 조합하여 애니메이션을 구현했습니다.

  `JSX.Element` 또는 `ReactNode`를 `props.children`으로 받게 설계하여 사용성을 높였습니다.

</br>

## 💻 프로젝트 실행 방법

```
git clone https://github.com/Dev-One-Project/ONF-client.git

yarn install

yarn start
```

</br>

## 🤔 어려웠던 것

Shiftee의 모달과 같이 모달의 `mount`/`unMount` 애니메이션을 커스텀 모달에 적용하기 위해 모달의 열림/닫힘 상태를

```ts
const [isOpen, setIsOpen] = React.useState(boolean);
```

로 생성하여 관리하고 있었습니다.

<img src="https://github.com/Dev-One-Project/ONF-client/assets/91879417/3446a627-91ec-4580-8628-bb6b40921981">
(위는 Shiftee의 모달 on/off 애니메이션입니다.)

<br>

여기서 문제가 하나 발생합니다. `unMount` 애니메이션은 `mount` 애니메이션과 달리 스타일을 적용한다고 바로 적용되지 않는 것이었습니다.
컴포넌트가 `mount`될 때 화면에 렌더링 되는 과정에서 스타일이 입혀지면서 `mount` 애니메이션이 자연스럽게 적용되지만, 컴포넌트가 `unMount`되면 스타일이 입혀지기 전에 이미 컴포넌트는 사라지고 없기 때문입니다.

<!-- 이걸 어떻게 해결해야할지 고민을 하다 처음으로 떠올린 것은 `animation`을 트리거할 상태를 따로 선언하고 모달을 닫는 함수에 `unMount-animation`트리거와 `setTimeout + setMountState(false)`트리거를 넣는 방법이었습니다. 닫기 이벤트에서 `setTimeout`의 `delay`와 `unMount-animation-duration`을 맞춰서 진행시키는 이 방법은 `닫기 버튼 클릭`, `바깥 클릭`, `X 클릭`에서는 자연스럽게 작동을 했지만, 입력 양식을 채워서 서버에 요청을 보낸 후에 모달을 닫게 하는 `추가하기 버튼 클릭`에서 http통신이 끝난 후 모달을 닫는 함수가 실행되고 `setTimeout`의 `delay`만큼 추가적인 지연 시간이 생기게 되었습니다. -->

유저가 모달을 닫는 액션을 취하면 `setIsOpen(false)`로 컴포넌트를 바로 `unMount` 시키는 것 대신에, `mount`/`unMount`애니메이션 상태를 위한 `state(aniMode)`를 하나 더 생성해서 유저가 모달을 닫으면 `unMount` 애니메이션을 `setAnimode`로 작동하게 만들었고 `onAnimationEnd`에서 모달이 열고 닫히는 애니메이션의 상태(boolean)를 나타내는 `aniMode`를 식별하여 닫히는 애니메이션인가? 라는 조건을 통과하면 그 때 `setIsOpen(false)`로 컴포넌트를 `unMount`시키는 것으로 해결했습니다.

코드 동작 흐름

모달 열기 함수 실행 > setAniMode(true), setIsOpen(true) > 컴포넌트 `component mount`, 열리는 애니메이션 실행 > onAnimationEnd 실행 > aniMode가 false인가? `No`

모달 닫기 함수 실행 > setAniMode(false) > 닫히는 애니메이션 실행 > onAnimationEnd 실행 > aniMode가 false인가? `Yes` > setIsOpen(false) 모달 닫기 > `component unMount`
