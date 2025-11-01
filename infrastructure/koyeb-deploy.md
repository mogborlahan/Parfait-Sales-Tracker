# Deploying Parfait.Api to Koyeb (free tier)

1. Build a Docker image (optional). Koyeb can deploy from Dockerfile or GitHub repo.

2. Recommended Dockerfile provided at `/docker/Dockerfile`. The image exposes port `80`.

3. Configure Koyeb service:
   - Image or Git repo: connect GitHub and point to `src/Parfait.Api`.
   - Environment variables: set values from `.env.example`, especially `ConnectionStrings__DefaultConnection`, `JWT__Secret`, `CORS__AllowedOrigins`, `ASPNETCORE_ENVIRONMENT=Production`.
   - Set `CMD` to run the app; Koyeb will use container's default.

4. PostgreSQL:
   - Use managed Postgres add-on linked to Koyeb app or external provider; set `ConnectionStrings__DefaultConnection`.

5. Health & scaling:
   - Koyeb free tier scales-to-zero; app must handle cold starts. Keep startup fast.

6. Secrets:
   - Add JWT secret and DB credentials to Koyeb secrets, not in code.

7. CI:
   - Use GitHub Actions to build and push image to a registry (e.g., GitHub Container Registry), then trigger Koyeb via API (secrets required).

