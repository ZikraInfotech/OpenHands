# Executive Summary

OpenHands is an MIT‑licensed framework for running AI coding agents inside Docker or remote runtimes. The open source version is single‑user and uses localhost URLs for VS Code and web previews. To monetize it as a cloud service we recommend:

1. **Introduce Multi‑Tenant Auth** – Implement OAuth‑based `UserAuth` and store user/tenant data in CloudSQL.
2. **Expose Runtimes Publicly** – Run each runtime in its own pod on GKE with subdomain routing (`https://{id}.domain`) via Traefik. VS Code and preview ports are served through gateway proxies.
3. **Automate Build & Dependency Installation** – Detect repo stack using Buildpacks/Nixpacks and build container images automatically.
4. **Add Billing Hooks** – Use Stripe and the existing `ENABLE_BILLING` flag to track usage and charge per runtime minute or API call.
5. **White‑Label Options** – Toggle analytics and replace logos through environment variables so partners can brand the UI.

This approach scales horizontally on GKE or Cloud Run while keeping tenants isolated at the namespace/service‑account level. It enables live previews and embedded VS Code directly in the browser without exposing localhost, providing a foundation for a Coding‑as‑a‑Service platform.
