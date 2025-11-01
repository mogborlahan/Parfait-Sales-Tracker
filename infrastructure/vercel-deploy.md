# Deploying frontend to Vercel

1. Create a Vercel project and connect the repo.
2. Set build command: `npm run build` and output directory: `dist`.
3. Environment variables:
   - `VITE_API_BASE_URL=https://<your-api-host>`
4. Protect the project with required environment variables in the Vercel UI.
5. Optional: set up custom domain and HTTPS.

