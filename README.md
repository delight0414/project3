## 🚩Project - C.P. Company

#### 📰 Intro 
React로 개발한 개인프로젝트입니다. GSAP Library를 사용해서 Parallax 웹사이트를 구현하였습니다. 
Styled-components로 일관된 스타일링을 하였고 Github로 웹호스팅하였습니다.
##
#### 👩‍💻 Stack 
<div>
  <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=white">
  <img src="https://img.shields.io/badge/Redux-764ABC?style=for-the-badge&logo=redux&logoColor=white">
  <img src="https://img.shields.io/badge/Javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=white">
  <img src="https://img.shields.io/badge/Styled components-DB7093?style=for-the-badge&logo=styledcomponents&logoColor=white">
  <img src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white">
</div>

##
#### 💻 Code review
🔸 styled components를 쓴 탓에 className으로 DOM을 참조하기 쉽지않아서 useState를 사용하기로 했다
```javascript
const [isOpen, setIsOpen]=useState(false);

const handleClick = () => {
  setIsOpen(!isOpen);
  gsap.to(".header", { height: isOpen ? "auto" : "250px", duration: 0.3 });
};

return(
    <>
      <HeaderBox className="header">
        <Inner>
          <Tab id="tab" className={isOpen ? "close" : ""} onClick={handleClick}>
            <span></span>
          </Tab>
            .
            .
            .
  );
```


🔸 styled components를 쓰려면 GlobalStyle이라는 전역 스타일을 설정해야한다. (+styled-reset)
```javascript
//src/styles/GlobalStyle.js
import { createGlobalStyle } from 'styled-components';
import reset from 'styled-reset';
import { font } from './FontStyle';

const GlobalStyles = createGlobalStyle`
  ${reset}
    .
    .
    .
  @media only screen and (max-width:***px) {
    // Media query도 설정해서 font 크기를 한번에 바꿀 수 있어서 아주 편함
  }
    .
    .
    .
  `
export default GlobalStyles;
```

```javascript
//src/App.js
import *** from "./component/***";
import GlobalStyles from "./styles/GlobalStyle";

function App() {
  return (
    <>
      <GlobalStyles />
      <***/>
    </>
  );
}
export default App;
```

