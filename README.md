# CorVas AI

CorVas AI is an AI-powered cardiac recovery companion built for the Pulse Foundry AI Healthcare Hackathon 2026. It helps patients understand their care, stay engaged with cardiac rehab, manage medications, and escalate to humans when recovery starts to drift into risk.

This repository is organized around the actual demo submission, not the broader ideation workspace. The core submission app lives in `visitflow/`, with an additional native iOS presentation build in `VisitFlowiOS/`.

## Why This Exists

Cardiac rehab is one of the most effective interventions in recovery after a major cardiac event, but participation and completion remain low. Patients often leave the hospital with instructions, anxiety, and a long recovery plan, but without enough day-to-day support.

CorVas AI is designed to close that gap by turning recovery into a guided, explainable, and human-supported journey.

## What Judges Should See

This project was shaped around the hackathon requirements:

- A working demo, not just slides
- A clear AI interaction with the patient
- A visible hook that keeps patients engaged
- A blueprint showing how the full system works
- A public GitHub repo and live deployment

CorVas AI addresses those directly:

- AI interaction: live visit explanation, grounded Q&A, recovery nudges, risk-aware support
- Hook: supportive accountability through rehab progress, family support, logistics help, and personalized encouragement
- Blueprint: visit context, rehab data, medication behavior, and wearable-style signals flow into an AI support and escalation loop

## Core Experience

- Live visit transcription with plain-language AI explanations
- Pre-visit preparation and question generation
- Post-visit follow-up with grounded answers
- Medication reminders and adherence support
- 12-week rehab progress tracking
- Document summaries in patient-friendly language
- Family, peer, and care-circle messaging
- Escalation logic for rising-risk recovery situations

## Submission Links

- Live demo: `ADD_DEPLOYED_URL_HERE`
- GitHub repo: `ADD_GITHUB_URL_HERE`
- Primary app route: `/app?view=live-visit`

## Demo Flow

1. Open the live visit experience.
2. Start the visit recording and show transcript streaming.
3. Tap a clinical moment and show the AI translation in plain language.
4. Move to rehab and simulate both a successful adherence moment and a risky setback.
5. Show the escalation flow in messages and support surfaces.
6. Return to the overview or landing page to show the system blueprint.

## Architecture

```text
Visit transcript
Medication behavior
Rehab progress
Wearable-style signals
        |
        v
    CorVas AI
explain -> guide -> encourage -> detect risk
        |
        v
Escalation layer
family -> care team -> support services
```

## Tech Stack

- Next.js App Router
- TypeScript
- Tailwind CSS
- Framer Motion
- Zustand
- OpenAI and Anthropic model abstraction
- SwiftUI companion app for iOS presentation

## Project Structure

```text
visitflow/          Main hackathon web app
VisitFlowiOS/       Native iOS presentation build
visitflow-iphone/   Earlier mobile web prototype
```

## Local Development

### Web app

```bash
cd visitflow
npm install
npm run dev
```

Open `http://localhost:3000`.

### iOS app

Open:

`/Users/nathanlara/Desktop/Pulse_Hackathon/VisitFlowiOS/VisitFlowiOS.xcodeproj`

Use the `VisitFlowiOS` scheme in Xcode and run on an iPhone simulator.

## Environment

The app expects local API keys for supported providers.

```bash
cp .env.example .env
```

Then provide the required values locally. Do not commit secrets.

## Repository Notes

The repo originally included ideation files, raw source materials, local build output, and unrelated visual experiments used during exploration. The submission-facing README and `.gitignore` now prioritize the actual competition deliverable so the project is easier for judges and collaborators to understand quickly.
