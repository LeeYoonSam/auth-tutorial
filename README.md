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
## Login form
## Register form
## Database & Prisma setup
## Create user
## Middleware & Login
## Callbacks
## OAuth(Google & Github)
## Resend(Sending emails)
## Email verification
## Reset password email
## Reset password form
## Two factor authentication
## User button
## Server & Client example
## Admin example
## Settings page
## Sponsor demo
## Deployment