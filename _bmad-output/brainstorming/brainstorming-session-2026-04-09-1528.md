---
stepsCompleted: [1, 2, 3, 4]
workflow_completed: true
inputDocuments: ["/home/tsvetan/Documents/NASBuddy/docs/IdeasDraft.md"]
session_topic: 'Feature discovery and competitive gap analysis for NASBuddy'
session_goals: 'Uncover missing/overlooked features by surveying the NAS/self-hosted file management landscape before writing the PRD'
selected_approach: 'progressive-flow'
techniques_used: ['Cross-Pollination', 'Mind Mapping', 'SCAMPER Method', 'Constraint Mapping']
ideas_generated: []
context_file: '/home/tsvetan/Documents/NASBuddy/docs/IdeasDraft.md'
---

# Brainstorming Session Results

**Facilitator:** Tsvetan
**Date:** 2026-04-09 15:28

## Session Overview

**Topic:** Feature discovery and competitive gap analysis for NASBuddy
**Goals:** Uncover missing/overlooked features by surveying the NAS/self-hosted file management landscape before writing the PRD

### Context Guidance

NASBuddy is a privacy-first, web-based NAS home server interface built with Java/Spring Boot (backend) and React + TypeScript + Tailwind CSS (frontend). The draft covers 4 phases: Phase 1 (core file browsing + security + image browser), Phase 2 (versioning, favorites, map view, REST API), Phase 3 (AI tools — OCR, face recognition, NLP, vector search), Phase 4 (cloud integrations). Key differentiator: privacy-first with local AI options.

### Session Setup

Competitive gap analysis — what are similar tools already doing that isn't yet in the NASBuddy draft?

## Technique Selection

**Approach:** Progressive Technique Flow
**Journey Design:** Systematic development from competitive landscape exploration to actionable PRD features

**Progressive Techniques:**

- **Phase 1 - Exploration:** Cross-Pollination — survey the competitive ecosystem for feature patterns
- **Phase 2 - Pattern Recognition:** Mind Mapping — organize ideas into categories, identify gaps vs. draft
- **Phase 3 - Development:** SCAMPER Method — refine top gaps into differentiated features
- **Phase 4 - Action Planning:** Constraint Mapping — filter through stack/phasing/privacy-first lens

**Journey Rationale:** Starting broad with cross-pollination against the NAS/self-hosted ecosystem ensures no obvious feature category is missed. Progressive narrowing through pattern recognition and SCAMPER produces PRD-ready, differentiated feature concepts grounded in the existing tech stack and privacy-first principle.

## Phase 1: Expansive Exploration — Cross-Pollination Results

**Technique:** Cross-Pollination (surveying Nextcloud, FileBrowser, Synology DSM, TrueNAS, Jellyfin, PhotoPrism, Immich, Google Drive, Dropbox, OneDrive)
**Ideas Generated:** 26 confirmed across 10 domains

### Scope Constraints Identified

- ❌ WebDAV / SMB / SFTP — handled by external services
- ❌ PWA / dedicated mobile app — out of scope for now
- 📅 Camera auto-backup — future phase when mobile story matures
- ⚠️ Heavy media transcoding — limited focus on content visualization

---

### Confirmed Ideas by Domain

**[Security/Sharing #1]: Shareable Links with Expiry**
_Concept:_ Time-limited, password-optional public links for any file or folder. Recipients need no account. Links expire after N days or a download count threshold.
_Novelty:_ Draft only covers internal permissions. External sharing without account creation is a massive everyday use case.

**[Sharing #33]: Upload-Only Share Links ("File Drop")**
_Concept:_ Share a link that lets recipients upload files into a specific folder without browsing or downloading anything else.
_Novelty:_ Invaluable for collecting files from people who shouldn't see NAS contents — clients, family, colleagues.

---

**[Notifications #2]: Activity Feed & Audit Log**
_Concept:_ Per-user and admin-level activity stream — who uploaded, deleted, accessed a shared link, when. Filterable by user, action type, and date.
_Novelty:_ Draft has permissions but no visibility into what happened. Critical for multi-user households.

---

**[Storage #4]: Disk Usage Visualization**
_Concept:_ Interactive treemap/sunburst chart showing which folders/files consume most space. Click to navigate and bulk-delete directly from the visualization.
_Novelty:_ No existing tool offers interactive drill-down visualization for storage.

---

**[Media #7]: Video Streaming (Lightweight)**
_Concept:_ Stream video files directly in the browser for common formats (MP4, MKV) without full transcoding infrastructure.
_Novelty:_ Even basic browser-native playback removes the download barrier for video files.

**[Media #9]: Document Preview**
_Concept:_ In-browser preview for PDFs, DOCX, XLSX, plain text, Markdown, and code files — no download required.
_Novelty:_ Dramatically reduces friction for everyday document access.

---

**[Upload #19]: Chunked Resumable Uploads**
_Concept:_ Large file uploads survive network drops and browser refreshes — resumes from where it stopped via TUS protocol.
_Novelty:_ Uploading large files over home WiFi is a core NAS use case. Resilience is expected.

**[Upload #20]: Drag & Drop Folder Upload**
_Concept:_ Drag a folder from desktop into the browser and preserve the full directory structure on upload.
_Novelty:_ Most tools only support flat file drag-and-drop. Full folder structure upload via File System API.

**[Upload #21]: Upload Queue with Progress Dashboard**
_Concept:_ Persistent non-blocking upload queue panel showing per-file progress, speed, ETA, and errors.
_Novelty:_ Non-blocking queue allows continued browsing during uploads — significant UX upgrade.

---

**[Search #22]: Saved Searches & Smart Folders**
_Concept:_ Save any search query as a "Smart Folder" showing live results — like smart playlists for the NAS.
_Novelty:_ Makes search a first-class navigation paradigm, not just a one-off tool.

**[Search #23]: Recent Files & Command Palette (Ctrl+K)**
_Concept:_ "Recent" section surfacing last N files accessed/modified. Global Ctrl+K shortcut for fuzzy file name search.
_Novelty:_ Power users in VS Code/Notion live by command palette. Essentially absent from file managers.

**[Search #24]: EXIF / Metadata Search for Images**
_Concept:_ Search images by camera model, ISO, aperture, lens, or GPS coordinates — not just name and date.
_Novelty:_ Game-changer for photography enthusiasts using NAS as photo archive. Aligns with existing image browser plans.

---

**[UX #28]: Keyboard Shortcut System**
_Concept:_ Full keyboard navigation — arrows, Enter, Space preview, Delete, Ctrl+C/V/X, / for search. Discoverable via ? overlay.
_Novelty:_ Almost no web file managers have serious keyboard support.

**[UX #29]: Multi-Panel / Split View**
_Concept:_ Optional dual-pane layout for moving/copying between folders — Norton Commander style.
_Novelty:_ Common in desktop file managers, essentially absent in web ones.

**[UX #30]: Contextual Right-Click Menu**
_Concept:_ Full context menu on files/folders: open, preview, download, rename, move, copy, share, delete, tag.
_Novelty:_ Native-feeling context menu is the single biggest "this feels like a real app" signal.

---

**[A11y #35]: Dark Mode + Theming**
_Concept:_ System-aware dark/light mode toggle persisted per user. Optional accent color selection.
_Novelty:_ Table stakes in 2026 — users notice its absence immediately.

---

**[Deploy #38]: First-Run Setup Wizard**
_Concept:_ Step-by-step wizard on first launch: set admin password → choose storage folders → configure base URL → optional SMTP. Skippable, resumable.
_Novelty:_ The difference between "easy to install" and "actually installed by non-technical users."

---

**[Archive #39]: In-Browser Archive Extraction**
_Concept:_ Right-click a ZIP/TAR.GZ/RAR and extract directly on the server — no download/extract/re-upload cycle.
_Novelty:_ Reverse of existing multi-file ZIP download. Equally expected by users.

**[Archive #40]: Create Archives On-The-Fly**
_Concept:_ Select any files/folders and compress into ZIP or TAR on the server, then download or save in-place.
_Novelty:_ Extends ZIP download into a full server-side compression workflow.

---

**[Image #43]: Timeline / Date-Based View**
_Concept:_ Browse images chronologically in a continuous timeline grouped by year → month → day.
_Novelty:_ Google Photos/Immich nail this. Natural third view mode alongside grid and list.

**[Image #44]: Album / Collection Management**
_Concept:_ Named virtual albums grouping images from any NAS location without moving files. User-specific or shareable.
_Novelty:_ Separates logical organization from physical file location — paradigm shift from pure folder browsing.

**[Image #45]: Slideshow Mode**
_Concept:_ Full-screen slideshow for any folder or album with configurable timing, transitions, keyboard controls.
_Novelty:_ Simple to implement, impressive to demo. Turns NASBuddy into a digital photo frame backend.

---

**[Auth #48]: API Keys / Personal Access Tokens**
_Concept:_ Users generate long-lived API tokens for scripting — rsync wrappers, backup scripts, CI pipelines — without exposing passwords.
_Novelty:_ Essential for the planned Phase 2 REST API to be usable securely.

---

**[Help #49]: Contextual Help & Tooltips**
_Concept:_ Inline help tooltips on complex UI elements. "?" icon opens contextual help panel without leaving the page.
_Novelty:_ Opens NASBuddy to less technical family audiences without compromising power-user experience.

---

### Phase 5/6 Backlog

**[Admin #25]: Storage Quota per User** — Admin sets disk quota per user; uploads blocked when exceeded.
**[Admin #26]: System Health Dashboard** — Admin panel with disk usage, SMART data, CPU/RAM, active connections.

### Ideas Not Confirmed (Available for Later Phases)

- Push notifications [#3], Duplicate file detection [#5], Trash/Recycle Bin [#6], Audio player [#8]
- Inline text/Markdown editor [#14], File comments & @mentions [#15]
- 2FA/TOTP [#16], Session management [#17], Brute-force protection [#18]
- Checksum verification [#31], Lightweight auto-snapshot on overwrite [#32]
- Share link analytics [#34], Multi-language UI [#36], Built-in update checker [#37]
- Email notifications via SMTP [#41], Webhook support [#42]
- LDAP/AD integration [#46], OAuth2/SSO login [#47]
- Demo/sample data mode [#50]

---

## Phase 2: Pattern Recognition — Mind Map

**Technique:** Mind Mapping — organizing confirmed ideas against the existing draft

### Gap Analysis: Draft Coverage vs. New Ideas

**🔴 Entirely absent from draft (new categories):**
- Sharing subsystem — no external sharing at all
- Preview & Media — no in-browser viewing of any kind
- Activity & Monitoring — no audit trail or activity history

**🟡 Partially covered in draft, substantially upgraded:**
- File Browser — upload resilience, folder upload, conflict handling, archive ops all missing
- Search — saved searches, command palette, EXIF search not present
- Image Browser — timeline, albums, slideshow not present
- UX — keyboard shortcuts, right-click menu, split view, dark mode all missing

**🟢 Well covered in draft:**
- Core security (users, permissions, roles)
- Basic file operations (browse, delete, create folder, rename, move, copy)
- Basic search (name, date, tags, content)
- Installation & configuration

### Feature Mind Map

```
NASBuddy
├── Security & Access
│   ├── IN DRAFT: login, users, folder/file permissions, role management
│   └── NEW: API Keys / Personal Access Tokens
├── Sharing (entirely new)
│   ├── NEW: Shareable Links with Expiry
│   └── NEW: Upload-Only File Drop Links
├── File Browser
│   ├── IN DRAFT: browse, upload, download ZIP, delete, create, rename, move, copy, sort, grid/list
│   ├── NEW: Chunked Resumable Uploads (no file size limit)
│   ├── NEW: Drag & Drop Folder Upload
│   ├── NEW: Upload Queue with Progress Dashboard
│   ├── NEW: Upload Conflict Resolution Policy per folder
│   ├── NEW: Archive Extraction in-browser
│   └── NEW: Create Archives On-The-Fly
├── Search & Discovery
│   ├── IN DRAFT: search by name, date range, tags, file contents
│   ├── NEW: Recent Files & Command Palette (Ctrl+K)
│   ├── NEW: Saved Searches & Smart Folders
│   └── NEW: EXIF / Metadata Search for Images
├── Image Browser
│   ├── IN DRAFT: viewer (zoom/pan), search, tags management
│   ├── NEW: Timeline / Date-Based View
│   ├── NEW: Album / Collection Management
│   ├── NEW: Slideshow Mode
│   ├── NEW: Map as fourth view mode (unifies Phase 2 plan)
│   └── NEW: EXIF Sidebar in full-screen viewer
├── Preview & Media (entirely new)
│   ├── NEW: Document Preview (PDF, DOCX, MD — PDF.js)
│   └── NEW: Video Streaming (lightweight browser-native)
├── UX & Interface
│   ├── IN DRAFT: responsive, grid/list view, simple & intuitive
│   ├── NEW: Keyboard Shortcut System + ? overlay
│   ├── NEW: Contextual Right-Click Menu
│   ├── NEW: Multi-Panel / Split View
│   └── NEW: Dark Mode + Theming
├── Activity & Monitoring (entirely new)
│   ├── NEW: Activity Feed & Audit Log
│   └── NEW: Disk Usage Visualization (Phase 2)
├── Admin & Config
│   ├── IN DRAFT: admin selects/hides accessible folders
│   └── NEW: First-Run Setup Wizard
└── Help & Onboarding (entirely new)
    └── NEW: Contextual Help & Tooltips
```

---

## Phase 3: Idea Development — SCAMPER Method

**Focus Areas:** Sharing Subsystem · Upload Experience · Image Browser

### SCAMPER: Sharing Subsystem

**Refined outputs:**

**[SCAMPER-S1]: QR Code for Share Links**
_Concept:_ Generate a QR code alongside any share link — scannable on a phone without typing a URL.
_Novelty:_ Zero extra infrastructure. Massive UX win for in-person sharing with family.

**[SCAMPER-S2]: Unified Share Dialog**
_Concept:_ Single "Share" dialog handles both internal user sharing and external link generation — same UI, same mental model.
_Novelty:_ Eliminates the split between permissions system and sharing system that confuses users in Nextcloud.

**[SCAMPER-S3]: Download-Count Expiry**
_Concept:_ Share links expire after N downloads, not just after N days. "This link expires after 3 downloads."
_Novelty:_ Fine-grained distribution control not available in any major self-hosted tool.

**[SCAMPER-S4]: One-Click Share from File List**
_Concept:_ Single click on hover/right-click copies share link immediately. Full options dialog available but optional.
_Novelty:_ Most users just want the link fast. Progressive disclosure keeps power features accessible without cluttering the default flow.

### SCAMPER: Upload Experience

**Refined outputs:**

**[SCAMPER-U1]: URL/HTTP Import**
_Concept:_ Paste a URL and NASBuddy fetches the file directly server-side to the NAS. No download-then-upload cycle.
_Novelty:_ Fetch a 10GB file from the internet at full server speed. `WebClient` in Spring Boot, trivial to implement.

**[SCAMPER-U2]: Upload Conflict Resolution Policy per Folder**
_Concept:_ Per-folder setting for when a file already exists: Overwrite / Rename with suffix / Skip / Ask. Configurable in folder settings.
_Novelty:_ Prevents a whole class of data loss accidents. "Always rename in /Photos, always overwrite in /Backups."

**[SCAMPER-U3]: Post-Upload Folder Actions**
_Concept:_ Admin-configurable trigger on new file arrival in a folder: generate thumbnails, extract archive, fire a webhook.
_Novelty:_ Turns the upload queue into a lightweight automation pipeline without a full workflow engine.

**[SCAMPER-U4]: No Practical File Size Limit (TUS)**
_Concept:_ TUS chunked protocol eliminates server upload size limits as a user-facing concept entirely.
_Novelty:_ Present as a feature ("upload files of any size"), not an implementation detail.

### SCAMPER: Image Browser

**Refined outputs:**

**[SCAMPER-I1]: Shareable Album Gallery Links**
_Concept:_ Albums are directly shareable as a public or password-protected gallery page. Albums become the atomic unit of both organization and photo sharing.
_Novelty:_ Unifies the sharing subsystem with the image browser. One feature, two systems connected.

**[SCAMPER-I2]: Map as Fourth Image Browser View Mode**
_Concept:_ Map view is a peer tab alongside Grid / List / Timeline — plots all geotagged photos using Leaflet.js + OpenStreetMap. Unifies the Phase 2 map plan as a native browser mode.
_Novelty:_ Treats the map as a navigation paradigm, not a separate page. Privacy-safe (OpenStreetMap, no Google).

**[SCAMPER-I3]: EXIF Sidebar in Full-Screen Viewer**
_Concept:_ While viewing a photo, a collapsible panel shows camera, lens, ISO, shutter, aperture, GPS + mini-map, and all tags.
_Novelty:_ Transforms the passive viewer into an information-rich inspection tool for photographers.

**[SCAMPER-I4]: Background Thumbnail Pre-Generation**
_Concept:_ Thumbnails generated proactively for all images on upload via async Spring Boot job (`Thumbnailator`). Image browser is always instant — no on-demand spinners.
_Novelty:_ Invisible to users but transformative for perceived performance. Foundation for all image browser features.

---

## Phase 4: Action Planning — Constraint Mapping

**Constraints applied:** Java/Spring Boot + React/TypeScript/Tailwind · Privacy-first (no cloud) · MVP-first phasing

### Technical Feasibility Notes

| Feature | Effort | Key Libraries |
|---|---|---|
| Chunked uploads (TUS) | Medium | `tus-java-server`, `tus-js-client` |
| Background thumbnail gen | Medium | `Thumbnailator`, Spring async |
| EXIF extraction | Low | `metadata-extractor` (Java) |
| Archive ops | Low | `Apache Commons Compress` |
| Document preview | Low | `PDF.js` (frontend only, no server) |
| Video streaming | Low | Spring Range requests + native `<video>` |
| Map view | Low | `Leaflet.js` + OpenStreetMap (local) |
| URL/HTTP import | Low | Spring `WebClient` |
| QR code generation | Low | `ZXing` Java or frontend JS |
| Shareable albums | Medium | Extends share link model |
| Command palette | Low | `cmdk` React library |
| Smart Folders | Medium | Saved query + live DB filter |
| EXIF metadata search | Medium-High | Indexed metadata schema required |

**Privacy compliance:** All features pass — no Google APIs, no cloud services, fully self-hosted. Map uses OpenStreetMap/Leaflet. Document preview runs entirely in the browser via PDF.js.

### Final Phase Assignment

#### 🟢 Phase 1 — Core MVP (17 new features added to draft)

*Sequencing note: Background thumbnail pre-generation and EXIF extraction must ship in Phase 1 as invisible infrastructure — they underpin Phase 2's Timeline, Albums, Map, and EXIF Search without rework.*

**Sharing subsystem (entirely new):**
- Shareable Links with Expiry + Download-count limit
- Upload-Only File Drop Links
- Unified Share Dialog + One-click share + QR code generation

**Upload experience upgrades:**
- Chunked Resumable Uploads (no practical file size limit)
- Drag & Drop Folder Upload (with directory structure)
- Upload Queue with Progress Dashboard (non-blocking)
- Upload Conflict Resolution Policy per folder

**File Browser additions:**
- Archive Extraction in-browser
- Create Archives On-The-Fly

**Search & Discovery:**
- Recent Files & Command Palette (Ctrl+K)

**Preview & Media:**
- Document Preview (PDF, DOCX, Markdown — PDF.js, zero server effort)

**UX & Interface:**
- Contextual Right-Click Menu
- Keyboard Shortcut System + ? overlay
- Dark Mode + Theming

**Image Browser infrastructure:**
- Background Thumbnail Pre-generation (async, invisible)
- EXIF Sidebar in Full-Screen Viewer

**Admin & Onboarding:**
- First-Run Setup Wizard
- Contextual Help & Tooltips

**Activity:**
- Activity Feed & Audit Log

#### 🔵 Phase 2 — Enhancements (12 features, builds on Phase 1 infrastructure)

- Timeline / Date-Based Image View
- Album / Collection Management
- Shareable Album Gallery Links
- Map as Image Browser View Mode (Leaflet.js + OpenStreetMap)
- EXIF / Metadata Search for Images
- Saved Searches & Smart Folders
- Multi-Panel / Split View
- Video Streaming (lightweight, browser-native)
- Disk Usage Visualization
- URL/HTTP Import
- Post-Upload Folder Actions (automation hooks)
- API Keys / Personal Access Tokens (pairs with Phase 2 REST API)
- Slideshow Mode

#### 🟡 Phase 3 — AI & Advanced
- System-suggested tags (EXIF + AI results)

#### 🔮 Phase 5/6 — Operational
- Storage Quota per User
- System Health Dashboard

---

## Session Summary and Insights

**Session Achievement:**
- **26 confirmed new features** identified across 10 domains
- **12 SCAMPER refinements** produced from 3 focus areas
- **0 cloud dependencies** — all features are privacy-safe
- **Clear phase roadmap** from MVP through advanced features

**Key Breakthroughs:**

- **Sharing is the biggest gap** — entirely absent from the draft, yet one of the most expected capabilities. A complete sharing subsystem (links, file drops, QR codes, album galleries) emerged as a coherent Phase 1 subsystem.
- **Upload resilience is table stakes** — TUS chunked uploads + conflict resolution + non-blocking queue form a cohesive upload experience that most tools get wrong.
- **Image Browser has a clear completion arc** — Phase 1 lays the invisible infrastructure (thumbnails + EXIF), Phase 2 delivers the full experience (Timeline, Albums, Map, Slideshow).
- **One critical sequencing insight** — background thumbnail pre-generation and EXIF extraction in Phase 1 are the hidden foundation that makes Phase 2 image features possible without rework.

**Scope boundaries confirmed:**
- ❌ WebDAV/SMB/SFTP — external services handle this
- ❌ PWA / mobile app — future consideration
- ❌ Heavy video transcoding — browser-native playback only
- 📅 Camera auto-backup — future mobile phase

**Recommended next step:** Use this session document as the primary context input for `bmad-create-prd`. The phase assignment table maps directly to PRD epic structure.

