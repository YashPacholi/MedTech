# CaseSetu

**AI-assisted patient case-taking: speak, scan, and consult in seconds.**

CaseSetu lets a patient give their medical history before the consultation, in their own language, by text, voice, or quick taps. It also digitises old reports. The doctor then opens a structured case summary instead of starting from scratch.

This repository contains the **front-end UI prototype** built for Smart India Hackathon 2026.

| | |
|---|---|
| Problem statement | SIH26047 – Patient Case-Taking Software |
| Ministry | Ministry of Ayush |
| Theme | MedTech / BioTech / HealthTech |
| Category | Software |
| Team | Team Straw Hats |
| Live demo | https://med-tech-xi.vercel.app/ |

---

## The problem

Outpatient doctors in busy hospitals have only a few minutes per patient. History-taking is rushed, old records are on paper, and language barriers make it harder still. A good history is often what points to the diagnosis, so anything missed at this stage costs time and quality of care.

## What CaseSetu does

- **Patient flow:** language choice, consent, profile, department, chief complaint, adaptive follow-up questions, optional document upload, priority screening, review and submit.
- **Adaptive questions:** the questions change with the answers. For example, a "Yes" to shortness of breath adds a question about breathlessness at rest.
- **Ayush history mode:** when the Ayurveda department is chosen, an extra assessment covers Prakriti, Vikriti, Agni, Koshtha, diet, lifestyle and sleep.
- **Priority screening (rule-based):** a transparent check that shows why a case was flagged. It is not a diagnosis.
- **Doctor view:** a case summary with symptoms, history, timeline, reports and the priority reasoning. The doctor completes the case or schedules a follow-up.
- **Admin view:** overview charts, a triage queue, doctor assignment, an audit log and settings.

### Priority rules used in the prototype

| Signal | Points |
|---|---|
| Chest pain mentioned | +3 |
| Shortness of breath | +3 |
| Breathlessness at rest | +2 |
| Worse with physical activity | +1 |
| Severity 7–10 out of 10 | +2 |
| Severity 4–6 out of 10 | +1 |

A total of 6 or more gives **Urgent review**, 3 to 5 gives **Priority review**, and anything lower stays **Normal**.

---

## Project status

This is a UI prototype with sample data. Some features are simulated so the full flow can be demonstrated.

| Feature | Status |
|---|---|
| Patient, doctor and admin screens | Built |
| Adaptive question flow | Built |
| Rule-based priority screening with reasons | Built |
| Ayush history assessment | Built |
| Triage queue, doctor assignment, audit log | Built (sample data) |
| Voice input | Simulated (fixed sample sentence) |
| Document OCR | Simulated (fixed sample result) |
| Multilingual interface and speech | Planned (language picker only for now) |
| Backend API and database (FastAPI, MongoDB) | Planned |
| Real speech recognition and OCR | Planned |
| Evidence links from summary to source | Planned |
| ABDM / ABHA and FHIR integration | Planned |
| Offline-first PWA | Planned |

---

## Run it locally

There is no build step.

1. Download `index.html` from this repository.
2. Open it in Chrome or Edge. It needs an internet connection to load the fonts and libraries from a CDN.

## Try the demo flow

1. On the login screen, choose **Continue as Demo Patient**.
2. Go through language and consent. On the profile screen, use **Use demo patient** to fill the form.
3. Pick **General Medicine**, describe a complaint (for example, chest pain), and answer the questions.
4. Review the priority screening, then submit the case.
5. Use **Demo: Switch Role** in the sidebar and choose **Admin**. Open **Triage Queue** and assign the case to **Dr. Gupta**.
6. Switch to **Doctor**, open the case from the dashboard, and complete it or schedule a follow-up.
7. Switch back to **Patient** to see the updated status and follow-up.

## Tech used

- React 18 (loaded from CDN)
- Tailwind CSS (CDN)
- Babel Standalone, to run the JSX in the browser
- Google Fonts: Sora and Inter
- All data lives in browser memory and resets when the page is refreshed

## Planned architecture

Patient device (PWA) → secure API gateway → voice interview, document AI, summary engine, and consent modules → MongoDB → doctor console and hospital system / ABHA record via FHIR.

---

## Important notes

- All patients, doctors and reports in this prototype are made-up sample data.
- CaseSetu supports the clinician. It does not diagnose, and the doctor always makes the final decision.
- The priority screening is a simple rule set for demonstration, not a validated clinical tool.
- Security and encryption labels in the interface describe the planned design and are not implemented in this prototype.

## Team

Team Straw Hats
