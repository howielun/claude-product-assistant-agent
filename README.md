🚀 Quick Start
1️⃣ Requirements

Claude CLI / terminal environment with filesystem access
PowerShell (Windows) or Terminal (macOS/Linux)
Optional: https://pandoc.org/ for Word export

2️⃣ Initialize Claude
From the project root:
In PowerShell
cd path\to\product-agent
claude --system .claude/system.md

📝 Use Case 1: Convert Notes into a Standardized Format (Agent A)
Step 1 - Add raw meeting notes:
notepad input\**meeting_2026-04-02-search-kickoff**.txt
Note 1: Paste raw notes or transcript directly (no cleanup needed)
Note 2: For the bolded section, you may choose whichever name you prefer to use for the raw meeting notes

Step 2 - Run Agent A (Prompt as below)
Activate Agent A: MeetingStructuringAgent.

Input file:
- input/**meeting_2026-04-02-search-kickoff**.txt

Output directory:
- meetings/**2026-04-02-search-kickoff**/

Create a single file named **artifact.md**.
Do not create additional files.

✅ Result:
meetings/**2026-04-02-search-kickoff**/**artifact.md**
Note: Each meeting always produces one artifact.

🔍 Use Case 2: Synthesize Insights (Agent B)
Generate insights across one or more meetings.

Step 1 - Run Agent B (Prompt as below)
Activate Agent B: ProductSynthesisAgent.
Input artifacts:
- meetings/**/**artifact**.md

Focus on:
- Domain: search
- Problem: latency

Output path:- product/**synthesis-search-latency**.md

✅ Result:
product/**synthesis-search-latency**.md
Note 1: You can generate multiple syntheses from the same artifacts.
Note 2: Input can be multiple artifact
Note 3: "Focus on" can be optional


📄 Use Case 3: Generate a PRD (Agent C)
Step 1 - Run Agent C
Activate Agent C: PRDWritingAgent.

Use synthesis file:
- product/**synthesis-search-latency**.md

Output path:
- product/**PRD-search-latency**.md

✅ Result:
product/**PRD-search-latency**.md


📤 Use Case 4 - Export to Word (Optional)
Step 1 - Install Pandoc once:
https://pandoc.org/installing.html
Step 2 - Convert PRD to Word:
pandoc product\PRD-search-latency.md `  
-o product\PRD-search-latency.docx

Note: Markdown remains the source of truth.


🧠 Design Principles
One meeting → one artifact
Artifacts are immutable history
Synthesis is perspective-based and cheap to regenerate
Domain / Problem are the only required topic tags
PRDs are intentional, not automatic
