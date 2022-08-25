# 핸즈온 스니펫

## 1. 웹사이트 움직이게 만들기

01-vanilla-js.html

## 2. 리액트 맛보기

02-react-tasting.html

### 2-1: catItem 엘리먼트 만들기

`console.log("야옹");` 이 있던 곳에 붙여넣어주세요.

```js
const catItem = (
  <li>
    <img src="https://cataas.com/cat/60b73094e04e18001194a309/says/react" />
  </li>
);
```

### 2-2: ReactDOM.render로 html에 엘리먼트 추가하기

1. body에 있는 고양이 관련 html 코드를 모두 주석처리 해주세요
2. body 여는 태그 밑에 엘리먼트를 박아넣을 공간을 마련해주세요

```js
<div id="app"></div>
```

3. 아까 만들었던 catItem을 html의 빈 공간에 ReactDOM.render를 써서 그려주세요

```js
const 여기다가그려 = document.querySelector("#app");

ReactDOM.render(catItem, 여기다가그려);
```

4. 'Live server'를 사용해 브라우저에서 열고, 개발자 도구에서 스크립트 `에러`가 나는걸 확인해주세요.

### 2-3: 리액트 스크립트 추가

https://ko.reactjs.org/docs/add-react-to-a-website.html

1. 리액트 라이브러리와 바벨 script를 고양이코드 script 위에 넣어주세요

```html
<script
  src="https://unpkg.com/react@17/umd/react.development.js"
  crossorigin
></script>
<script
  src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"
  crossorigin
></script>
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

2. 고양이코드 script에 type을 넣어주세요

```html
<script type="text/babel">
  // 고양이코드
</script>
```

## 4. JSX로 HTML 과 JS 짬뽕하기

### 4-1: js에 favorites변수 만들어서 html에서 오려오기

```jsx
const favorites = (
  <ul class="favorites">
    <li>
      <img src="https://cataas.com/cat/60b73094e04e18001194a309/says/react" />
    </li>
    <li>
      <img src="https://cataas.com/cat/60b73094e04e18001194a309/says/react" />
    </li>
    <li>
      <img src="https://cataas.com/cat/60b73094e04e18001194a309/says/react" />
    </li>
  </ul>
);
```

### 4-2: ReactDOM.render에 catItem대신 favorites 그려보기

```jsx
ReactDOM.render(favorites, 여기다가그려);
```

### 4-3: 중괄호{}를 사용해서 catItem을 favorites에 그려보기

```jsx
const favorites = (
  <ul class="favorites">
    {catItem}
    {catItem}
    {catItem}
  </ul>
);
```

### 4-4: mainCard 변수 만들어서 html에서 오려오기

```jsx
const mainCard = (
  <div class="main-card">
    <img
      src="https://cataas.com/cat/60b73094e04e18001194a309/says/react"
      alt="고양이"
      width="400"
    />
    <button>🤍</button>
  </div>
);
```

### 4-5: app 변수 만들어서 mainCard, favorites 리액트에 모두 그리기

```jsx
const app = (
  <div>
    {mainCard}
    {favorites}
  </div>
);
```

### 4-6: h1태그, form태그도 모두 리액트에 그리기

```jsx
const title = <h1>1번째 고양이 가라사대2</h1>;

const form = (
  <form>
    <input type="text" name="name" placeholder="영어 대사를 입력해주세요" />
    <button type="submit">생성</button>
  </form>
);
```

```jsx
const app = (
  <div>
    {title}
    {form}
    {mainCard}
    {favorites}
  </div>
);
```

## 6. 컴포넌트 만들기

### 6-1: CatItem을 함수 형태의 컴포넌트로 바꿔보기

```jsx
function CatItem(props) {
  return (
    <li>
      <img src={props.img} />
    </li>
  );
}
```

### 6-2: favorites에서 <CatItem /> 태그 형태로 써보기

### 6-3: 두 개의 CatItem에 img prop을 다르게 넘겨보기

utils.js의 CAT1, CAT2 복붙

```jsx
function Favorites() {
  return (
    <ul class="favorites">
      <CatItem img="https://cataas.com//cat/5e9970351b7a400011744233/says/inflearn" />
      <CatItem img="https://cataas.com/cat/595f280b557291a9750ebf65/says/JavaScript" />
    </ul>
  );
}
```

### 6-4: 나머지 element를 모두 함수 형태의 컴포넌트로 바꿔보기

examples/06-making-component.html 을 참고해주세요

### 6-5 Title의 내용을 children prop으로 받아오기

```jsx
const Title = (props) => {
  return <h1>{props.children}</h1>;
};
```

## 7. 스타일링

### 7-1: class대신 className으로 찾아바꿔주세요

07-styling.html 참고해주세요

### 7-2: 인라인 스타일: favorites img 150px css 없애고 CatItem에 style prop으로 넣기

```jsx
function CatItem(props) {
  return (
    <li>
      <img src={props.img} style={{ width: "150px" }} />
    </li>
  );
}
```

## 8. 이벤트 다루기

### 8-1: MainCard 내에 handleHeartClick 함수 만들고 onClick에 연결해줘서 하트 눌렀을 때 console.log찍기

```jsx
const MainCard = ({ img }) => {
  function handleHeartClick() {
    console.log("하트 눌렀음");
  }
  function handleHeartMouseOver() {
    console.log("하트 스쳐 지나감");
  }
  return (
    <div className="main-card">
      <img src={img} alt="고양이" width="400" />
      <button onClick={handleHeartClick} onMouseOver={handleHeartMouseOver}>
        🤍
      </button>
    </div>
  );
};
```

### 8-2: Form에 handleFormSubmit 함수를 만들고 form의 onSubmit prop에 연결해주기

```jsx
const Form = () => {
  function handleFormSubmit(event) {
    // 브라우저 리프레시 막기 event.preventDefault()
    event.preventDefault();
    console.log("폼 전송됨");
  }

  return (
    <form onSubmit={handleFormSubmit}>
      <input type="text" name="name" placeholder="영어 대사를 입력해주세요" />
      <button type="submit">생성</button>
    </form>
  );
};
```

## 9. useState으로 상태 만들기

### 9-1: React.useState로 counterState 만들기

```jsx
const [counter, setCounter] = React.useState(1);
```

### 9-2: 폼이 전송될때마다 setCounter로 counter + 1 씩 해주기

```jsx
console.log("카운터", counter);

function handleFormSubmit(event) {
  event.preventDefault();
  console.log("폼 전송됨");
  setCounter(counter + 1);
}
```

## 10. 상태 끌어올리기

### 10-1: app에 상태를 넣기 위해 컴포넌트로 바꾸기

- Form, Title 을 모두 참조할 수 있는 공간(app)으로 상태를 끌어올리기!
- Title에 1 대신 counter를 넣기
- handleFormSubmit도 App으로 끌어올리기

```jsx
const App = () => {
  const [counter, setCounter] = React.useState(1);

  console.log("카운터", counter);

  function handleFormSubmit(event) {
    event.preventDefault();
    console.log("폼 전송됨");
    setCounter(counter + 1);
  }

  return (
    <div>
      <Title>{counter}번째 고양이 가라사대</Title>
      <Form handleFormSubmit={handleFormSubmit} />
      <MainCard img="https://cataas.com/cat/60b73094e04e18001194a309/says/react" />
      <Favorites />
    </div>
  );
};
```

### 10-2: app에 상태를 넣기 위해 컴포넌트로 바꾸기

```jsx
const App = () => {
  const CAT1 = "https://cataas.com/cat/60b73094e04e18001194a309/says/react";
  const CAT2 = "https://cataas.com//cat/5e9970351b7a400011744233/says/inflearn";
  const CAT3 =
    "https://cataas.com/cat/595f280b557291a9750ebf65/says/JavaScript";

  const [counter, setCounter] = React.useState(1);
  const [mainCat, setMainCat] = React.useState(CAT1);

  console.log("카운터", counter);

  function handleFormSubmit(event) {
    event.preventDefault();
    console.log("폼 전송됨");
    setCounter(counter + 1);
    setMainCat(CAT2);
  }

  return (
    <div>
      <Title>{counter}번째 고양이 가라사대</Title>
      <Form handleFormSubmit={handleFormSubmit} />
      <MainCard img={mainCat} />
      <Favorites />
    </div>
  );
};
```

## 11. 리스트

### 11-1

```jsx
function Favorites() {
  const CAT1 = "https://cataas.com/cat/60b73094e04e18001194a309/says/react";
  const CAT2 = "https://cataas.com//cat/5e9970351b7a400011744233/says/inflearn";
  const CAT3 =
    "https://cataas.com/cat/595f280b557291a9750ebf65/says/JavaScript";

  const cats = [CAT1, CAT2];

  return (
    <ul className="favorites">
      {cats.map((cat) => (
        <CatItem img={cat} key={cat} />
      ))}
    </ul>
  );
}
```

## 12. 배웠던 개념 조합해서 기능 추가(상태, prop, 이벤트, 리스트)

### 12-1: handleHeartClick을 App으로 끌어올리기

```jsx
const App = () => {
  // ...
  function handleHeartClick() {
    console.log("하트 눌렀음");
  }

  //...
  return (
    <div>
      // ...
      <MainCard img={mainCat} handleHeartClick={handleHeartClick} />
    </div>
  );
};
```

### 12-2: 하트를 누르면 리스트에 고양이 추가하기

- 고양이 좋아요 리스트를 App에 favorites로 상태를 만들어 추가하기 ([cat1, cat2]를 초기값으로)
- 하트를 누르면 cat3를 배열에 추가

```jsx
const App = () => {
  const CAT1 = "https://cataas.com/cat/60b73094e04e18001194a309/says/react";
  const CAT2 = "https://cataas.com//cat/5e9970351b7a400011744233/says/inflearn";
  const CAT3 =
    "https://cataas.com/cat/595f280b557291a9750ebf65/says/JavaScript";

  const [counter, setCounter] = React.useState(1);
  const [mainCat, setMainCat] = React.useState(CAT1);
  const [favorites, setFavorites] = React.useState([CAT1, CAT2]);

  console.log("카운터", counter);

  // ...

  function handleHeartClick() {
    console.log("하트 눌렀음");
    setFavorites([...favorites, CAT3]);
  }

  return (
    <div>
      // ...
      <MainCard img={mainCat} handleHeartClick={handleHeartClick} />
      <Favorites favorites={favorites} />
    </div>
  );
};
```

## 13. 폼 다루기

### 13-1: Form 컴포넌트에 value state 추가하기

```jsx
const Form = ({ handleFormSubmit }) => {
  const [value, setValue] = React.useState("");
  // ...
};
```

### 13-2: input이 onChange될 때마다 대문자로 바꿔서 value에 넣어주기

```jsx
const Form = ({ handleFormSubmit }) => {
  const [value, setValue] = React.useState("");

  function handleInputChange(e) {
    setValue(e.target.value.toUpperCase());
  }

  return (
    <form onSubmit={handleFormSubmit}>
      <input
        type="text"
        name="name"
        placeholder="영어 대사를 입력해주세요"
        value={value}
        onChange={handleInputChange}
      />
      <button type="submit">생성</button>
    </form>
  );
};
```

## 14. 폼 검증하기

- 한글은 못 적도록
  - utils.js의 includesHangul 함수 복붙 후 Form에 넣기

```jsx
const Form = () => {
  const includesHangul = (text) => /[ㄱ-ㅎ|ㅏ-ㅣ|가-힣]/i.test(text);
```

- 에러메세지 state 추가하기

```jsx
const Form = () => {
  // ...
  const [errorMessage, setErrorMessage] = React.useState("");
```

한글이 들어오면 에러메세지 보여주기
에러메세지를 input 밑에 넣어주기 (빨간색으로)
한글이 없다면 에러메세지 초기화

```jsx
const Form = () => {
  const includesHangul = (text) => /[ㄱ-ㅎ|ㅏ-ㅣ|가-힣]/i.test(text);
  const [value, setValue] = React.useState("");
  const [errorMessage, setErrorMessage] = React.useState("");

  function handleInputChange(e) {
    const userValue = e.target.value;
    setErrorMessage("");
    if (includesHangul(userValue)) {
      setErrorMessage("한글은 입력할 수 없습니다.");
    }
    setValue(userValue.toUpperCase());
  }

  // ...

  return (
    <form onSubmit={handleFormSubmit}>
      <input
        type="text"
        name="name"
        placeholder="영어 대사를 입력해주세요"
        value={value}
        onChange={handleInputChange}
      />
      <button type="submit">생성</button>
      <p style={{ color: "red" }}>{errorMessage}</p>
    </form>
  );
};
```

빈값을 전송하려고 하면 에러메세지 추가

```jsx
const Form = () => {
  // ...
  function handleFormSubmit(e) {
    e.preventDefault();
    setErrorMessage("");

    if (value === "") {
      setErrorMessage("빈 값으로 만들 수 없습니다.");
    }
  }

  // ...
};
```

## 15. 로컬스토리지에 데이터 싱크하기

```jsx
const App = () => {
  // ...

  const [counter, setCounter] = React.useState(
    Number(localStorage.getItem("counter"))
  );
  // ...

  function updateMainCat() {
    setMainCat(CAT2);
    const nextCounter = counter + 1;
    setCounter(nextCounter);
    localStorage.setItem("counter", nextCounter);
  }

  //...
};
```

## 16. GitHub Pages로 배포하기

혹시 Git이 처음이라면?
```
Git 명령어
이름 설정 : git config –global user.name 이름
이메일 설정: git config –global user.email 이메일
```

포크한 저장소에 코드 올리기
```
git add .
git commit -m "initial commit"
git push -u origin main

```

- settings > github pages > source를 none이 아닌 main으로 바꾼다

## 기타

- 50프로 할인 쿠폰: https://forms.gle/Y7rTP4qKw89NStkP7
