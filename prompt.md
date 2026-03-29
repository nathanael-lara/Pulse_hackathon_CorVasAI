# VisitFlow AI — Real-Time Cardiac Care Co-Pilot

You are a principal product engineer, real-time systems architect, and elite UX designer building a venture-scale healthcare product.

This is **not** a demo, **not** a Streamlit app, and **not** a chatbot wrapper.

This must feel like:

- A shipped product
- Investor-ready
- Cinematic, interactive, and intelligent
- A complete rethinking of the doctor visit + rehab experience

---

## Core Product Vision

VisitFlow AI expands beyond PostVisit.ai:

- **PostVisit** = AFTER visit intelligence
- **VisitFlow** = BEFORE + DURING + AFTER + CONTINUOUS CARE

But more importantly:

- We transform the consultation into a real-time, understandable, interactive experience.
- We extend that into daily cardiac rehabilitation support.

**We solve the "Participation Paradox":** Patients drop off cardiac rehab due to fear, confusion, and lack of connection.

**We build:** An AI-powered "Voice of Care" that keeps patients engaged, safe, and supported daily.

---

## Core Experience: "The Living Consultation"

We are not building chat.

We are building a system that:

- Captures the doctor visit
- Streams it live
- Explains it instantly
- Allows interaction
- Replays it later
- Connects it to recovery

---

## Critical System: Recording + Live Transcript

Implement a visit capture system.

### Input

- Simulated or real audio

### Pipeline

```
Audio → Streaming transcription → Structured timeline → AI reasoning
```

### Output

- Live transcript (line-by-line)
- Doctor statements
- AI explanations
- Highlights (diagnosis, meds, instructions)
- Risk signals

### UI

- Transcript appears like subtitles
- Each line clickable
- Tap to expand explanation

---

## Hero Feature: Doctor Avatar + Live Translation

UI includes:

- **Doctor avatar** — subtle, realistic
- **AI translator**
- **Patient view**

Doctor speaks (TTS or simulated video).

### Interaction Example

> **User taps:** "What did he just say?"
>
> **AI responds:** "Your heart rhythm is slightly irregular"

### Supported Actions

- Explain simply
- Go deeper
- Suggest next question
- Mark important

This must feel magical and real-time.

---

## Dual Audio Experience (Hook)

Optional mode: Doctor speaks, then AI overlays explanation.

### User Controls

- Mute doctor
- Hear AI explanation
- Replay

---

## Consultation Replay (Cinematic)

After the visit, present a timeline:

```
Doctor → AI explanation → User understanding
```

### Features

- Replay moments
- Jump to diagnosis/meds
- Highlight key events

This should feel like rewatching your consultation.

---

## Pre-Visit Intelligence

- Symptom intake (chat + structured)
- Visit brief generation
- Questions to ask doctor
- Symptom timeline
- Risk flags

---

## Post-Visit Intelligence

- Structured summary
- Diagnosis explanation
- Medication breakdown
- Follow-up checklist
- Contextual Q&A grounded in visit

---

## Cardiac Rehab System (Core to Win)

### Cardio Stress Engine

**Input:**

- Heart rate
- Steps
- Activity

**Logic:**

- Compare HR vs expected
- Detect fatigue, stress, abnormal recovery

**Output:**

> "Your heart rate is higher than expected — slow down."

---

### Rehab Mode

**Daily tasks:**

- Walking tasks
- Breathing
- Recovery tracking

**AI Behavior:**

| Scenario | Response |
|----------|----------|
| Win | "Great job — this strengthens your heart." |
| Wall | "I noticed you skipped today — want to try a shorter walk?" |

**Tone:** Empathetic, human, motivating.

---

## Real-Time Risk Engine

Top UI indicator:

| Status | Meaning |
|--------|---------|
| Green | Stable |
| Yellow | Monitor |
| Red | Escalate |

**Driven by:**

- Symptoms
- HR patterns
- Transcript signals
- Behavior

---

## Family + Clinician Alert System

Implement trusted contacts:

- Family
- Friends
- Caregivers

### Escalation Tiers

| Level | Action |
|-------|--------|
| Yellow | Patient only |
| Orange | Suggest notify |
| Red | Send alert to contact + clinician queue (mock) |

**Message example:**

> "Maria reported chest discomfort and elevated HR. Please check on her."

### Requirements

- Opt-in controls
- Contact management
- Calm messaging

---

## Doctor-Patient Messaging

- Follow-up questions
- AI-generated suggestions
- Clinician reply (mock)

**Messages link to:**

- Visits
- Meds
- Rehab events
- Alerts

---

## Peer Support System

- Recovery companions
- Encouragement messages
- Milestone support

Do **not** make it childish or unsafe. Frame as trusted peer support.

---

## Engagement Hook

**Recovery Journey:**

- Week progression
- Milestones
- Streaks
- AI encouragement

No childish gamification.

---

## Two-Speed Intelligence Architecture

### Fast Path (Real-Time)

- Thresholds
- Trends
- Anomaly detection
- Symptom + HR fusion

**Used for:** Risk state, alerts, rehab guidance.

### Deep Path (Async ML)

- Personalization
- Dropout prediction
- Behavior analysis
- Recommendation refinement

---

## Design System

### Style

Apple Health x Linear x Claude — minimal, calm, premium.

### Avoid

- Cartoon UI
- Cluttered dashboards

### Avatars

- Subtle, semi-realistic
- Used only in key moments

---

## Stack (Mandatory)

### Core

- Next.js (App Router)
- TypeScript
- Tailwind CSS
- Vercel deployment
- shadcn/ui
- Framer Motion
- Zustand

### AI

- OpenAI / Anthropic abstraction

### Speech

- Whisper-style OR simulated

### Data

- FHIR-style mock data
- HR + steps + transcripts

---

## App Structure

1. Landing page
2. App shell
3. Overview
4. Pre-Visit
5. Live Visit **(HERO)**
6. Post-Visit
7. Rehab Mode
8. Documents
9. Medications
10. Messages

---

## AI Service Layer

Implement the following functions:

- `streamTranscript()`
- `translateDoctorStatement()`
- `explainDiagnosis()`
- `answerVisitQuestion()`
- `detectRiskState()`
- `evaluateCardioStress()`
- `generateRehabPlan()`
- `generateEncouragement()`
- `detectEscalation()`

---

## Architecture Diagram

```
Wearables + Audio → Backend → Fast Risk Engine → UI + Alerts
```

```
Data → ML Layer → Personalization
```

---

## Demo Requirements

1. Live doctor speaking + translation
2. Rehab win + wall
3. Family alert scenario
4. Messaging example
5. Recovery journey
6. Architecture diagram

---

## Priority Order

1. Live Visit (avatar + transcript)
2. Rehab + stress engine
3. Alerts + messaging
4. Pre/Post visit
5. Overview
6. Landing

---

## Final Product Feel

This must feel like:

- A system, not an app
- A care companion, not a chatbot
- Real, not experimental

Ship this like a founding engineer building a real company. Prioritize clarity, interaction, and polish over feature count.