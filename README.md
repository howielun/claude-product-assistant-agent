\# Claude Product Agent 🧠📄



A multi-agent workflow for turning meeting notes into structured insights and PRDs using Claude (terminal / CLI).



This toolkit is designed for Product Managers and teams who want to:

\- Organize meeting notes reliably

\- Extract long-term product insights

\- Generate PRDs with traceable sources

\- Export clean, human-readable documents (Word)



\---



\## ✨ What This Is



This is \*\*not a chatbot\*\*.



This is a \*\*product documentation system\*\* powered by Claude that enforces:

\- Clear separation of responsibilities (agents)

\- Structured, reusable artifacts

\- Topic-based knowledge accumulation (Domain / Problem)

\- Explicit, reviewable outputs at every step



\---



\## 🧠 Agent Overview



| Agent | Responsibility | Output |

|------|---------------|--------|

| Agent A | Structure raw meeting notes | `artifact.md` |

| Agent B | Synthesize insights across meetings | `synthesis-\*.md` |

| Agent C | Generate PRD from synthesis | `PRD-\*.md` |



\---



\## 📁 Project Structure



```text

product-agent/

├─ input/                  # Raw meeting notes (human input)

├─ meetings/               # One folder per meeting

│  └─ YYYY-MM-DD-topic/

│     └─ artifact.md

├─ product/                # Syntheses and PRDs

│  ├─ synthesis-\*.md

│  └─ PRD-\*.md

├─ .claude/

│  └─ system.md            # Multi-agent system prompt

├─ scripts/

│  └─ export.ps1           # Markdown → Word

└─ README.md



```



\---



\## 🚀 How to Use

For complete step-by-step instructions, see:

👉 **[USAGE INSTRUCTION.md](./USAGE INSTRUCTION.md)**

