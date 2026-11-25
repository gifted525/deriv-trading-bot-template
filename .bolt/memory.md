# Project memory

## Product intent & audience

- Trading bot web app that connects to Deriv trading platform via OAuth
- Users can log in with Deriv, build bots visually, run them against real-time trading data
- Core surfaces: dashboard, visual bot builder, charts pages
- Mobile-responsive; works on phone and desktop browsers

## Brand personality & voice

- Brand identity and theming are driven by a brand config file (colors, logo, production hostname)
- Brand styles are generated from config into a stylesheet the build depends on

## Visual design & UX direction

- SPA architecture; client-side routing handles URL parameters from Deriv OAuth redirect
- Visual bot builder is a primary interactive surface
- Real-time charts/data display
- Mobile layout supported

## Decisions, constraints & rationale

- No code additions or removals — deployment is purely config, build, and host setup
- Build outputs static files to `dist` folder
- Host must configure publish directory as `dist` (host defaults are usually wrong)
- Host must enable SPA fallback so unknown routes serve index page (required for OAuth redirect params)
- Deriv OAuth client ID is the single required secret; must be set as build-time environment variable on the host
- Production hostname in brand config must match the final live domain for correct trading server connections
- Brand styles must be generated before running production build

## Open questions & assumptions

- Whether user already has a Deriv OAuth client ID or needs to register one
- Preferred hosting provider (Vercel, Netlify, Cloudflare Pages) — no decision yet
- Whether a custom domain will be used or host's default address is acceptable
- Assumed: dependencies are installable and build runs successfully in current environment