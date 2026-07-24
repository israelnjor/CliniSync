https://israelnjor.github.io/CliniSync/

# CliniSync

**AI-powered diagnostic navigation & care coordination platform**
Imperial Global Challenge Lab 2026 · Track 2: Health & Technology

CliniSync is a patient-first coordination layer that sits on top of existing healthcare providers — aggregating medical history, generating AI-powered clinical summaries, and helping patients (and eventually clinicians) navigate fragmented care journeys without replacing any existing EHR system.

This repository contains the **interactive front-end prototype**: a single-file, responsive HTML/CSS/JS mock-up of the patient-facing experience, built to demonstrate the product vision for the Challenge Lab submission.

---

## 🔗 Live prototype

Open [`clinisync-prototype.html`]((https://israelnjor.github.io/CliniSync/ ) directly in any browser, or deploy the `/prototype` folder to Firebase Hosting / Vercel / GitHub Pages for a shareable link.

No build step, no dependencies — it's a single static file.

---

## ✨ What's in the prototype

| Screen | What it shows |
|---|---|
| **Home** | AI-generated plain-language summary of the last visit, next appointment with AI-suggested prep questions, and daily medication reminders |
| **Timeline** | A unified "care thread" pulling consultations, lab results, and prescriptions from multiple independent providers into one chronological view, with category filters and inline AI pattern/observation cards |
| **Trends** | Lab value charts (HbA1c, LDL cholesterol) over time, each with a plain-language AI interpretation panel |
| **Symptom diary** | Patient-logged symptom entries with severity tracking, feeding into the trends and AI pattern detection |
| **Emergency ID** | A QR-based digital health passport showing critical info (allergies, conditions, medications, emergency contact) for use in emergencies |
| **CliniSync Assistant** | A floating, self-inviting AI chatbot (top-right) for plain-language Q&A about the patient's own record |
| **CliniSync Band** *(vision preview)* | A non-functional concept section illustrating a future connected wearable — clearly marked as roadmap, not a shipped feature |

The prototype is fully responsive: a mobile app-style layout with bottom tab navigation below ~1024px, and a sidebar + multi-column desktop layout above it.

---

## 🧠 AI behaviour in this prototype

The **CliniSync Assistant** is wired two ways so the demo never breaks:

1. If a live Anthropic API key is available in the environment, it calls the Claude API directly with a system prompt containing the demo patient's record and strict guardrails (no diagnosis, no medication changes, always defer clinical decisions to the care team).
2. If no live API is reachable (e.g. hosted as a static file with no backend), it falls back to a **scripted, context-aware response engine** that tracks the current conversation topic so follow-ups like *"why"* or *"how"* stay coherent rather than repeating a generic answer.

**This is a prototype, not the production AI implementation.** In production, all AI calls must be routed through a backend function (never the browser) so API keys are never exposed client-side. See [Roadmap](#-roadmap) below.

The assistant, and every AI-generated card in the app, carries a visible disclaimer: *CliniSync explains and organizes — it does not diagnose or replace your care team.*

---

## 🛠 Tech stack — prototype vs. production

| | Prototype (this repo) | Planned production stack |
|---|---|---|
| Frontend | Static HTML / CSS / vanilla JS | React + Tailwind CSS |
| Data | Hardcoded demo patient (Ama Owusu) | PostgreSQL via Supabase, FHIR-aligned schema |
| Auth | None (demo only) | Supabase Auth → NHS Login (future) |
| AI | Direct/fallback client-side call | Server-side Edge Function, key never exposed |
| Hosting | Any static host | Vercel / Firebase Hosting, UK region for data residency |

The production architecture is designed so this migration is additive, not a rewrite — see the [Roadmap](#-roadmap) for the phased plan, including the longer-term move toward a FHIR-native backend (e.g. Medplum or HAPI FHIR) for NHS integration.

---

## 🚀 Running locally

No installation required:

```bash
git clone https://github.com/<your-org>/clinisync.git
cd clinisync
open clinisync-prototype.html   # macOS
# or just double-click the file in Finder/Explorer
```

To serve it (recommended for testing on a phone over local Wi-Fi):

```bash
npx serve .
```

---

## 🗺 Roadmap

**Phase 1 — MVP (Year 1)**
Patient-only app. No institutional integration required. Upload documents, get AI summaries, generate pre-appointment briefs.

**Phase 2 — Institutional integration (Year 2–3)**
NHS FHIR API integration via the NHS Innovation Accelerator pathway. Clinician-facing views. Hospital SaaS licensing.

**Phase 3 — Global & data (Year 4–5)**
International expansion (West Africa, Middle East). Consented, anonymised research data licensing.

Full compliance roadmap (ICO registration, DPIA, DSPT, DTAC, DCB0129 clinical safety) is tracked separately in the project's business & governance documentation.

---

## ⚠️ Disclaimer

This is a **student challenge prototype**, not a certified medical device or a live clinical product. It does not store real patient data, is not connected to any live healthcare system, and must not be used to make real clinical decisions. All patient data shown (Ama Owusu) is fictional demo data.

---

## 👥 Team

Imperial Global Challenge Lab 2026 · Track 2: Health & Technology
*(Add team member names & roles here)*

## 📄 License

*(Add license — e.g. MIT for the prototype, TBD for production codebase)*
