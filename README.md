# Decision Council

**A locally hosted, multi-agent AI decision support system. No internet required. No data leaves your machine.**

![Version](https://img.shields.io/badge/version-0.1.0-teal) ![License](https://img.shields.io/badge/license-MIT-blue) ![Python](https://img.shields.io/badge/python-3.10%2B-blue) ![Ollama](https://img.shields.io/badge/powered%20by-Ollama-black)

---

## What Is This

Decision Council is an open-source AI system that runs entirely on your own computer. It uses a council of specialized AI agents — each with a distinct analytical lens — to help you think through complex decisions with rigor and without bias.

Unplug your internet. It still works. Nothing you type is sent to any server. No company sees your input. No API key required.

Think of it as a private advisory board that lives on your machine.

This was built and tested on an old, underpowered laptop. If it runs here, it runs anywhere.

---

## How It Works

When you submit a decision, the system runs a structured three-stage process:

```
Your Input
    ↓
[Mediator] Triage — reads your Identity Matrix, selects the 3 most relevant specialists
    ↓
[Specialists] Dialogue Rounds — each specialist analyzes the decision from their domain
    ↓
[Mediator] Synthesis — produces a final recommendation, tradeoffs, and confidence rating
    ↓
Executive Dashboard — rendered in the UI with full reasoning visible
```

The internal debate between specialists stays hidden by default. You see a clean, structured result. The full specialist dialogue is available if you want to audit it.

The user always remains in control of the final decision. The system advises. You decide.

---

## Core Principles

- **Sovereign by design** — everything runs locally via Ollama, zero external calls
- **Transparent reasoning** — every recommendation is auditable, not a black box
- **Profile-aware** — advice is anchored to your actual situation, not generic
- **Modular** — new specialists and capabilities can be added by the community
- **You stay in control** — the system presents perspectives and tradeoffs, never dictates

---

## The Specialist Roster

Six specialist agents are available by default (configurable in the UI):

- **Risk & Consequence** — maps downside scenarios and failure modes
- **Values & Alignment** — checks the decision against your personal constraints
- **Strategic Perspective** — long-horizon thinking, second-order effects
- **Ethics** — flags moral tradeoffs and blind spots
- **Financial Impact** — cash flow, opportunity cost, resource implications
- **Human Relationships** — relational consequences, stakeholder dynamics

---

## The Identity Matrix

On first run, the system builds a 4-layer psychological profile from your context input — your risk tolerance, decision style, hard constraints, and current priorities. This profile is injected into every analysis so the council reasons about *your* situation, not a generic one.

All profile data is stored locally as JSON in `memory_data/`. It updates passively over time as you run more sessions.

---

## Requirements

- Python 3.10+
- [Ollama](https://ollama.com) installed and running
- ~8GB RAM minimum (16GB recommended for the 8B mediator model)

Pull the required models:

```bash
ollama pull qwen3:8b        # Mediator model — triage and synthesis
ollama pull qwen2.5:3b      # Specialist and chat model — fast and lightweight
```

---

## Installation

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/decision-council.git
cd decision-council

# 2. Create a virtual environment
python -m venv venv

# Windows:
venv\Scripts\activate

# Mac/Linux:
source venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Make sure Ollama is running
ollama serve

# 5. Pull the required models
ollama pull qwen3:8b
ollama pull qwen2.5:3b

# 6. Launch
streamlit run ui/streamlit_app.py
```

Opens at `http://localhost:8501`

You can also run a quick command-line test without the UI:

```bash
python main.py
```

---

## First Run

On first launch you'll go through a short onboarding flow. Describe your current situation honestly — your goals, constraints, what's broken, what's non-negotiable. The system extracts your baseline Identity Matrix from this input. Takes 30–60 seconds depending on your hardware.

After onboarding, the Command Center is your home base.

---

## Project Structure

```
decision-council/
├── config.py                  # All model and system settings
├── decision_council.py        # Main orchestration class
├── requirements.txt
│
├── core/
│   ├── mediator.py            # Triage, dialogue coordination, synthesis
│   ├── dialogue_manager.py    # Multi-round specialist dialogue
│   └── synthesizer.py        # Output formatting
│
├── specialists/               # Individual specialist logic
├── prompts/
│   ├── mediator_prompts.py    # Mediator system prompt
│   └── specialist_prompts.py  # All specialist identity prompts
│
├── memory/
│   ├── memory_manager.py      # Profile read/write
│   ├── user_profile.py        # Profile schema
│   └── session_memory.py      # Session log management
│
├── memory_data/               # Your profile — stored locally, gitignored
├── sessions/                  # Decision logs — stored locally, gitignored
│
├── chat/
│   ├── main_chat.py           # Council Coordinator chat interface
│   └── chat_router.py        # Routes input to structured vs chat mode
│
├── ui/
│   ├── streamlit_app.py       # Main application entry point
│   └── dashboard_renderer.py  # HTML decision output renderer
│
└── utils/
    ├── ollama_client.py       # Ollama API wrapper
    └── json_parser.py         # Robust JSON extraction from LLM output
```

---

## Configuration

All settings live in `config.py`:

```python
MEDIATOR_MODEL = "qwen3:8b"       # Handles triage and synthesis
SPECIALIST_MODEL = "qwen2.5:3b"   # Runs the specialist swarm
MAX_DIALOGUE_ROUNDS = 2            # How many rounds specialists debate
STRUCTURED_TEMPERATURE = 0.3       # Lower = more consistent decisions
CHAT_TEMPERATURE = 0.7             # Higher = more natural conversation
```

The system works on `qwen2.5:3b` alone if your hardware is limited — slower and less nuanced, but fully functional.

---

## Privacy

- Zero network calls — all inference runs locally via Ollama
- No telemetry of any kind
- Your profile and session files live on your own disk
- Both `memory_data/` and `sessions/` are gitignored — they will never be accidentally committed

---

## Current Limitations (v0.1)

This is an early release. Known rough edges:

- Model selection requires editing `config.py` directly — UI model selector is on the roadmap
- Profile extraction quality scales with model size — larger models produce better profiles
- Session log retention settings in the UI are not yet wired up
- No multi-user support — designed for a single local user
- Minor path handling quirks on some Windows environments

---

## Roadmap

- [ ] **v0.2** — In-UI model selector so users can run whatever models their hardware supports, no config editing required
- [ ] Specialist voting and dissent protocol — structured disagreement between agents
- [ ] Context compression for small models
- [ ] Export decisions to PDF
- [ ] Multi-user profile support
- [ ] Plugin architecture for custom specialist personas
- [ ] Mobile-friendly layout

---

## Contributing

This project is being released at v0.1 intentionally — rough edges and all. The architecture is solid. There is real work to be done and this is an open invitation to do it together.

To contribute:

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes
4. Open a pull request with a clear description of what you built and why

Areas where contributions are most welcome:

- New specialist personas (`prompts/specialist_prompts.py`)
- Improved profile extraction logic (`memory/memory_manager.py`)
- Better JSON parsing robustness (`utils/json_parser.py`)
- UI improvements (`ui/streamlit_app.py`)
- Setup guides for Linux and Mac
- Testing and bug reports

---

## License

MIT — fork it, build on it, ship it, improve it.

---

## Author

Built by **Lars Horpestad** — writer, entrepreneur, based in Medellín, Colombia.

This project was built during a period of post-traumatic clarity following a motorcycle accident that, according to the doctors, I should not have survived. It was built on a machine that probably shouldn't have survived either.

Make of that what you will.

---

*v0.1 — Released June 2026*
