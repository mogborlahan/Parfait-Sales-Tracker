# Parfait & Juice Sales Tracker

A production-ready full-stack application: ASP.NET 9 Web API backend and React + Vite + TypeScript PWA frontend. Designed to run on minimal free-tier infrastructure (Koyeb for API + Postgres, Vercel for frontend).

## Highlights
- Clean Architecture: `Api`, `Core`, `Data`, `Models`, `Shared`.
- PostgreSQL + EF Core 9 (Npgsql).
- JWT auth with refresh tokens (secure, BCrypt hashed passwords).
- Offline-first frontend with Dexie (IndexedDB) and sync queue.
- Excel import/export support (server: EPPlus; client: SheetJS).
- Rate limiting, HSTS, HTTPS enforcement, Serilog structured logging.
- CI/CD: GitHub Actions for build/test and deploy to Vercel/Koyeb.

## Quick local dev (summary)
1. Install:
   - .NET 9 SDK
   - Node 20+
   - PostgreSQL
2. Clone repo and open terminal:
```bash
git clone <repo>
cd Parfait-Sales-Tracker
dotnet restore
cd src/Parfait.Data
dotnet ef database update --project ../Parfait.Data --startup-project ../Parfait.Api
# or run seed
dotnet run --project src/Parfait.Data
3. Run backend:
dotnet run --project src/Parfait.Api
4. Run frontend:
cd src/Parfait.Frontend
npm install
npm run dev

See detailed instructions below in README and infrastructure/.


Security appendix
Passwords hashed with BCrypt.
JWT secret must be strong and kept out of VCS.
CORS limited by env var.
HSTS & HTTPS enforced in production.
Rate limiting implemented.


Acceptance tests: See acceptance-checklist.md.


