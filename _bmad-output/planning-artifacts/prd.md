---
stepsCompleted: ['step-01-init', 'step-02-discovery', 'step-02b-vision', 'step-02c-executive-summary', 'step-03-success', 'step-04-journeys', 'step-05-domain', 'step-06-innovation', 'step-07-project-type', 'step-08-scoping', 'step-09-functional', 'step-10-nonfunctional', 'step-11-polish', 'step-12-complete']
workflowStatus: complete
completedAt: '2026-04-09'
inputDocuments:
  - /home/tsvetan/Documents/NASBuddy/docs/IdeasDraft.md
  - /home/tsvetan/Documents/NASBuddy/_bmad-output/brainstorming/brainstorming-session-2026-04-09-1528.md
workflowType: 'prd'
briefCount: 0
researchCount: 0
brainstormingCount: 1
projectDocsCount: 1
classification:
  projectType: web_app
  domain: general
  complexity: low
  projectContext: greenfield
---

# Product Requirements Document - NASBuddy

**Author:** Tsvetan
**Date:** 2026-04-09

## Executive Summary

NASBuddy is a privacy-first, web-based file management interface for home NAS servers. It targets self-hosters who have the technical ability to run a service, but demand a product that works beautifully out of the box — for themselves and for non-technical family members sharing the same system. Default settings produce a complete, production-quality experience; advanced configuration is available for those who want it, never required.

The problem NASBuddy solves is a false choice: today, home NAS users either accept the friction and complexity of raw self-hosted tools (TrueNAS, Samba/NFS, Nextcloud), or surrender data ownership to cloud services (Google Drive, Google Photos, Dropbox). NASBuddy eliminates that trade-off — delivering the polish and completeness of a cloud product, running entirely on hardware the user owns.

**One-liner:** *"Google Drive, but yours."*

### What Makes This Special

The core differentiator is UX parity with cloud services, achieved without any cloud dependency. Three specific gaps in the self-hosted landscape drive NASBuddy's early differentiation:

1. **Sharing subsystem** — entirely absent from all major self-hosted file managers; NASBuddy ships time-limited links, file-drop uploads, and QR codes in Phase 1; shareable album galleries follow in Phase 2.
2. **Upload resilience** — chunked resumable uploads (TUS protocol), folder drag-and-drop, and a non-blocking upload queue handle the large-file NAS use case that cloud tools solve but self-hosted tools routinely drop.
3. **Image browser completeness** — a full photo management experience (timeline, albums, slideshow, map, EXIF) built privacy-safe on OpenStreetMap and local thumbnail generation, with no Google Photos dependency.

All AI features are disabled by default and designed to run entirely on local hardware. Cloud AI models are optionally supported for users who opt in — never as a requirement.

## Project Classification

- **Project Type:** Web Application (React SPA + Spring Boot REST API)
- **Domain:** General / Home Self-Hosting
- **Complexity:** Low — standard security, UX, and performance concerns; no regulated industry requirements
- **Project Context:** Greenfield — new product built from scratch
- **Tech Stack:** Java 25 LTS / Spring Boot (backend), React + TypeScript + Tailwind CSS (frontend), Docker-managed dependencies

## Success Criteria

### User Success

- A non-technical family member completes core tasks (upload, download, search, browse photos, share a file) without asking for help.
- First-time setup — from download to first successful login — takes under 15 minutes on a standard home server.
- The photo library is fully browsable, searchable, and shareable from any device without downloading files locally.
- Files of any size upload reliably over home WiFi without manual retry.

### Business Success

NASBuddy is an open-source personal tool. Success is measured by personal adoption and community reach, not revenue:

- **6-month primary target:** A stable personal install that is actively and frequently used as the primary interface for the home NAS.
- **6-month stretch target:** At least one friend or acquaintance has successfully self-installed NASBuddy and is actively testing or using it — validating that the install experience works for people outside the author.
- **Indicator of failure:** The install requires repeated manual intervention, workarounds, or documentation lookups to maintain.

### Technical Success

- Single-command install (JAR or Docker Compose) with no manual dependency configuration required.
- All features covered by unit tests; no feature ships without test coverage.
- UI is responsive and performant across mobile, tablet, and desktop — pages load in under 2 seconds on a local network.
- Zero required cloud services — the application runs fully air-gapped if needed.
- Configuration via environment variables or a single external config file; sensible defaults require no customization for standard use.

### Measurable Outcomes

| Outcome | Target |
|---|---|
| Setup time (download → first login) | < 15 minutes |
| Core task completion by non-technical user | No external help required |
| Page load time (local network) | < 2 seconds |
| Unit test coverage | All features covered |
| Personal daily/weekly active use | Sustained at 6 months |
| External installs by friends | ≥ 1 successful install at 6 months |

## Product Scope

### MVP — Phase 1

Core file browsing and security (login, users, roles, folder/file permissions), full sharing subsystem (time-limited links, file-drop uploads, QR codes, unified share dialog), upload resilience (TUS chunked uploads, folder drag-and-drop, upload queue), archive operations (extract and create), document preview (PDF, DOCX, Markdown), image browser foundation (viewer with zoom/pan, tags, EXIF sidebar, background thumbnail pre-generation), search (name, date, tags, content, command palette), contextual right-click menu, keyboard shortcut system, dark mode, first-run setup wizard, activity feed and audit log, contextual help.

### Growth Features — Phase 2

File versioning, favorites, image timeline and album management, shareable album galleries, map view (OpenStreetMap/Leaflet), EXIF/metadata search, saved searches and smart folders, multi-panel split view, video streaming (browser-native), disk usage visualization, URL/HTTP import, post-upload folder actions, API keys / personal access tokens, full REST API, slideshow mode.

### Vision — Phase 3+

AI tools (OCR, image recognition, face recognition with known-faces repository, NLP text processing, vector search, natural language file search), cloud integrations (Google Photos, Dropbox, and other storage services), storage quotas per user, system health dashboard, camera auto-backup (when mobile story matures).

## User Journeys

### Journey 1: Tsvetan Sets Up NASBuddy and Invites His Family

**Persona:** Tsvetan, 34, software developer. He's been running a bare TrueNAS install for two years. His wife asks him every few weeks to find a photo from a family trip — he SSHes in, rsyncs, sends a file over Telegram. It works, but it's embarrassing that it takes 20 minutes.

**Opening Scene:** Tsvetan downloads the NASBuddy Docker Compose file on a Saturday afternoon. He runs `docker compose up`. The first-run setup wizard opens in his browser. He sets an admin password, selects two folders (`/photos` and `/family-docs`) to expose, sets the base URL, and clicks Finish. Total time: 11 minutes.

**Rising Action:** He creates two user accounts — one for his wife, one for his teenage son. He grants his wife read/write access to `/photos` and read-only to `/family-docs`. He sets his son to read-only on both. He sends them each a signup link.

**Climax:** His wife logs in on her phone. She finds the folder "Summer 2024" in under 30 seconds, without asking Tsvetan anything. She selects 12 photos and shares them with her sister via a time-limited link — no account required on the sister's end.

**Resolution:** Tsvetan's NAS stops being a personal tool and becomes a shared family resource. The 20-minute SSH ritual is gone. He checks the activity feed the next morning and sees his wife uploaded 40 new photos from her phone.

*Capabilities revealed: first-run wizard, user management, folder permissions, mobile-responsive UI, photo browsing, multi-select download, share links.*

---

### Journey 2: His Wife Recovers from a Botched Upload

**Persona:** Marta, 36, teacher. Not technical. She's uploading 800 photos from a school event — a 4.2 GB folder drag-and-drop. Halfway through, her home WiFi drops for 90 seconds.

**Opening Scene:** The upload queue panel shows a pause icon and an amber status. Marta doesn't know what happened. She waits.

**Rising Action:** WiFi reconnects. The upload queue resumes automatically from where it stopped. No files are duplicated; no files are lost. The progress dashboard shows "Resuming — 412 of 800 files, 47% complete."

**Climax:** Marta didn't have to do anything. The upload finishes. She sees all 800 photos in the image browser, already thumbnailed.

**Resolution:** Marta trusts the system. She never worries about upload reliability again. Next time she drags in a folder, she doesn't watch it — she makes coffee.

*Capabilities revealed: TUS chunked resumable uploads, upload queue with per-file progress, automatic resume, drag-and-drop folder upload, background thumbnail generation.*

---

### Journey 3: A Friend Drops Off Documents via File Drop Link

**Persona:** Dani, freelance graphic designer. Tsvetan needs raw project files from Dani — 3.8 GB of assets. Dani has no NASBuddy account and shouldn't need one.

**Opening Scene:** Tsvetan right-clicks the `/incoming` folder, selects "Share," and switches the dialog to "File Drop." He sets an expiry of 7 days and copies the link. He pastes it into a message to Dani.

**Rising Action:** Dani opens the link in her browser. She sees a simple upload page: the folder name, an expiry notice, and a drop zone. No login prompt, no account creation.

**Climax:** Dani drags her 3.8 GB asset folder onto the drop zone. The upload progress shows per-file status. She closes the browser when done.

**Resolution:** Tsvetan's activity feed shows "Dani (anonymous) uploaded 47 files via file drop link." The files are in `/incoming`, thumbnailed and ready. The link has expired per schedule.

*Capabilities revealed: upload-only file drop links, link expiry, anonymous upload without account, activity feed showing link usage.*

---

### Journey 4: Tsvetan Investigates a Suspicious Deletion

**Persona:** Tsvetan, admin. He notices a folder is missing that he didn't delete. He suspects his son accidentally deleted it.

**Opening Scene:** Tsvetan opens the Activity Feed and filters by action type "Delete" and date range "last 7 days."

**Rising Action:** He sees: "Lukas deleted /family-docs/Insurance/ — 2026-04-07 21:14." He confirms it was his son.

**Climax:** He checks file versioning (Phase 2) — not yet available, but the activity log gives him the timestamp and user. He checks if the files exist in any backup.

**Resolution:** Tsvetan uses the audit log to understand what happened and have a conversation with his son. He then adds a note to his backlog: enable versioning on `/family-docs` in the next release.

*Capabilities revealed: activity feed, audit log, filter by user/action/date, per-folder permissions, admin oversight.*

---

### Journey 5: The Power User Finds a Document Fast

**Persona:** Tsvetan, using NASBuddy as a daily driver. He remembers scanning a tax document last March but can't recall the filename.

**Opening Scene:** He presses `Ctrl+K`. The command palette opens. He types "tax 2024." Results appear instantly, fuzzy-matched against file names.

**Rising Action:** He clicks the result. A PDF preview opens in-browser — no download. He finds the page he needs.

**Climax:** Total time from remembering the document to reading it: 12 seconds.

**Resolution:** Tsvetan stops thinking of the NAS as "where files live" and starts thinking of it as "where I find things." The command palette becomes a daily habit.

*Capabilities revealed: command palette (Ctrl+K), fuzzy file name search, recent files, in-browser document preview (PDF.js), keyboard navigation.*

---

### Journey Requirements Summary

| Capability Area | Revealed By |
|---|---|
| First-run setup wizard | Journey 1 |
| User management and folder permissions | Journey 1 |
| Mobile-responsive photo browsing | Journey 1 |
| Time-limited share links with QR code | Journey 1 |
| TUS chunked resumable uploads | Journey 2 |
| Upload queue with progress dashboard | Journey 2 |
| Drag-and-drop folder upload | Journey 2 |
| Background thumbnail pre-generation | Journey 2 |
| Upload-only file drop links | Journey 3 |
| Anonymous upload (no account) | Journey 3 |
| Activity feed and audit log | Journeys 3 + 4 |
| Admin filter/search in activity log | Journey 4 |
| Command palette (Ctrl+K) | Journey 5 |
| In-browser document preview | Journey 5 |
| Keyboard navigation | Journey 5 |

## Web App Specific Requirements

### Project-Type Overview

NASBuddy is a React SPA served by a Spring Boot backend. The frontend is bundled and served directly from the JAR — no separate static file server. The app is always authenticated; the only unauthenticated surfaces are the share link and file drop pages, which are lightweight server-rendered HTML pages outside the SPA shell. These pages include Open Graph tags for link previews; no public search indexing is required.

### Browser Matrix

| Browser | Minimum Version | Notes |
|---|---|---|
| Chrome / Chromium | Last 2 major releases | Primary target |
| Firefox | Last 2 major releases | Full support |
| Safari | Last 2 major releases | iOS/iPad primary mobile browser |
| Edge | Last 2 major releases | Chromium-based, covered by Chrome parity |

No legacy browser support. File System API (folder drag-and-drop) and native `<video>` streaming require modern browser support — a conscious constraint for a self-hosted tool where users control their environment.

### Responsive Design

- **Mobile:** Full feature access on phone-sized screens; bottom navigation or hamburger menu; touch-friendly tap targets (min 44px)
- **Tablet:** Optimised grid layout for image browser; sidebar visible on landscape
- **Desktop:** Full layout with sidebar navigation, split-pane option (Phase 2), keyboard shortcut system

File browser and image browser are fully functional on mobile — not degraded to view-only. Upload from mobile browser must work.

### Real-Time Communication

**Server-Sent Events (SSE)** over HTTP/1.1 — one-way server→client push. Used for upload queue progress (per-file %, speed, ETA, errors), activity feed live updates, and share link usage notifications. Spring Boot `SseEmitter` handles SSE natively; no WebSocket infrastructure required. Clients reconnect automatically on disconnect.

### Keyboard & Accessibility

Full keyboard navigation: arrows, Enter, Space (preview), Delete, Ctrl+C/V/X, `/` for search focus, `Ctrl+K` for command palette. `?` overlay documents all shortcuts. Formal accessibility requirements: NFR18–NFR20.

### Implementation Notes

- Frontend bundle served from Spring Boot static resources — no CDN, no external runtime asset dependencies
- Dark/light theme via CSS custom properties; OS preference respected by default, per-user override persisted in backend
- Share link and file drop pages are server-rendered and functional without JavaScript for maximum recipient compatibility

## Project Scoping & Phased Development

### MVP Strategy & Philosophy

**MVP Approach:** Experience MVP — the product must reach a quality bar where it actively replaces the existing workflow (SSH + rsync + manual file sharing), not merely demonstrate a concept. A minimal file browser that doesn't handle real NAS use cases (large uploads, family sharing, photo browsing) would not achieve the 6-month success target.

**Resource Requirements:** Solo developer with Java/Spring Boot + React/TypeScript/Tailwind skills. No date pressure — milestone-driven delivery.

**Sequencing principle:** Ship a working personal install as early as possible (Phase 1a), then build to full Phase 1 completeness (Phase 1b). Each phase produces a usable product, not a partial one.

---

### Phase 1a — Core Daily Driver

*Goal: Replace SSH/rsync as the primary NAS interface for the developer.*

**Core User Journeys Supported:** Journey 1 (partial — setup + family access), Journey 5 (power user finds files fast)

**Must-Have Capabilities:**
- Authentication: login, user management, roles
- Folder/file permissions (read, write, delete; subfolder inheritance)
- File browser: browse, upload, download (multi-file ZIP), delete, create folder, rename, move, copy, sort, grid/list view
- Image browser: viewer (zoom/pan), tag management, background thumbnail pre-generation
- Basic search: name, date range, tags
- First-run setup wizard
- Admin: select/hide accessible folders
- Responsive UI (mobile, tablet, desktop)
- Dark mode + theming

---

### Phase 1b — Experience Completeness

*Goal: Extend to full family use and external sharing. Validate with friends.*

**Must-Have Capabilities:**
- Sharing subsystem: time-limited links with expiry + download-count limit, upload-only file drop links, unified share dialog, one-click share, QR code generation
- Upload resilience: TUS chunked resumable uploads, drag-and-drop folder upload (with directory structure), upload queue with progress dashboard (SSE-powered), upload conflict resolution policy per folder
- Archive operations: in-browser extraction, create archives on-the-fly
- Document preview: PDF, DOCX, Markdown (PDF.js, browser-side only)
- EXIF extraction + EXIF sidebar in full-screen image viewer (infrastructure for Phase 2 image features)
- Search: content-based search (grep), command palette (Ctrl+K)
- Contextual right-click menu
- Keyboard shortcut system + `?` overlay
- Activity feed and audit log (filterable by user, action, date)
- Contextual help and tooltips

---

### Phase 2 — Growth Enhancements

*Goal: Full image management experience + power user features + REST API.*

File versioning, favorites, image timeline and album management, shareable album galleries, map view (OpenStreetMap/Leaflet), EXIF/metadata search, saved searches and smart folders, multi-panel split view, video streaming (browser-native), disk usage visualization, URL/HTTP import, post-upload folder actions, API keys / personal access tokens, full REST API, slideshow mode.

---

### Phase 3+ — Vision

*Goal: AI-powered features and cloud integrations.*

AI tools (OCR, image recognition, face recognition with known-faces repository, NLP text processing, vector search, natural language file search), cloud integrations, storage quotas per user, system health dashboard, camera auto-backup.

---

### Risk Mitigation Strategy

**Technical Risks:**
- *TUS chunked upload* is the most complex single implementation piece — mitigated by `tus-java-server` (battle-tested library) and deferring to Phase 1b.
- *Background thumbnail generation at scale* — mitigated by `Thumbnailator` + Spring async job; tested early in Phase 1a with the image browser.
- *SSE connection stability on home networks* — mitigated by automatic client reconnect; acceptable degradation is polling fallback.

**Scope Risks:**
- The brainstorming session identified 26+ confirmed features plus a long backlog. Strict phase gates (Phase 1a → 1b → 2) prevent backlog items from creeping into active development.
- "Not confirmed" features (2FA, trash/recycle bin, inline editor, push notifications) are explicitly deferred to future consideration.

**Resource Risks:**
- Solo developer with no date pressure — primary risk is momentum loss between milestones. Mitigation: Phase 1a ships a real personal install quickly, creating daily-use feedback that drives continued development. Phase 1b completion is validated by sharing with friends.
- If Phase 1b proves too large, archive operations and activity feed are the first candidates to defer to Phase 2 without breaking core value.

## Functional Requirements

### Authentication & Access Control

- **FR1:** Users can authenticate to NASBuddy using a username and password.
- **FR2:** Authenticated users can change their own password.
- **FR3:** Admin users can create, edit, and deactivate user accounts.
- **FR4:** Admin users can assign roles (admin, standard user) to accounts.
- **FR5:** Admin users can grant read, write, and delete permissions on specific folders and files to individual users.
- **FR6:** Subfolder permissions inherit from their parent folder and can be overridden at the subfolder level.
- **FR7:** Unauthenticated users can access share links and file drop pages without creating an account.
- **FR8:** *(Phase 2)* Users can generate personal access tokens for scriptable API access without exposing passwords.

### File Management

- **FR9:** Users can browse folders and files they have permission to access.
- **FR10:** Users can view files and folders in grid or list view.
- **FR11:** Users can sort files and folders by name, date modified, and size.
- **FR12:** Users can create new folders.
- **FR13:** Users can rename files and folders.
- **FR14:** Users can move files and folders to a different location.
- **FR15:** Users can copy files and folders.
- **FR16:** Users can delete files and folders they have delete permission on.
- **FR17:** Users can add, edit, and delete tags on files and folders.
- **FR18:** Users can access a contextual right-click menu with all available operations for any file or folder.
- **FR19:** Users can navigate and operate the file browser using keyboard shortcuts; available shortcuts are discoverable via an overlay.
- **FR20:** *(Phase 2)* Users can maintain a favorites list of files and folders for quick access.
- **FR21:** *(Phase 2)* Users can enable versioning on files or folders and revert to previous versions.
- **FR68:** *(Phase 2)* Users can view and manage files across two folder locations simultaneously in a split-pane dual-panel layout.

### File Transfer & Upload

- **FR22:** Users can upload files to folders they have write permission on.
- **FR23:** Users can upload folders preserving the full directory structure.
- **FR24:** File uploads resume automatically after network interruption without data loss or duplication.
- **FR25:** Users can monitor upload progress through a non-blocking upload queue panel showing per-file status, speed, ETA, and errors.
- **FR26:** Users can download multiple selected files as a single ZIP archive.
- **FR27:** Admin users can configure the upload conflict resolution policy per folder (overwrite, rename with suffix, skip, or prompt).
- **FR28:** Users can extract archive files directly on the server without downloading.
- **FR29:** Users can compress selected files and folders into an archive on the server.
- **FR30:** *(Phase 2)* Users can import a file from a remote URL directly to the server.
- **FR31:** *(Phase 2)* Admin users can configure automated actions triggered by new file arrivals in a folder.

### Sharing

- **FR32:** Users can generate time-limited share links for any file or folder; links expire by date, download count, or both.
- **FR33:** Users can generate upload-only file drop links allowing anonymous uploads into a folder without NAS browsing access.
- **FR34:** Users can generate a QR code for any share link.
- **FR35:** Users can view and revoke all active share links they have created.
- **FR36:** *(Phase 2)* Users can share image albums as public or password-protected gallery pages.

### Search & Discovery

- **FR37:** Users can search files and folders by name, date range, and tags.
- **FR38:** Users can search files by text content using system-native search tools.
- **FR39:** Users can access a command palette for fuzzy file name search and recent files.
- **FR40:** Users can view a list of recently accessed or modified files.
- **FR41:** *(Phase 2)* Users can search images by EXIF metadata including camera model, ISO, aperture, and GPS coordinates.
- **FR42:** *(Phase 2)* Users can save search queries as smart folders that display live results.

### Media & Preview

- **FR43:** Users can view image files in a full-screen viewer with zoom and pan controls.
- **FR44:** Users can view EXIF metadata for any image in a collapsible panel within the full-screen viewer.
- **FR45:** The system generates thumbnails for all images automatically on upload.
- **FR46:** Users can preview PDF, DOCX, and Markdown files in the browser without downloading.
- **FR47:** *(Phase 2)* Users can play video files in the browser for supported formats without transcoding.
- **FR48:** *(Phase 2)* Users can browse images in a timeline view grouped chronologically by year, month, and day.
- **FR49:** *(Phase 2)* Users can create and manage named virtual albums grouping images from any NAS location without moving files.
- **FR50:** *(Phase 2)* Users can view a slideshow of any folder or album.
- **FR51:** *(Phase 2)* Users can view geotagged images plotted on a map.

### Administration & Configuration

- **FR52:** Admin users can complete initial system setup through a guided first-run wizard.
- **FR53:** Admin users can select which NAS folders are accessible through NASBuddy and hide specific folders from the file browser.
- **FR54:** Users can switch between light and dark themes; the system respects OS-level preference by default with per-user override.
- **FR55:** Users can view an activity feed showing file and folder operations, share link usage, and user actions.
- **FR56:** Admin users can filter the activity log by user, action type, and date range.
- **FR57:** The application provides contextual help tooltips on complex UI elements.
- **FR58:** *(Phase 2)* Admin users can view disk usage through an interactive storage visualization.
- **FR59:** *(Phase 2)* The system exposes a REST API for file and folder management usable by external applications.
- **FR69:** *(Phase 3)* Admin users can set disk quota limits per user; uploads are blocked when a user's quota is exceeded.
- **FR70:** *(Phase 3+)* Admin users can monitor system health including disk status, CPU and RAM usage, and active connections through a dedicated dashboard.

### AI Processing *(Phase 3)*

- **FR60:** Admin users can enable AI-powered image recognition that automatically generates tags based on image content.
- **FR61:** The system identifies faces in images; users can associate faces with names and build a known-faces repository.
- **FR62:** Users can filter images by identified faces.
- **FR63:** Admin users can enable NLP processing of text files that automatically generates tags based on content.
- **FR64:** Users can search files using natural language queries.
- **FR65:** Admin users can configure which folders are processed by AI tools.
- **FR66:** Admin users can configure connections to local AI models and supported cloud AI providers.

### Cloud Integrations *(Phase 4)*

- **FR67:** Admin users can configure integrations with third-party cloud storage services to sync or import content.

## Non-Functional Requirements

### Performance

- **NFR1:** All authenticated page loads complete within 2 seconds on a local network connection.
- **NFR2:** File list renders within 500ms for up to 1,000 items in view.
- **NFR3:** Image thumbnails load within 1 second; thumbnails are pre-generated at upload time and served from local disk.
- **NFR4:** Name and tag search results return within 300ms.
- **NFR5:** Upload throughput is bounded only by available network speed; no artificial server-side cap is imposed.
- **NFR6:** Upload processing runs in the background and does not block UI interaction.

### Security

- **NFR7:** All client-server communication uses HTTPS.
- **NFR8:** Passwords are stored using a strong adaptive hashing algorithm (bcrypt or Argon2).
- **NFR9:** Session tokens are HTTP-only, Secure cookies with configurable expiry.
- **NFR10:** File and folder access permissions are enforced server-side on every request; client-side permission state is for UX rendering only.
- **NFR11:** Share link tokens are cryptographically random and not guessable by enumeration.
- **NFR12:** File drop links enforce upload-only access; recipients cannot browse, list, or download folder contents.
- **NFR13:** The application exposes no unauthenticated endpoints except the login endpoint, share link pages, and file drop pages.

### Reliability

- **NFR14:** The application starts cleanly after an unexpected shutdown without manual intervention or data corruption.
- **NFR15:** File operations (upload, copy, move, delete) are atomic where possible; partial failures leave the system in a consistent, recoverable state.
- **NFR16:** SSE connections reconnect automatically after network interruption without requiring user action.
- **NFR17:** Resumable upload state (TUS) persists across server restarts; in-progress uploads can resume after a reboot.

### Accessibility

- **NFR18:** The UI meets WCAG 2.1 AA colour contrast ratios in both light and dark themes.
- **NFR19:** All interactive elements are reachable and operable via keyboard alone.
- **NFR20:** Core navigation and interactive elements include appropriate ARIA roles and labels for screen reader compatibility.

### Privacy

- **NFR21:** The application makes no outbound network requests to third-party services at runtime, except when explicitly configured by an admin (cloud AI, integrations).
- **NFR22:** Map features use OpenStreetMap tiles via a configurable tile server; no Google APIs are used.
- **NFR23:** No telemetry, analytics, crash reporting, or usage data is collected or transmitted.
- **NFR24:** The application is fully functional without any internet connectivity (air-gapped install).

### Installability & Maintainability

- **NFR25:** The application can be installed and running from a fresh system using a single command (Docker Compose or JAR execution).
- **NFR26:** All required dependencies are bundled or managed automatically; no manual dependency installation is required from the user.
- **NFR27:** All configuration is available via environment variables or a single external config file; all settings have sensible defaults requiring no customisation for standard use.
- **NFR28:** The application is distributed as a single artifact (JAR or Docker image) containing the frontend, backend, and all bundled dependencies.
- **NFR29:** All product features are covered by automated tests; no feature ships without test coverage.
- **NFR30:** Database schema migrations run automatically on startup; upgrades require no manual migration steps from the user.

