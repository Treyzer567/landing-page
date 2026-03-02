# landing-page

A self-hosted landing page for managing access to a personal media server suite. Serves as a central hub for users to submit support tickets, import playlists, run maintenance scripts, browse FAQs, and navigate to the sign-on portal.

---

## Pages

| Page | Description |
|------|-------------|
| `index.html` | Home — navigation hub linking to all other pages |
| `ticket-form.html` | Support ticket submission form (via Hesk) |
| `faq.html` | Frequently asked questions |
| `playlist-tool.html` | Spotify/YouTube Music → Jellyfin playlist importer UI |
| `script-control.html` | Manual trigger buttons for server maintenance scripts |
| `coming-soon.html` | Placeholder page for upcoming features |

---

## Backend Repos

Each backend service has its own repository. See them below:

| Service | Repo | Description |
|---------|------|-------------|
| **Playlist Importer** | [playlist-importer](https://github.com/YOUR_USERNAME/playlist-importer) | Imports Spotify/YouTube Music playlists into Jellyfin |
| **Script Runner** | [script-runner](https://github.com/YOUR_USERNAME/script-runner) | API for triggering and monitoring media mover scripts |
| **Ticket Middleware** | [ticket-middleware](https://github.com/YOUR_USERNAME/ticket-middleware) | Node.js proxy that submits tickets to a self-hosted Hesk instance |
| **Sign-On Page** | [sign-on-page](https://github.com/YOUR_USERNAME/sign-on-page) | RollCall — user registration portal across all services |

> Replace `YOUR_USERNAME` with your GitHub username in the links above.

---

## Deployment

This repo contains only the frontend (`pages/` and `assets/`). It is served via an **nginx** Docker container. The nginx startup command injects runtime configuration into `config.js`, which the frontend pages read to locate backend services.

See `landing-compose.yml` for the full Docker Compose setup including all backend services.

### Environment Variables (homarr-pages service)

| Variable | Description |
|----------|-------------|
| `ACCESS_TOKEN` | Hesk API access token |
| `HESK_URL` | Internal URL of your Hesk instance |
| `HESK_MIDDLEWARE_URL` | Internal URL of the ticket middleware service |
| `SIGNON_URL` | Internal URL of the RollCall sign-on frontend |
| `SCRIPT_RUNNER_URL` | Internal URL of the script runner service |
| `PLAYLIST_BACKEND_URL` | Internal URL of the playlist importer backend |

---

## Related Repos

| Repo | Description |
|------|-------------|
| [sign-on-page](https://github.com/YOUR_USERNAME/sign-on-page) | RollCall user registration portal |
| [scripts](https://github.com/YOUR_USERNAME/scripts) | Standalone media mover scripts |
