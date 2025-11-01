
// FILE: acceptance-checklist.md
```markdown
# Acceptance Test Checklist

Manual steps to verify core functionality:

1. Build
   - `dotnet build` in solution root succeeds.
   - `npm install && npm run build` in `frontend` succeeds.

2. Migrations & DB
   - `dotnet ef database update` creates tables.
   - Run `src/Parfait.Data` seed script to add sample data.

3. Run backend and open Swagger
   - Start API and visit `https://localhost:5001/swagger` (or http depending on dev). Secure endpoints require JWT.

4. Auth
   - Use seeded owner account to obtain JWT and refresh token.
   - Try refresh token flow.

5. Products / Customers / Production
   - Create product, produce stock (duplicate prevention), create sale (transactional decrement stock).
   - Observe optimistic concurrency on product stock.

6. Frontend
   - Login, view products, add sale while offline, confirm Dexie queue sync when back online.
   - Export dashboard to Excel.

7. Import
   - Import an Excel with duplicates and verify merge summary.

8. Health & Logging
   - Visit `/health` and confirm DB and disk checks.
   - Confirm logs redact PII.

9. CI
   - Push branch to GitHub and verify workflows run (build + tests).

