# capstone22 - 프뉴비(201840231 최기룡)
    팀 구성 : 배다슬(팀장, 프론트엔드), 최기룡(프론트엔드)
    팀명 정하기 : 프뉴비
    프로젝트 주제 정하기 : 일정 관리 웹 어플리케이션
    개발 환경 : HTML5 , CSS3 , JAVASCRIPT , REACT
    프로젝트 이름 : 오늘 하루를 책임질 '**투데이**'
    백엔드 없이 리액트로 일정관리 웹 어플리케이션을 만들고자 함.
    프로젝트 소개 사이트 : https://github.com/das0166/frontnewbe

## 2022.09.28
+ 회원가입 틀 완성(기능 다음주까지 예정)
+ 캘린더 틀 완성
+ 팀내 회의, 개발하면서 어려웠던 부분, 개선 방안 토의
    + 해상도 1920 x 1080으로 확정
    + 그에 따른 width height 전체 수정
    + 공통 css 수정
    + 전반적인 디자인 디테일 회의
    + 어려웠던 부분 : 회원가입 폼을 react-hook-form을 사용하며 이해하는데에 시간이 걸림
+ 다음주까지의 목표
    + 캘린더 기능 추가(일정 추가 기능)
    + 회원가입 기능 완성
    + 작품 포스터 제작
+ 작품 포스터 디자인 회의
## 2022.09.21
+ 개발 시작
+ 이번주 할 일 분배(일요일까지)
    + 회원가입 폼, 캘린더 폼 라이브러리 사용
+ 회원가입 폼 개발
    + **react-hook-form** 라이브러리 사용
+ react-hook-form
    + register 함수를 활용하여 여러 input 관리
    ```jsx
    <input
        id="name"
        type="text"
        placeholder="홍길동"
        {...register("name", {
        required: "이름은 필수 입력입니다.",
        })}
    />
    ```
    + handleSubmit : 함수에 data라는 인자를 받아 데이터를 출력해줌
    ```jsx
    const onSubmit = data => console.log(data);
    <form onSubmit={handleSubmit(onSubmit)}>
    ...
    </form>
    ```
    + 뛰어난 유효성 검사
    ```jsx
    <input
        id="email"
        type="text"
        placeholder="test@email.com"
        {...register("email", {
        required: "이메일은 필수 입력입니다.",
        pattern: {
        value: /\S+@\S+\.\S+/,
        message: "이메일 형식에 맞지 않습니다.",
        },
        })}
    />
    ```
+ react-router-dom 연결 및 학습
    + 라우팅: **웹에서 사용자가 요청한 URL에 따라 알맞는 페이지를 보여주는 것**
    + SPA : **한 개의 페이지로 이루어진 애플리케이션**
    브라우저의 History API를 사용하여 브라우저의 주소창의 값만 변경하고 라우팅 설정에 따라 또 다른 페이지를 보여주는 것
    + 라이브러리 설치
    ```jsx
    npm install react-router-dom
    ```
    + index.js에 BrowserRouter 컴포넌트 사용하여 적용
    ```javascript
    const root = ReactDOM.createRoot(document.getElementById('root'));
    root.render(
    <BrowserRouter>
      <App />
    </BrowserRouter>
    );
    ```
    + 메인 페이지, 고정 시킬 컴포넌트, 이동할 페이지 등에 주소를 정하고 link to를 이용하여 페이지 이동
    + App.js
    ```jsx
    function App() {
    return(
    <Routes>
      <Route element={<Header />}>
        <Route index element={<Todo />}/>
        <Route path = "/join" element={<Join />}/>
      </Route>
    </Routes>
    )}
    ```
    + header.js
    ```jsx
    <div className='login'>
        <Link to="/join">
            <img className='login' src={login} alt='login'/>
        </Link>
    </div>
    ```
+ 컴포넌트 분리
    + 공통된 부분 분리
## 2022.09.14 [3주차]
+ **로고 제작**  
![로고](./img/logo.png)
+ 작품 기술서 작성 완료
+ React 학습
    + Router-Dom 이용하여 페이지 이동
    + useState
+ git fork, pull-request, fetch 학습
    + 원하는 저장소 fork 후 fork한 repository clone
    + git remote add upstream fork했던 원격 저장소 주소
    + 커밋 후 pull-request
    + 원격 저장소에 변경사항 있을시에
    + git fetch upstream
    + git merge upstream/main 또는 upstream/master

## 2022.09.07 [2주차]
+ **작품 기술서 제작**
    + 작품개요 작성
    + 팀 규칙 정하기  

    + 작품기획(AS-IS, TO-BE)
    + 벤치마킹 사례 서치
    + 작품 와이어 프레임 제작  

    ![회로도](./img/schematic.png)
      
+ **정해진 기능**
    + 홈화면
        + 오늘 할 일이 보여짐
        + today 왼쪽에 있는 edit 버튼을 누르면 메모지,글 색상 등 마음대로 디자인 가능
        + 화살표를 눌러 다음 날로 이동하게 되면서 일정 확인 가능
        + 오른쪽 포스트잇에는 오늘 추가한 내용이 나옴  
    + 캘린더
        + 연도,월,주로 원하는 방식의 달력을 볼 수 있음
        + 해당 날짜에 간단하게 일정이 표시 됨
        + 생일이나 공휴일 등 주요 기념일 표시
        + 오늘이 아닌 다른 날짜의 일정을 추가 가능
    + 로그인
        + 유효성 검사
        + 소셜 로그인
+ **작품 디자인**  

![홈화면](./img/home.png)  
![메모지색상변경시](./img/home_change.png)
![캘린더](./img/calendar.png)
![로그인](./img/login.png)  



___
## 2022.08.31 [1주차]

+ 프로젝트의 전반적인 구성(팀 구성, 팀명, 프로젝트 주제 등)
+ 수업 내용 숙지(수행평가, 점수 등)
+ 프로젝트 기능 토론

