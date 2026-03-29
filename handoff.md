# VisitFlow AI — Agent Handoff

**Hackathon:** Pulse Foundry AI Healthcare Hackathon 2026
**Product:** VisitFlow AI — Real-Time Cardiac Care Co-Pilot
**Status:** Core app built and running. Ready for polish, deployment, and demo prep.

---

## Quick Start

```bash
cd /Users/nathanlara/Desktop/Pulse_Hackathon/visitflow
npm run dev        # http://localhost:3000
npm run build      # production build (currently clean — 0 errors)
```

API keys are already in `.env.local` (Anthropic + OpenAI). Do not commit this file.

---

## What's Built

### Routes
| URL | Description |
|-----|-------------|
| `/` | Landing page — hero, stats, feature cards, architecture diagram |
| `/app` | Full app shell — sidebar nav, all views |
| `/app?view=live-visit` | Deep-link directly to Live Visit |

### Views (`src/components/views/`)
| File | View | Status |
|------|------|--------|
| `OverviewView.tsx` | Dashboard — vitals, rehab tasks, last visit recap, week progress | ✅ Done |
| `LiveVisitView.tsx` | **Hero** — doctor avatar, streaming transcript, AI explanations, Q&A | ✅ Done |
| `PreVisitView.tsx` | Symptom intake, question builder, AI visit brief generation | ✅ Done |
| `PostVisitView.tsx` | Diagnosis cards, meds, checklist, grounded Q&A | ✅ Done |
| `RehabView.tsx` | Daily tasks, Cardio Stress Engine, streaks, milestones | ✅ Done |
| `MessagesView.tsx` | Doctor/AI/patient chat, family alert panel, escalation demo | ✅ Done |
| `MedicationsView.tsx` | Drug cards with dose, purpose, side effects | ✅ Done |
| `DocumentsView.tsx` | Clinical file browser | ✅ Done |
| `PeersView.tsx` | Recovery companions, milestone messages | ✅ Done |

### Core Files
| File | Purpose |
|------|---------|
| `src/lib/types.ts` | All TypeScript types (TranscriptLine, Visit, RehabTask, etc.) |
| `src/lib/mock-data.ts` | FHIR-style mock data — patient Maria Santos, visit, rehab, alerts, messages |
| `src/lib/store.ts` | Zustand store — global state for all views |
| `src/lib/ai-service.ts` | AI functions — calls Claude Haiku / GPT-4o-mini with demo fallbacks |
| `src/components/AppShell.tsx` | Sidebar navigation + patient vitals strip |
| `src/components/RiskBadge.tsx` | Green/Yellow/Orange/Red risk indicator |

### AI Service Layer (`src/lib/ai-service.ts`)
All functions implemented with live API calls + graceful demo fallbacks:
- `streamTranscript()` — simulated live transcript stream
- `translateDoctorStatement(text)` — plain-language medical translation
- `explainDiagnosis(diagnosis)` — patient-friendly explanation
- `answerVisitQuestion(question, context)` — grounded Q&A from transcript
- `detectRiskState(params)` — returns green/yellow/orange/red
- `evaluateCardioStress(params)` — Karvonen formula, returns CardioStressResult
- `generateRehabPlan(week, compliance)` — personalized plan text
- `generateEncouragement(scenario)` — win/wall/streak/milestone responses
- `detectEscalation(params)` — returns escalation level + contact message

---

## Stack
- **Framework:** Next.js 16.2.1 (App Router, Turbopack)
- **Language:** TypeScript (strict)
- **Styling:** Tailwind CSS v4 + custom design tokens (dark-first, glass morphism)
- **Components:** shadcn/ui (base-ui fork)
- **Animation:** Framer Motion 12
- **State:** Zustand 5
- **Icons:** Lucide React
- **AI:** Anthropic Claude Haiku + OpenAI GPT-4o-mini (abstracted, either works)

---

## What's Missing / Next Tasks

### High Priority (demo blockers)
- [ ] **Vercel deployment** — run `vercel deploy` from `visitflow/`. Check that `ANTHROPIC_API_KEY` and `OPENAI_API_KEY` are set as environment variables in the Vercel project settings.
- [ ] **Mobile responsiveness** — sidebar collapses to bottom nav on small screens. AppShell needs a responsive breakpoint.
- [ ] **HR simulation ticker** — add a `useEffect` in AppShell or a provider that increments `currentHR` ±2 every 3s to make the sidebar feel live.

### Medium Priority (demo quality)
- [ ] **Replay mode in LiveVisitView** — `mode === 'replay'` state exists but the replay UI isn't wired. Should re-play `MOCK_TRANSCRIPT_LINES` with a scrubber timeline.
- [ ] **Overview HR sparkline** — currently SVG is rendered but could use recharts or a proper micro-chart.
- [ ] **Alert contacts UI in MessagesView** — the `PATIENT.contacts` array exists; add a contact management modal.
- [ ] **Sonner toast notifications** — `src/components/ui/sonner.tsx` is installed. Wire it up for alert triggers and task completions.
- [ ] **Pre-Visit symptom add/remove** — symptom input exists but adding new symptoms isn't implemented.

### Low Priority (polish)
- [ ] **Landing page hero animation** — add a subtle animated mockup of the Live Visit UI (can be a screenshot/static image).
- [ ] **Architecture diagram view** — a dedicated fullscreen diagram for the demo pitch (can use a FigJam embed or SVG).
- [ ] **Documents view** — currently list-only; add a mock PDF preview panel.
- [ ] **Medications view** — add a "next dose" reminder and adherence tracker.

---

## Demo Script (3-minute flow)

1. **Open** `/app?view=live-visit`
2. **Press** "Start Visit Recording" → watch transcript stream in, AI explains each line
3. **Tap** the arrhythmia or metoprolol line → AI translation expands
4. **Navigate** to Rehab → press "Simulate Walk" → show optimal → press "Trigger Alert" → show critical stop
5. **Navigate** to Messages → press "Demo Alert" → show red alert sent to contacts
6. **Navigate** to Overview → show streak, week progress, quick actions
7. **Show** Landing page architecture diagram

---

## Key Design Decisions to Preserve

- **Dark mode only** — `globals.css` uses oklch tokens, no `.dark` toggle needed
- **Glass morphism** — use `.glass` and `.glass-card` utility classes, not custom inline styles
- **No mock API routes** — all AI calls go directly from client to Anthropic/OpenAI (acceptable for hackathon demo)
- **Patient identity** — Maria Santos, 58, Post-MI Week 3, Dr. Okafor (cardiologist). Keep consistent across all views.
- **Tone** — empathetic, calm, premium. No cartoon UI, no gamification language, no excessive color.

---

## Known Issues

| Issue | Location | Fix |
|-------|----------|-----|
| `visitElapsed` counter uses `getState()` pattern (not reactive) | `LiveVisitView.tsx:275` | Use a local `useRef` counter and sync to store at end of visit |
| `lineTimerRef` only holds the last timeout (doesn't cancel all) | `LiveVisitView.tsx` | Use an array of timeout IDs for proper cleanup |
| Mock data `HEALTH_METRICS` uses `Math.random()` at module load | `mock-data.ts:146` | Fine for demo; use stable seed if SSR issues arise |

---

## Environment

```
Node: check .nvmrc or use 20+
Package manager: npm
.env.local: ANTHROPIC_API_KEY, OPENAI_API_KEY (already populated)
```

To add new environment variables for Vercel, use the dashboard or:
```bash
vercel env add ANTHROPIC_API_KEY
```
