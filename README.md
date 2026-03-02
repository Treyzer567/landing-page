# landing-page

A self-hosted landing page for managing access to a personal media server suite. Serves as a central hub for users to submit support tickets, import playlists, run maintenance scripts, browse FAQs, and navigate to the sign-on portal.

These tools (with the exception of the Sign-On Page) are used through iFrames on Homarr. They can be used directly as their own site or as an iFrame - each one should be fairly flexible.

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

Each backend service has its own repository. See them below for more detail regarding each:

| Service | Repo | Description |
|---------|------|-------------|
| **Playlist Importer** | [playlist-importer](https://github.com/Treyzer567/playlist-importer) | Imports Spotify/YouTube Music playlists into Jellyfin |
| **Script Runner** | [script-runner](https://github.com/Treyzer567/script-runner) | API for triggering and monitoring media mover scripts |
| **Ticket Middleware** | [hesk-middleware](https://github.com/Treyzer567/hesk-middleware) | Node.js proxy that submits tickets to a self-hosted Hesk instance |
| **Sign-On Page** | [sign-on-page](https://github.com/Treyzer567/sign-on-page) | RollCall — user registration portal across all services |

---

## Deployment

This repo contains only the frontend (`pages/` and `assets/`). `backend/` will need to be pulled from each respective repo.

See `landing-compose.yml` for the full Docker Compose setup including all backend services.

To use: download the required files for the tool/page you want to make use of (see releases) > set up the folder structure > update the env variables in the compose > bring up the container (I use Portainer) > navigate to the IP:Port for the main landing-page > enjoy!

Sign-On Page is a bit special. It is primarily used as its own page rather than through an iFrame on Homarr but is accessible for easy use locally. In fact, the password protection is disabled locally as well. Due to this, the landing page actually just links to that service on that port rather than loading the HTML file.

---

## Related Projects

| Repo | Description |
|------|-------------|
| [scripts](https://github.com/Treyzer567/scripts) | Standalone media mover scripts |

---

## External Projects

| Project | Description |
|---------|-------------|
| [Jellyfin](https://github.com/jellyfin/jellyfin) | Open source media server |
| [Homarr](https://github.com/homarr-labs/homarr) | Self-hosted dashboard — where these pages are embedded as iFrames |
| [Hesk](https://www.hesk.com) | Self-hosted helpdesk software — powers the ticket system |
| [RomM](https://github.com/rommapp/romm) | Self-hosted ROM manager |
| [Booklore](https://github.com/booklore-app/booklore) | Self-hosted digital library |
| [Synapse](https://github.com/element-hq/synapse) | Matrix homeserver |
| [Filebrowser Quantum](https://github.com/gtsteffaniak/filebrowser) | Self-hosted web file manager |
| [Immich](https://github.com/immich-app/immich) | Self-hosted photo library |
| [Lidarr](https://github.com/Lidarr/Lidarr) | Music collection manager |
| [Sonarr](https://github.com/Sonarr/Sonarr) | TV series collection manager |
