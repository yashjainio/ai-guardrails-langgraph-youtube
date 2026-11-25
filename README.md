# **LangGraph Guardrails Series**

Welcome to the **LangGraph Guardrails Playlist** repository!

This playlist is designed to help you understand AI guardrails from the ground up — starting with the basics of LangGraph state, nodes, and edges, all the way to prompt injection defense, jailbreak detection, PII redaction, tool permissions, human-in-the-loop approval, and a full guardrails pipeline around a real LLM.
Each video walks you through real, practical examples so you can build AI helpers that stay safe even when users (or the data they read) try to trick them. Episodes 01–09 run fully offline — no API key needed.

---

## 🐍 **Install Python Using Miniconda / Miniforge**

To keep your AI projects clean and organized, it is recommended to use **conda environments**. Follow the steps below to install Miniforge and set up your environment.

---

### 🔗 **Download Miniforge for macOS (ARM64)**

Download from the official repository:
https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh

---

### 💻 **Install Miniforge**

Run the following commands:

```bash
chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh
sh ~/Downloads/Miniforge3-MacOSX-arm64.sh
source ~/miniforge3/bin/activate
```

---

### 🧱 **Create a project-specific conda environment**

```bash
conda create --prefix ./env python=3.13
conda activate ./env
```

---

### 📦 **Install packages from requirements.txt**

```bash
pip install -r requirements.txt
```

---

### 🔑 **(Optional) OpenAI API key for episode 10**

Only the bonus episode calls a real model. Copy `.env.example` to `.env` and set `OPENAI_API_KEY` (and optionally `OPENAI_MODEL`). Without a key, the notebook still runs: the input guards block attacks before the model is ever called.

Your guardrails environment is ready to build safe AI apps 🚀

---

# **📺 Playlist Breakdown**

### **1. What Are Guardrails? + LangGraph Basics**

- The "school gate" picture used throughout the series.
- LangGraph basics: state, nodes, and edges.
- Building an AI helper with no guards — and watching it get tricked.

### **2. Input Guard: Prompt Injection**

- Building `guard_input`, the first guard at the gate (OWASP LLM01).
- Building `refuse`, the polite NO when a guard blocks a request.
- Using conditional edges to route between guarded paths.

### **3. Jailbreak Detection**

- Catching "DAN mode", "developer mode", and "pretend you have no rules" attacks.
- Normalising text to catch sneaky spellings like `D.A.N m0de`.
- Measuring the guard: false positives vs. false negatives.

### **4. PII Detection & Redaction**

- Regex detectors for email, phone, credit card (with Luhn check), Aadhaar, PAN, SSN, and IP address.
- Four strategies: redact, mask, hash, and block.
- Running the PII guard on both the input and the output of the graph.

### **5. Tool Permissions (RBAC)**

- Preventing Excessive Agency (OWASP LLM06): your code decides who can do what, not the AI.
- A `WHO_CAN_USE` role → tool permission table with deny-by-default `guard_tool`.
- Wiring the helper ↔ tool loop.

### **6. Indirect Prompt Injection in Tool Results**

- Attacks hidden inside web pages, emails, PDFs, and database rows.
- Watching an unguarded helper obey a poisoned page.
- Scanning tool results before they go back to the AI.

### **7. Output Guard: Secrets & Safe Output**

- Detecting leaked secrets with keywords and patterns.
- Using a canary token to catch system-prompt leaks.
- PII redaction and HTML escaping on the way out (OWASP LLM02, LLM10).

### **8. Human-in-the-Loop Approval**

- Pausing the graph with `interrupt(...)` before risky actions.
- Saving state with a checkpointer and resuming with `Command(resume=...)`.
- Letting admins delete — but only after a human approves.

### **9. Full Guardrails Pipeline**

- Combining every guard from episodes 02–08 into one graph.
- `guard_input`, `guard_tool`, `ask_human`, `run_tool`, `guard_output`, and `refuse` working together.

### **10. Bonus: Guarding a Real LLM with OpenAI**

- Plugging in a real OpenAI model with tool calling.
- Keeping the same guards — the graph shape doesn't change.

---

# **📄 requirements.txt**

```
# Core
langgraph==1.2.19
langchain-core==1.7.3

# Episode 10 (bonus): real OpenAI model
langchain-openai==1.7.3
python-dotenv==1.2.4

# Notebooks
jupyterlab==4.6.5
ipykernel==7.4.0
nbformat==5.11.1
nbconvert==7.17.2
```

---

# **🤝 Contributing**

Got suggestions or improvements?
Feel free to open an issue or submit a pull request.

---

# **📬 Stay Connected**

- [YouTube Channel](https://www.youtube.com/@yashjainio)
- [LinkedIn](https://www.linkedin.com/in/yashjainio)

---

Thank you for checking out the **LangGraph Guardrails Playlist**!
Happy building with AI 🚀
