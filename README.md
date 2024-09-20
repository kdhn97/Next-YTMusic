# Next-YTMusic

인프런 - 기초부터 배우는 Next YTMusic 클론 코딩

# 섹션 4. NextJS 핵심 개념(이론)

### 3.1 HTML+CSS+JS vs React.js vs Next.js 차이점

    - HTML+CSS+JS
        - 기본기 - 작은 프로젝트나 간단한 웹 페이지
        - 단일 페이지 어플(SPA) 구축 어려움
        - 장점 : 가장 빠르다
        - 단점 : 큰 프로젝트 개발이 어려움

    - React
        - SPA
        - 페이스북에서 만든 JavaScript 라이브러리
        - 장점 : 웹에서 앱처럼 UI 상호작용 가능
        - 단점 : SEO 불리 및 초기 JS 로딩 느리다

    - Next
        - MPA
        - React 기반의 서버 사이드 렌더링(SSR) 및 정적 사이트 생성(SSG)
        - 장점 : SEO 최적화 및 초기 로딩 속도 향상

### 3.2 랜더링 종류 - CSR, SSR, Hydration

    - React.js
        - index.html (빈 화면) -> Js bundle (React Code)
        - CSR (React -> Virtual DOM -> Real DOM)

    - Next.js (Page Router)
        - SSR (React > html) -> 초기 화면에 html 요소 보임
        - html+css+js -> Js bundle (React Code) + hydration (html > React)
        - 이벤트 발생 시, CSR

    - Next.js (App Router)
        - SSR (React > html) -> 초기 화면에 html 요소 보임
        - Streaming Server Rendering [progressive hydration (부분 hydration 동시 진행)]
        - 이벤트 발생 시, CSR

### 3.3 컴포넌트 종류 - RSC, RCC, use client

    - React Server Component (RSC) -> SSR
        - Fetch data
            - 서버에서 직접 데이터를 가져올 수 있어 클라이언트-서버 간 추가적인 네트워크 요청이 필요 없습니다.
            - 예: const data = await fetch('https://api.example.com/data');
        - Access backend resources
            - 데이터베이스나 파일 시스템 등 서버 측 리소스에 직접 접근할 수 있습니다.
        - Keep sensitive information on the server
            - API 키나 비밀번호 같은 중요 정보를 클라이언트에 노출하지 않고 사용할 수 있습니다.
            - 예: const apiKey = process.env.API_KEY;
        - Keep large dependencies on the server / Reduce client-side JavaScript
            - 큰 라이브러리나 모듈을 서버에서만 사용하여 클라이언트로 전송되는 JavaScript 양을 줄일 수 있습니다.

    - React Client Component (RCC) -> SSR + CSR -> "use client"
        - Add interactivity and event listeners (Onclick, Onchange)
            - 클릭, 입력 등 사용자 상호작용을 처리

        - Use State and Lifecycle Effects (React Hooks)

        - Use browser-only APIs (브라우저 전용 API)

        - Use custom hooks that depend on state, effects or browser-only APIs (커스텀 Hooks)

        - Use React Class components (React Class 컴포넌트)

### 3.4 React Suspense ( Streaming, Progressive Hydration )

    - React Suspense
        - 비동기 작업을 처리하는 동안 로딩 상태를 표시

    - Streaming
        - 서버에서 생성된 HTML을 점진적으로 클라이언트에 전송하는 기술
        - 사용자가 전체 페이지 로딩을 기다리지 않고도 일부 콘텐츠를 볼 수 있게 해줍니다.

    - Progressive Hydration
        - 페이지의 각 부분을 독립적으로 hydrate할 수 있게 해주는 기술
