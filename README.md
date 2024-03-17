# [Next Auth V5](https://www.youtube.com/watch?v=1MTyCvS05V4)
- Github & Live Website: https://www.codewithantonio.com/projects/auth-masterclass
- Auth.js: https://authjs.dev/
- Middleware config: https://dub.sh/Apr6dvD
- Resend: https://resend.com/
- Node.js: https://nodejs.org/en
- ShadcnUI: https://ui.shadcn.com/
- Clerk: https://dub.sh/SdVFxFU

Learn how to add advanced authentication to your NextJS App.

Key Features:
- 🔐 Next-auth v5 (Auth.js)
- 🚀 Next.js 14 with server actions
- 🔑 Credentials Provider
- 🌐 OAuth Provider (Social login with Google & GitHub)
- 🔒 Forgot password functionality
- ✉️ Email verification
- 📱 Two factor verification (2FA)
- 👥 User roles (Admin & User)
- 🔓 Login component (Opens in redirect or modal)
- 📝 Register component
- 🤔 Forgot password component
- ✅ Verification component
- ⚠️ Error component
- 🔘 Login button
- 🚪 Logout button
- 🚧 Role Gate
- 🔍 Exploring next.js middleware
- 📈 Extending & Exploring next-auth session
- 🔄 Exploring next-auth callbacks
- 👤 useCurrentUser hook
- 🛂 useRole hook
- 🧑 currentUser utility
- 👮 currentRole utility
- 🖥️ Example with server component
- 💻 Example with client component
- 👑 Render content for admins using RoleGate component
- 🛡️ Protect API Routes for admins only
- 🔐 Protect Server Actions for admins only
- 📧 Change email with new verification in Settings page
- 🔑 Change password with old password confirmation in Settings page
- 🔔 Enable/disable two-factor auth in Settings page
- 🔄 Change user role in Settings page (for development purposes only)

## 폴더 및 파일 요약
- actions: "use server" 로 비동기 작업시 실행 할 액션
- libs: 서버 사이드에서 사용 할 비동기 작업
- hooks: 클라이언트 사이드에서 사용 할 hook
- routes.ts: public, auth 등등 Route 관리
- next-auth.d.ts: next-auth 에서 사용 하는 session 커스텀
- middleware.ts: 인증 시 리디렉트 관리
- auth.ts: 로그인, 세션, 인증 처리
- auth.config.ts: 인증 프로바이더 제공 및 인증 로직

## Project setup
프로젝트 생성 - create-next-app
```bash
npx create-next-app@latest auth-tutorial
Need to install the following packages:
create-next-app@14.1.0
Ok to proceed? (y) y
✔ Would you like to use TypeScript? … No / Yes
✔ Would you like to use ESLint? … No / Yes
✔ Would you like to use Tailwind CSS? … No / Yes
✔ Would you like to use `src/` directory? … No / Yes
✔ Would you like to use App Router? (recommended) … No / Yes
✔ Would you like to customize the default import alias (@/*)? … No / Yes
Creating a new Next.js app in /Users/user/Documents/Github/auth-tutorial.

Using npm.

Initializing project with template: app-tw 


Installing dependencies:
- react
- react-dom
- next

Installing devDependencies:
- typescript
- @types/node
- @types/react
- @types/react-dom
- autoprefixer
- postcss
- tailwindcss
- eslint
- eslint-config-next


added 360 packages, and audited 361 packages in 24s

128 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
Initialized a git repository.

Success! Created auth-tutorial at /Users/user/Documents/Github/auth-tutorial
```

- shadcn-ui 추가
```bash
npx shadcn-ui@latest init
✔ Which style would you like to use? › New York
✔ Which color would you like to use as base color? › Slate
✔ Would you like to use CSS variables for colors? … no / yes

✔ Writing components.json...
✔ Initializing project...
✔ Installing dependencies...

Success! Project initialization completed. You may now add components.
```

### dependencies
- `npx shadcn-ui@latest add button`


## Routing crash course
- [Routing](https://nextjs.org/docs/pages/building-your-application/routing)

### Index routes
- 라우터는 인덱스라는 이름의 파일을 디렉토리의 루트로 자동 라우팅합니다.

```
- pages/index.js → /
- pages/blog/index.js → /blog
```

### Nested routes
- 라우터는 중첩 파일을 지원합니다. 중첩된 폴더 구조를 만들면 파일이 자동으로 동일한 방식으로 라우팅됩니다.

```
pages/blog/first-post.js → /blog/first-post
pages/dashboard/settings/username.js → /dashboard/settings/username
```

## Home page
- app/globals.css 수정
  - 기본 높이 100% css 추가
- app/page.tsx 수정
  - 기본 화면 구성 및 로그인 버튼 추가
- components/auth/login-button.tsx 생성
  - 로그인 버튼 래핑 컴포넌트
  - 클릭 컨트롤

### Note
Gradient 적용 방법
```
<main className="bg-[radial-gradient(ellipse_at_top,_var(--tw-gradient-stops))] from-sky-400 to-blue-800">
```
- top 쪽은 from-sky-400 부터 아래로 색이 진해짐
- 양쪽 사이드는 안쪽에서 부터 바깥으로 from-sky-400 -> to-blue-800 으로 진해짐


## Card wrapper
카드 형태의 로그인 컴포넌트 구현

- app/auth/login/page.tsx
  - 로그인 폼
- app/auth/layout.tsx
  - 로그인 레이아웃
- components/auth/login-form.tsx
  - 로그인 폼 영역 구성
- components/auth/card-wrapper.tsx
  - 카드를 감싸는 래퍼
- components/auth/back-buttons.tsx
  - 뒤로가기 버튼 컴포넌트
- components/auth/header.tsx
  - 헤더 컴포넌트
- components/auth/social.tsx
  - 소셜 로그인 버튼

### dependencies
- `npx shadcn-ui@latest add card`
  - 카드 컴포넌트
- `npm i react-icons`
  - 리액트 아이콘 팩


## Login form
- schemas/index.ts 추가
  - zod 스키마 생성
- components/auth/login-form.tsx 수정
  - form 추가 및 useForm
- components/form-error.tsx 추가
  - form 작성 실패시 보여줄 컴포넌트
- components/form-success.tsx 추가
  - form 작성 성공시 보여줄 컴포넌트

### dependencies
- `npx shadcn-ui@latest add form`
- `npx shadcn-ui@latest add input`

### Note
**zod**
- Zod는 TypeScript와 잘 어울리는 스키마 선언 및 검증 라이브러리입니다.
- Zod를 사용하면 데이터 타입을 한 번 선언하면 Zod가 자동으로 TypeScript 타입을 추론해줍니다.
- Zod는 간단한 타입을 복잡한 데이터 구조로 쉽게 조합할 수 있습니다.
- React Hook Form은 React에서 자주 사용되는 "성능, 유연성, 확장성이 뛰어난 폼 라이브러리"입니다.
- React Hook Form은 Zod와 함께 사용할 수 있으며, Zod를 통해 폼 데이터의 유효성을 검사할 수 있습니다.
- Next.js 13에서는 Server Actions라는 새로운 기능이 추가되었는데, 이는 서버에서 폼 데이터를 처리하고 응답을 보내는 데 유용합니다.

## Register form
- actions/login.ts 추가
  - 스키마 유효성 검사에 따라서 성공/실패 메시지 리턴
- actions/register.ts 추가
  - 스키마 유효성 검사에 따라서 성공/실패 메시지 리턴
- components/auth/login-form.tsx 수정
  - 로그인 action 연결
  - success, error 연결
- components/auth/register-form.tsx 추가
  - 회원가입 폼 컴포넌트
- schemas/index.ts 수정
  - RegisterSchema 유효성 검사 추가


## Database & Prisma setup
- lib/db.ts 생성
  - prisma 클라이언트 생성
- Prisma 초기 설정
  - `npx prisma init`
- Database 연동
  - 데이터베이스는 [Neon Serverless Postgres](https://neon.tech/) 사용
  - Neon 프로젝트 생성
- prisma/schema.prisma 설정
  - database 정보 설정 (Neon postgre 사용)
  - model User 생성
  - `npx prisma generate` - Prisma 클라이언트 스키마 생성
  - `npx prisma db push` - 데이터베이스에 Prisma 스키마 동기화
- [auth/prisma-adapter](https://authjs.dev/reference/adapter/prisma) 연결
  - prisma/schema.prisma 수정
    - User 수정
    - model Account 추가

### dependencies
- `npm i -D prisma`
- `npm i @prisma/client`
- `npm i @auth/prisma-adapter`


## Create user
- actions/register.ts 수정
  - 회원가입 데이터베이스 연결
  - bcryptjs 를 사용해서 비밀번호 hash 처리
  - 중복 가입 에러 처리
- data/user.ts 생성
  - email, id 로 User 데이터를 반환하는 데이터 추가

### dependencies
- `npm i bcryptjs`
- `npm i -D @types/bcryptjs`


## Middleware & Login
### [Auth.js 설치](https://authjs.dev/guides/upgrade-to-v5)
- `npm install next-auth@beta`
- auth.ts 생성
  - https://authjs.dev/guides/upgrade-to-v5#configuration 복사
- app/api/auth/[...nextauth]/route.ts 생성
- http://localhost:3000/api/auth/providers 프로바이더 확인
  - AUTH_SECRET 생성 
    - `npx auth secret`
  - .env
    - 생성된 AUTH_SECRET 추가
- [middleware 추가](https://authjs.dev/reference/nextjs#in-middleware)
  - middleware.ts 생성
- [Edge compatibility](https://authjs.dev/guides/upgrade-to-v5#edge-compatibility)
  - 인증 구성 분할
  - NextAuth.js는 두 가지 세션 전략을 지원합니다. 어댑터를 사용하는 경우 세션 데이터를 데이터베이스에 저장하도록 선택할 수 있습니다. 데이터베이스 및 해당 어댑터가 Edge 런타임/인프라와 호환되지 않는 한 "데이터베이스" 세션 전략을 사용할 수 없습니다.
  - `auth.config.ts` 생성
    - next-auth 에서 제공하는 credentila 함수의 authorize 콜백을 통해서 DB 의 유저 정보와 비밀번호가 일치하는지 검증
  - `auth.ts` 수정
    - authConfig, PrismaAdapter 를 사용해서 인증하도록 수정
    - `npm i @auth/prisma-adapter` 어댑터 설치
  - 미들웨어가 엣지와 호환되지 않는 어댑터로 가져오기를 사용하고 있지 않은지 확인합니다:
    ```
    - export { auth as middleware } from './auth'
    + import authConfig from "./auth.config"
    + import NextAuth from "next-auth"
    + export const { auth: middleware } = NextAuth(authConfig)
    ```
- `app/(protected)/settings/page.tsx` 생성
  - 인증 테스트 페이지 추가
- `routes.ts` 생성
  - publicRoutes, apiRoutes 등 route 관련 정보 제공
  - `middleware.ts` 수정
    - auth 콜백 수정
      - 로그인 유무에 따라서 리디렉트 처리
- `auth.ts` 수정
  - signIn, signOut 추가
- `actions/login.ts` 수정
  - 로그인 액션에 next-auth 의 signIn 에 credentials 프로바이더로 로그인 처리
  - 로그인 후 settings 페이지 리디렉트
- `app/(protected)/settings/page.tsx` 수정
  - 로그아웃 구현
  - 로그아웃 후 로그인 페이지 리디렉트

## [Callbacks](https://authjs.dev/guides/basics/callbacks)
- `auth.ts` 수정
  - NextAuth Callbacks 추가
    - session, jwt
- `prisma/schema.prisma` 수정
  - UserRole 추가 (ADMIN, USER)
  - `npx prisma generate`
  - `npx prisma migrate reset`
  - `npx prisma db push`
- `next-auth.d.ts` 생성
  - [next-auth type 확장](https://authjs.dev/getting-started/typescript)

### Note
**NextAuth - Callbacks**
- 콜백은 동작이 수행될 때 발생하는 상황을 제어하는 데 사용할 수 있는 비동기 함수입니다.
- 콜백은 데이터베이스 없이 액세스 제어를 구현하고 외부 데이터베이스 또는 API와 통합할 수 있기 때문에 특히 JSON 웹 토큰과 관련된 시나리오에서 매우 강력합니다.


## OAuth(Google & GitHub)
- `auth.config.ts` 수정
  - Provider 에 GitHub, Google 프로바이더 추가
    - clientId, clientSecret 추가(`.env` 에 설정 값을 추가)
  - `http://localhost:3000/api/auth/providers` 프로바이더 확인
  - providers GitHub clientId, clientSecret 추가
    - GitHub 에서 [OAuth 설정 후 키 가져오기](#github-oauth-설정)
  - providers Google clientId, clientSecret 추가
    - Google 에서 [OAuth 설정 후 키 가져오기](#google-oauth-설정)
- `components/auth/social.tsx` 수정
  - 소셜 로그인을 지원하도록 소셜 로그인 버튼 onClick 수정
- [소셜 계정과 데이터베이스의 사용자와의 연결](https://authjs.dev/guides/basics/events#linkaccount)
  - `auth.ts` 수정
    - events: linkAccount 추가
      - 데이터베이스 `emailVerifed` 필드 데이터 채워짐
    - pages 추가
      - 로그인, 에러 path 지정
      - `app/auth/error/page.tsx` 에러 페이지 추가
        - `components/auth/error-card.tsx` 에러 컴포넌트 카드 추가
- `components/auth/login-form.tsx` 수정
  - 소셜 계정 이메일 중복시 에러 추가 (**OAuthAccountNotLinked 에러**)
    
### GitHub OAuth 설정
- GitHub(login) > Settings > Developer Settings > OAuth Apps > Register a new application
  - Application name: auth-tutorial
  - Homepage URL: http://localhost:3000
  - Authorization callback URL: http://localhost:3000/api/auth/callback/github
    - `http://localhost:3000/api/auth/providers` 여기서 github callbackUrl 을 복사
- 새로운 어플리케이션이 생성되면 clientId를 받을 수 있습니다.
- Client secrets > Generate a new client secret 으로 Secret 생성

### Google OAuth 설정
- google api console 검색
- 상단 프로젝트 선택 > 새 프로젝트 > 프로젝트 생성
- APIs & Services 검색 or 메뉴 클릭 > OAuth consent screen(OAuth 동의 화면)
  - External(외부) 타입 선택 > 만들기
  - 앱 이름, 사용자 지원 이메일, 개발자 연락처 정보 등 필수 정보 입력 후 진행
  - 나머지 단계는 별다른 입력없이 통과
- Credentials
  - CREATE CREDENTIALS > OAuth client ID
    - Application type: Web application
    - Name: web client 1
    - Authorized JavaScript origins: http://localhost:3000
    - Authorized redirect URIs: http://localhost:3000/api/auth/callback/google
      - `http://localhost:3000/api/auth/providers` 여기서 google callbackUrl 을 복사
- OAuth client created - Client ID, Client secret 만들기 완료
- 테스트를 하기 위해서는 **테스트 사용자** 추가 필요

### Note
**OAuthAccountNotLinked 에러 발생(소셜 로그인 이메일 중복)**
- Social 계정으로 로그인 시 같은 이메일을 사용할 경우 `OAuthAccountNotLinked` 에러가 발생
  - 따로 처리하려면 별도의 페이지를 구현해서 처리
  - 테스트시에는 디비에 데이터를 삭제 후 테스트


## Resend(Sending emails)
- prisma/schema.prisma 수정
  - VerificationToken 모델 추가
- data/verification-token.ts 생성
  - 데이터베이스에서 email, token 으로 verification token 가져오기
- lib/tokens.ts 생성
  - 새로운 토큰 생성(기존 토큰이 있으면 삭제)
  - `npm i uuid` 설치
  - `from "uuid"` 를 사용하기 위해 `npm i --save-dev @types/uuid` 설치
- actions/register.ts 수정
  - 회원 가입시 인증 토큰 생성
- actions/login.ts 수정
  - 로그인시 이메일 인증이 안되어 있을 경우 토큰 재생성 후 메시지만 전달
- lib/mail.ts 생성
  - **resend** 를 사용해서 이메일 전송(토큰 인증)
- actions/register.ts | actions/login.ts 수정
  - 회원가입/로그인 시 이메일 전송

### [Resend](https://resend.com/)
- 이메일 전송 서비스
- 회원가입 > 팀 만들기 > API Key 추가
- `npm install resend` 설치
- `.env` RESEND_API_KEY 추가

### dependencies
- `npm i uuid`
- `npm i --save-dev @types/uuid`


## Email verification
- `routes.ts` 수정
  - public routes 에 이메일 인증시 사용하는 경로 추가
- `app/auth/new-verification/page.tsx` 생성
  - 이메일 인증 페이지
- `components/auth/new-verification-form.tsx` 생성
  - 이메일 인증 폼
  - searchParmas 의 token 으로 자동 인증 처리
  - success, error 메시지 처리
- `actions/new-verification.ts` 생성
  - 데이터베이스 토큰 정보에 따라 유효성 체크
  - 유효한 토큰이면 유저정보 업데이트

### dependencies
- `npm i react-spinners`


## Reset password email
- `components/auth/login-form.tsx` 수정
  - 비밀번호 재설정 버튼 추가
  - 비밀번호 재설정 화면 이동
- `routes.ts` 수정
  - authRoutes 에 비밀번호 재설정 path 추가
- `app/auth/reset/page.tsx` 생성
  - 비밀번호 재설정 화면
- `components/auth/reset-form.tsx` 생성
  - 비밀번호 재설정 폼
- `schemas/index.ts` 수정
  - ResetSchema 추가
- `actions/reset.ts` 생성
  - 이메일 재전송을 위한 액션
  - 이메일 유효성 체크
  - 이메일 재전송
- `prisma/schema.prisma` 수정
  - PasswordResetToken 모델 추가
- `data/password-reset-token.ts` 생성
  - 데이터베이스에서 passwordResetToken 모델의 데이터를 가져오는 역할
- `lib/tokens.ts` 수정
  - passwordResetToken 에서 사용 할 토큰 및 유효기간 데이터 생성
  - 데이터베이스 토큰 데이터 최신화
- `lib/mail.ts` 수정
  - 패스워드 재설정 이메일 발송 추가


## Reset password form
- routes.ts 수정
  - authRoutes 에 `/auth/new-password` 추가
- `app/auth/new-password/page.tsx` 생성
  - 패스워드 재설정 화면
- `components/auth/new-password-form.tsx` 생성
  - 패스워드 재설정 화면 폼
- `schemas/index.ts` 수정
  - NewPasswordSchema 추가
- `actions/new-password.ts` 생성
  - 비밀번호 재설정 화면에서 사용 할 버튼 액션
  - 유효성 체크(길이, 토큰 만료, 토큰 파라미터 등)
  - 데이터베이스 유저 업데이트, 사용 한 토큰 제거

## Two factor authentication
- `prisma/schema.prisma` 수정
  - TwoFactorConfirmation 모델 추가
  - TwoFactorToken 모델 추가
  - User 모델에 twoFactor 관련 필드 추가
  - prisma
    - `npx prisma generate`
    - `npx prisma migrate reset`
    - `npx prisma db push`
- `data/two-factor-token.ts` 생성
  - token, email 로 2단계 토큰 정보 가져옴
- `data/two-factor-confirmation.ts` 생성
  - 데이터베이스에서 2단계 인증 정보 가져옴
- `lib/tokens.ts` 수정
  - 2 단계 인증에서 사용할 토큰 생성
  - crypto 내장 함수 사용해서 토큰 생성
- `lib/mail.ts` 수정
  - 2단계 인증 메일 전송
- `auth.ts` 수정
  - signIn 콜백에 2FA 인증 업데이트
- `actions/login.ts` 수정
  - 로그인시 2FA 활성 상태 체크 후 분기
  - 2FA 데이터베이스 정보 삭제 및 예외처리 추가
- `components/auth/login-form.tsx` 수정
  - 2FA 활성/비활성화 UI 변경
  - 2FA 활성 상태일경우 이메일로 코드를 받아서 로그인


## User button
- app/(protected)/settings/page.tsx 수정
  - useSession 훅을 통해서 세션 정보를 가져오도록 수정
- app/layout.tsx 수정
  - Root 에 SessionProvider 추가 session 정보 세팅
- actions/logout.ts 생성
  - 로그아웃 처리
- app/(protected)/layout.tsx 생성
  - navbar 를 가진 상위 레이아웃 추가
- app/(protected)/_components/navbar.tsx 생성
  - 설정 메뉴 네비게이션 버튼
- hooks/use-current-user.ts 생성
  - useSession 으로 현재 유저 정보를 가져오는 훅 생성
- components/auth/logout-button.tsx 생성
  - 로그아웃 컴포넌트
- components/auth/user-button.tsx 생성
  - 유저 아바타 컴포넌트
  - 드롭다운 메뉴 구현
    - 로그아웃

### dependencies
- `npx shadcn-ui@latest add dropdown-menu`
- `npx shadcn-ui@latest add avatar`


## Server & Client example
- `app/(protected)/server/page.tsx` 생성
  - 네비게이션 Server 에서 보여줄 유저 정보 화면
- `components/user-info.tsx` 생성
  - 유저 정보 컴포넌트
  - shadcn-ui Badge 추가
    - variant.success 타입 추가
- `auth.ts` 수정
  - jwt: 토큰 정보에 isTwoFactorEnabled 정보 전달
  - session: 토큰 정보로 session.user.isTwoFactorEnabled 설정
- `next-auth.d.ts` 수정
  - ExtendedUser.isTwoFactorEnabled 추가
- `app/(protected)/client/page.tsx` 생성
  - 서버와 동일한 컴포넌트를 복사해서 Client 유저 정보 화면 추가

### dependencies
- `npx shadcn-ui@latest add badge`


## Admin example
- `app/(protected)/admin/page.tsx` 생성
  - 관리자만 사용하는 화면
  - role-gate 로 권한 메시지 표시
  - 관리자용 액션 생성
- `hooks/use-current-role.ts` 생성
  - role 가져오는 hook 생성
- `components/auth/role-gate.tsx` 생성
  - 권한 메시지 컴포넌트
- `app/api/admin/route.ts` 생성
  - 관리자가 사용 할 API
- `app/layout.tsx` 수정
  - 상위에 <Toaster /> 추가 (sonner)


### dependencies
- `npx shadcn-ui@latest add sonner` : toast


## Settings page
## Sponsor demo
## Deployment