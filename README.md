# 메뉴 이벤트 만들기 
![](https://miro.medium.com/max/900/1*q99J7XLYVWgOt69E8IuXqw.gif)

안녕하세요 **코딩알려주는 누나**👩에요! 이번시간에는 자바스크립트로 어떻게하면 HTML과 CSS를 컨트롤할 수 있을까에 대해서 배웠는데 
수업중에 진행했던 코드와 함께 여러분들이 궁금해 하실수 있을 개념에 대해 정리를 해드리려 합니다!

* 강의🎞: 
* 데모 링크: https://menu-indicator.netlify.app
* 누나 온라인코스 : https://codingnoona.thinkific.com/

## 개념정리🎢
* document: document는 DOM트리의 최상위 객체이다 
DOM(Document Object Model)이라 하면 자바스크립트 입장에서 그저 일종의 문자열일 뿐인 HTML을 자바스크립트가 이해할수있게 객체의 형태로 바꿔둔것이다.(Document를 HTML이라고 이해하면 편하다). 이 DOM을 이제 자바스크립트가 마음대로 컨트롤할 수 있어야되는데 이때 필요한 기본 함수들과 속성값을 제공해주는게 document라는 객체이다. 

* document.getElementById : HTML태그를 JS파일로 불러오기 위해선 HTML태그를 선택을 해야하는데 그 선택을 하게 해주는 함수중 하나이다. 이 외에도 getElementsByClassName,querySelector,querySelectorAll 이 있다.

* Event객체 : addEventListener함수를 사용할때 매개변수로 event를 자동으로 넘겨준다. DOM내에서 이벤트가 발생할 시에 그 이벤트에 관한 모든 정보를 넘겨준다. 이벤트 발생 위치(event.curretTarget 또는 event.target), 이벤트 타입(evnet.type)등 이 있다.


## 소스코드💻
```htmlembedded=
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <nav>
        <div id="horizontal-underline"></div>
        <a href="#">About</a>
        <a href="#">Menu</a>
        <a href="#">Store</a>
        <a href="#">Service</a>
        <a href="#">Responsibility</a>
    </nav>

    <nav>
        <div id="vertical-underline"></div>
        <a href="#">About</a>
        <a href="#">Menu</a>
        <a href="#">Store</a>
        <a href="#">Service</a>
        <a href="#">Responsibility</a>
    </nav>

    
    <script src="main.js"></script>
</body>
</html>
```

```css=

nav:first-child {
    display: flex;
    justify-content: center;
    margin-bottom: 2em;
}
nav:nth-child(2){
    display: flex;
    align-items: center;
    flex-direction: column;
}
nav a {
    text-decoration: none;
    color:black;
    margin: 1em;
    font-size: 2em;
}

#horizontal-underline{
    position: absolute;
    left:0;
    height: 4px;
    width: 0;
    border-radius: 3px;
    transition: 0.5s;
    background-color: pink;
    top:0;

}

#vertical-underline{
    position: absolute;
    left:0;
    height: 4px;
    width: 0;
    border-radius: 3px;
    transition: 0.5s;
    background-color: skyblue;
    top:0;

}
```

```javascript=
let verticalBar = document.getElementById("vertical-underline");
let horizontalBar = document.getElementById("horizontal-underline");
let horizontalMenus = document.querySelectorAll("nav:first-child a");
let verticalMenus = document.querySelectorAll("nav:nth-child(2) a");

function verticalIndicator(e) {
  verticalBar.style.left = e.offsetLeft + "px";
  verticalBar.style.width = e.offsetWidth + "px";
  verticalBar.style.top = e.offsetTop + e.offsetHeight + "px";
}
function horizontalIndicator(e) {
  horizontalBar.style.left = e.offsetLeft + "px";
  horizontalBar.style.width = e.offsetWidth + "px";
  horizontalBar.style.top = e.offsetTop + e.offsetHeight + "px";
}

horizontalMenus.forEach((menu) =>
  menu.addEventListener("click", (e) =>
    horizontalIndicator(e.currentTarget)
  )
);

verticalMenus.forEach((menu) =>
  menu.addEventListener("click", (e) => verticalIndicator(e.currentTarget))
);

```


![](https://gif.fmkorea.com/files/attach/new/20170829/486616/486636532/759265048/e3283afbceb6be7766b38f101fa337d2.gif)
오늘도 여러분들이 한층 더 진화했기를 바라면서 
우리 다음강의에서 만나요!! 🎈
