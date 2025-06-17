# 🎭 Persona Mini Homepage

![Persona 3 Reload Logo](https://images.squarespace-cdn.com/content/v1/5e1bc9535920f22934e85ea8/9176f066-e11e-4f9f-a956-5c178528a843/persona-3-reload.jpeg)

<img width="1470" alt="image" src="https://github.com/user-attachments/assets/ca2651b2-0714-4154-9f74-9cbe26f1b3c3" />


## 📋 프로젝트 소개

이 프로젝트는 아틀러스의 인기 RPG 시리즈 '페르소나'를 테마로 한 미니홈페이지입니다. 특히 '페르소나 3 리로드'를 중심으로, 시리즈의 캐릭터와 게임 정보를 소개하는 인터랙티브 웹사이트입니다.

## 📋 프로젝트 정보

- **개발 기간**: 2024.07 ~ 2024.08
- **개발자**: Toon
- **배포 주소**: [https://persona3reloadminihomep.web.app](https://persona3reloadminihomep.web.app)

## 🛠️ 사용 기술
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![SCSS](https://img.shields.io/badge/SCSS-CC6699?style=for-the-badge&logo=sass&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)

## ✨ 주요 기능

### 1. 인트로 애니메이션
페르소나 시리즈의 분위기를 살린 인트로 애니메이션을 구현했습니다.

```javascript
bgVideo1.addEventListener("play", () => {
  gek.classList.add("active");
});

bgVideo2.addEventListener("ended", () => {
  bgVideo2.style.display = "none";
  bgVideo3.autoplay = true;
  bgVideo3.play();
  setTimeout(() => {
    wrapper.classList.add("active");
    heading.classList.add("active");
  }, 1600);
});
```

### 2. 실시간 시계 기능
현재 시간과 날짜를 실시간으로 표시하는 기능을 구현했습니다.

```javascript
setInterval(() => {
  const today = new Date();
  let hrs = today.getHours();
  let mins = today.getMinutes();
  let secs = today.getSeconds();

  hrs < 10 ? (hrs = `0${hrs}`) : (hrs = hrs);
  mins < 10 ? (mins = `0${mins}`) : (mins = mins);
  secs < 10 ? (secs = `0${secs}`) : (secs = secs);

  const timeDisplay = document.querySelector(".clock .time");
  timeDisplay.innerText = `${hrs}:${mins}:${secs}`;

  if (hrs === "00" && mins === "00" && secs === "00") {
    updateDate(today);
  }
}, 1000);
```

### 3. 동적 페이지 전환
iframe을 활용한 동적 페이지 전환 기능을 구현했습니다.

```javascript
const frames = [
  "./home/home.html",
  "./about/about.html",
  "./jukebox/jukebox.html",
  "./game/game.html",
];

modes.forEach((mode, index) => {
  mode.addEventListener("click", () => {
    heading.classList.remove("active");
    setTimeout(() => {
      heading.classList.add("active");
    }, 200);
    heading.innerHTML = `<span>0${index + 1}</span>${titleIndicators[index]}`;

    frame.setAttribute("src", frames[index]);
    modes.forEach((item, i) => {
      if (index === i) {
        item.classList.add("active");
      } else {
        item.classList.remove("active");
      }
    });
  });
});
```

### 4. 캐릭터 선호도 저장
로컬 스토리지를 활용한 사용자 캐릭터 선호도 저장 기능을 구현했습니다.

```javascript
const bias = document.querySelector("select");
bias.addEventListener("change", (e) => {
  const iframe = document.querySelector("iframe");
  localStorage.setItem("bias", bias.value);
  iframe.src = "./home/home.html";
});
```

## 📁 프로젝트 구조

```
Persona-MiniHomepage/
├── index.html              # 메인 페이지
├── style.css               # 컴파일된 CSS
├── style.scss              # SCSS 소스
├── reset.css               # 리셋 CSS
├── reset.scss              # 리셋 SCSS
├── script.js               # 메인 JavaScript
├── contents/               # 미디어 파일 (이미지, 비디오)
├── home/                   # 홈 페이지 관련 파일
├── about/                  # 소개 페이지 관련 파일
├── jukebox/                # 음악 페이지 관련 파일
└── game/                   # 게임 페이지 관련 파일
```

## 💡 배운 점

### 기술적 측면

- **비디오 제어 API**: JavaScript를 사용한 비디오 요소 제어 및 이벤트 처리 방법을 배웠습니다.
- **로컬 스토리지 활용**: 사용자 선호도 정보를 로컬 스토리지에 저장하고 활용하는 방법을 익혔습니다.
- **SCSS 활용**: 중첩 선택자와 변수를 활용한 효율적인 스타일 관리 방법을 배웠습니다.
- **iframe 통신**: iframe을 활용한 페이지 간 통신 및 데이터 전달 방법을 학습했습니다.

### 디자인 측면

- **게임 테마 디자인**: 게임의 시각적 아이덴티티를 웹 디자인에 적용하는 방법을 연구했습니다.
- **애니메이션 효과**: CSS 애니메이션과 JavaScript를 활용한 다양한 시각적 효과 구현 방법을 익혔습니다.
- **타이포그래피**: 게임 분위기에 맞는 폰트 선택과 텍스트 스타일링 방법을 배웠습니다.

## 🚀 설치 및 실행 방법

1. 저장소를 클론합니다:
   ```
   git clone https://github.com/GiToon10100011/Persona-MiniHomepage.git
   ```
2. 프로젝트 폴더로 이동합니다:
   ```
   cd Persona-MiniHomepage
   ```
3. 웹 브라우저에서 `index.html` 파일을 엽니다.

## ⚠️ 면책 조항

이 프로젝트는 팬이 제작한 비공식 사이트입니다. '페르소나' 시리즈와 관련된 모든 콘텐츠의 저작권은 아틀러스와 세가에 있습니다.
