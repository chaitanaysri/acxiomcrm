# AcxiomCRM Frontend

A frontend-only implementation baseline for the **AcxiomCRM Functional & Technical Project Specification**.

## Included

- Authentication UI: login, forgot password, password policy, lockout states
- Role-based navigation for Admin, Manager and Sales Executive
- Dashboard with KPIs and pipeline
- CRM contacts and customer profile
- Sales opportunities / pipeline board
- Follow-up management
- Audit log
- API integration settings and endpoint catalog
- Reports with charts and CSV export
- Client-side form validation and business validation examples
- Loading, empty, error and confirmation UI states
- Responsive desktop/tablet/mobile layout
- Local mock data and mock auth/session layer
- Reusable UI components and design tokens

## Run

Requirements: Node.js 18+.

```bash
npm install
npm run dev
```

Open the Vite URL shown in the terminal, normally `http://localhost:5173`.

Production build:

```bash
npm run build
npm run preview
```

## Demo accounts

The login screen accepts any non-empty email and a password with 8+ characters. Demo role selection is available on the login screen.

For UI testing:
- Admin: `admin@acxiomcrm.local`
- Manager: `manager@acxiomcrm.local`
- Sales Executive: `sales@acxiomcrm.local`
- Password: `Password123!`

## Backend integration

This project deliberately does **not** implement a real backend. Replace the functions in `src/services/api.ts` with real HTTP calls when the backend is available.

Recommended environment variable:

```env
VITE_API_BASE_URL=http://localhost:8080/api
```

Do not store secrets, tokens, or passwords in source code. Authentication, authorization and password hashing must be enforced server-side.

## Architecture

```text
src/
  components/       Reusable UI
  data/             Mock/demo data
  layouts/          App shell
  pages/            Route-level screens
  services/         API/auth abstraction
  store/            Lightweight frontend state
  styles/           Global design system
  types/            Domain types
```

## Functional baseline mapping

| Requirement | Frontend implementation |
|---|---|
| Validation | Form validation utilities, required fields, email/phone/password checks, business validation messages |
| Security | Password policy UI, lockout UI, session abstraction, no secret persistence |
| Authorization | Role-aware navigation and route guards |
| API | Central `api.ts` service layer + endpoint catalog |
| Reports | KPI dashboard, sales/funnel charts, activity report, CSV export |
| Audit | Audit log screen with filtering and event details |

## Important security note

This is a frontend implementation baseline. Client-side authorization is only a UX control. The backend must independently validate the user's session, role and permissions for every protected API operation.
