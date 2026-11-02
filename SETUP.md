# StudentVoice setup

StudentVoice is an independent institutional reporting platform. The product UI is implemented with plain HTML, CSS and JavaScript under `client/`. It uses sample records and a browser-based service preview state so judges can explore the flows without entering sensitive information.

## Run locally

From `/home/ubuntu/studentvoice`, run:

```bash
pnpm install
pnpm dev
```

The managed preview uses port 3000. For a static-only preview, use `pnpm dev:static`.

## Access

Students create an anonymous handle and password. No Gmail account, email address, real name, phone number, or student ID is required. When the server and SQL database are available, the handle/password account is stored server-side with a salted password hash and a secure session cookie, so the student can sign out and sign in again from another device. The restricted Agency workspace is protected by the agency access code `rimshaagency26`; enter it in the Agency workspace and press “Enter agency workspace” to open the case desk.

## Working now

Navigation, responsive layout, anonymous handle + password student accounts, persistent server sessions, SQL-backed report storage, agency update timelines, category cards, simulated district/category routing, client-side report validation, reference-number generation, report history, status timeline, notifications, student-to-agency report visibility, agency search/filtering, selected-case details, status updates, internal-note separation, privacy/safety content, and explicit privacy and service-boundary notices are functional in the browser when the API is running. Standalone HTML remains available with a clearly limited browser-only fallback.

## Production requirements

The persistent account API is now connected to the managed SQL database. Do not run the standalone HTML as the official deployment because its fallback mode is browser-only. Production should keep `DATABASE_URL` and `AGENCY_ACCESS_CODE` server-side, enforce HTTPS, rotate credentials, add rate limiting and password recovery policy, and configure backups and retention.

## Python/SQL production handoff

The managed backend provides the persistent API in `server/studentApi.ts` and SQL tables for anonymous accounts, server sessions, reports, and report status updates. Use server-side sessions, enforce role-based access on every report endpoint, store evidence outside the public web root, validate uploads, log access, apply retention/deletion rules, and keep secrets in the deployment environment. The frontend calls these endpoints with credentials and renders only authorized responses.

Do not present this institutional release as an official government website, an emergency channel, or a guarantee of anonymity.
