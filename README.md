# Pulse Hackathon

Workspace for a Pulse Foundry cardiac rehab hackathon project, including source audio, generated transcripts, and multiple rounds of idea exploration based on the official prompt.

## Structure

- `scripts/`
  - `transcribe_voice_memos.py`: Whisper-based transcription script for Apple Voice Memo recordings
- `data/audio/`
  - Raw `.m4a` voice memo files
- `data/transcripts/`
  - Raw `.txt` transcription outputs
- `docs/ideas/`
  - Idea exploration documents
- `docs/transcripts/`
  - Combined Markdown transcript notes

## Transcription

Install dependencies:

```bash
python3 -m pip install openai-whisper imageio-ffmpeg
```

Transcribe one file:

```bash
python3 scripts/transcribe_voice_memos.py "data/audio/The Anya and Andrew Shiva Gallery 4.m4a" --model base
```

Transcribe all audio in the folder:

```bash
python3 scripts/transcribe_voice_memos.py data/audio --model base
```

Write transcripts into the dedicated transcript folder:

```bash
python3 scripts/transcribe_voice_memos.py data/audio --model base --output-dir data/transcripts
```

## Notes

- The repo keeps the raw audio and transcript outputs for hackathon context.
- `Hackathon-6/` is treated as a local reference clone and is ignored from version control.
- Copy `.env.example` to `.env` if you want local configuration values without committing secrets.
