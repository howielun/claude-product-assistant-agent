## 🚀 Quick Start

---

### 1️⃣ Requirements

- Claude CLI / terminal environment with filesystem access  
- PowerShell (Windows) or Terminal (macOS/Linux)  
- (Optional) [Pandoc](https://pandoc.org/) for Word export  

---

### 2️⃣ Initialize Claude

From the project root (PowerShell):

```bash
cd path\to\product-agent
claude --system .claude/system.md
📝 Use Case 1: Convert Notes into a Standardized Format (Agent A)
Step 1 — Add raw meeting notes
notepad input/meeting_2026-04-02-search-kickoff.txt

📌 Note 1
Paste raw notes or transcript directly — no cleanup needed.

📌 Note 2
You can choose any filename for the raw meeting notes.

Step 2 — Run Agent A

Activate:

MeetingStructuringAgent

Input:

input/meeting_2026-04-02-search-kickoff.txt

Output:

meetings/2026-04-02-search-kickoff/

Rules:

Create a single file named artifact.md
Do not create additional files

✅ Result

meetings/2026-04-02-search-kickoff/artifact.md

📌 Each meeting produces exactly one artifact.

🔍 Use Case 2: Synthesize Insights (Agent B)

Generate insights across one or more meetings.

Step 1 — Run Agent B

Activate:

ProductSynthesisAgent

Input:

meetings/**/artifact.md

Focus (optional):

Domain: search
Problem: latency

Output:

product/synthesis-search-latency.md

✅ Result

product/synthesis-search-latency.md

📌 Notes:

You can generate multiple syntheses from the same artifacts
Input can include multiple artifacts
"Focus" is optional
📄 Use Case 3: Generate a PRD (Agent C)
Step 1 — Run Agent C

Activate:

PRDWritingAgent

Input:

product/synthesis-search-latency.md

Output:

product/PRD-search-latency.md

✅ Result

product/PRD-search-latency.md
📤 Use Case 4: Export to Word (Optional)
Step 1 — Install Pandoc

https://pandoc.org/installing.html

Step 2 — Convert PRD to Word
pandoc product/PRD-search-latency.md -o product/PRD-search-latency.docx

📌 Markdown remains the source of truth.

🧠 Design Principles
One meeting → one artifact
Artifacts are immutable history

Synthesis is perspective-based and cheap to regenerate

Domain / Problem are the only required topic tags

PRDs are intentional, not automatic
