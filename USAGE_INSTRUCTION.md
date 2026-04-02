# Usage Instruction – Claude Product Agent

This document provides a complete, step-by-step guide for using the
Claude Product Agent from meeting notes to PRD.

---

## Prerequisites

- Claude CLI / terminal environment with filesystem access
- PowerShell (Windows) or Terminal (macOS / Linux)
- Optional: Pandoc (for exporting Word documents)

---

## Step 1 – Start Claude with the Multi-Agent System

From the project root:

```powershell
cd path\to\product-agent
claude --system .claude/system.md
```

---

## Step 2 – Import a New Meeting (Agent A)

This step turns one raw meeting note into one structured artifact.

### Create a raw meeting note file

```powershell
notepad input\meeting_2026-04-02-search-kickoff.txt
```

Paste raw meeting notes or transcript directly.
Do not clean or summarize manually.

### Run Agent A

```text
Activate Agent A: MeetingStructuringAgent.

Input file:
- input/meeting_2026-04-02-search-kickoff.txt

Output directory:
- meetings/2026-04-02-search-kickoff/

Create a single file named artifact.md.
Do not create additional files.
```

Expected output:

```text
meetings/2026-04-02-search-kickoff/artifact.md
```

---

## Step 3 – Synthesize Insights (Agent B)

This step synthesizes insights across one or more meeting artifacts.

```text
Activate Agent B: ProductSynthesisAgent.

Input artifacts:
- meetings/**/artifact.md

Focus on:
- Domain: search
- Problem: latency

Output path:
- product/synthesis-search-latency.md
```

Expected output:

```text
product/synthesis-search-latency.md
```

---

## Step 4 – Generate a PRD (Agent C)

This step generates a PRD from exactly one synthesis file.

```text
Activate Agent C: PRDWritingAgent.

Use synthesis file:
- product/synthesis-search-latency.md

Output path:
- product/PRD-search-latency.md
```

Expected output:

```text
product/PRD-search-latency.md
```

---

## Step 5 – Export PRD to Word

Install Pandoc:
https://pandoc.org/installing.html

```powershell
pandoc product\PRD-search-latency.md -o product\PRD-search-latency.docx
```

Markdown is the source of truth.
Word is an export format only.
