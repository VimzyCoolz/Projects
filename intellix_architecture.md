# Intellix IDE Architecture & Roadmap

🎯 **Vision**  
Build **Intellix IDE**, a browser-based AI development environment that is local-first rather than server-first.  
The user owns:
* their models,
* their AI memory,
* their projects,
* their workspace.  

Your servers are not responsible for running the AI.

---

## 🏗 Foundation
Instead of building everything from scratch:
* **✅ Start from OpenHands.**
* Clone it first.
* Understand the architecture.
* Gradually transform it into Intellix IDE.  

The objective is not to rebrand OpenHands immediately but to evolve it into a different product.

---

## 🔄 Biggest Architectural Change

### Current OpenHands:
```text
Browser
   │
OpenHands Server
   │
LLM
```

### Intellix:
```text
Browser
   │
Intellix Runtime (localhost)
   │
LLM
```
The **Runtime** becomes the center of the system.

---

## 📦 Intellix Workspace

Instead of installing multiple components separately, users create or open an Intellix Workspace.

The workspace contains:

- Runtime
- Inference Engine
- AI Models
- Projects
- AI Memory
- Chat History
- Settings
- Cache

The user chooses where the workspace is stored.

Supported locations:
- Internal SSD
- External SSD
- USB Drive
- Custom Folder

The workspace is portable between devices.

### Responsibilities:
* Download AI models.(from huggingface)
* Manage installed models.
* Start/stop models.
* Expose a localhost API.
* Manage AI memory.
* Manage projects.
* Backup workspaces.
* Restore workspaces.
* Manage updates.
* Connect to cloud providers when the user chooses.

It becomes the web IDE which gets its models locally.

---

## 💻 Intellix IDE
The browser application becomes lightweight.

### Responsibilities:
* Monaco editor
* AI chat
* Terminal UI
* File explorer
* GitHub integration
* Settings
* Calling Intellix Runtime

No heavy AI work happens inside the browser.

---

## 🤖 AI Models
The Runtime should support multiple providers.

### Local:
* Ollama
* LM Studio
* llama.cpp
* auto detect

### Cloud:(this already exist on openhands)
* OpenRouter
* OpenAI
* Anthropic
* Gemini

The IDE never talks directly to these providers.

---

## 🔌 Adapter Architecture
Instead of the IDE learning every provider:

```text
IDE
 │
 ▼
Intellix Runtime
 │
 ├── Ollama Adapter
 ├── LM Studio Adapter
 ├── llama.cpp Adapter
 ├── OpenRouter Adapter
 ├── Anthropic Adapter
 └── Future Adapters
```

The IDE always speaks one API. Only the Runtime translates requests.

---

## 📦 Portable Workspace
The Runtime stores workspaces.

### Example Directory Structure:
```text
Intelix_Workspace/
│
├── AI/
├── Models/
├── Projects/
├── Memory/
├── Git/
└── Settings/
```

Users choose where to save it (e.g., SSD, HDD, USB drive, External SSD).

---

## 🔄 Backup & Restore
* **Instead of:** Connect to Cloud things only
* **we add this below it:** 
  * 📂 Backup Workspace
  * 📂 Restore Workspace

The Runtime performs the work. The browser only requests it.

---

## 🖥 Model Storage
Users decide where models live (Internal SSD, External SSD, USB drive). The Runtime remembers those locations.

---

## 🧠 Memory
Memory is stored locally (conversations, AI context, workspace state, settings). Everything belongs to the user.

---

## ☁ Cloud
Cloud is optional. Users may choose Local Runtime or Cloud Provider. Local-first remains the default philosophy.

---

## 🎨 UI Changes
LLM settings become structured like:
* **LLM**
  * **Cloud**(which already exists on openhands)
    * • OpenRouter
    * • OpenAI
    * • Anthropic
  * **Local**
    * • LLM (with download buttons and storage size)
    * • Ollama
    * • LM Studio
    * • llama.cpp

---

## 🔤 Rebranding Strategy
Don't rename everything immediately.

* **Phase 1:** Learn OpenHands. Make it work.
* **Phase 2:** Change architecture. Add Runtime.
* **Phase 3:** Rename classes. Rename branding. Update documentation.

Using IDE refactoring tools is safer than global text replacement for code symbols.

---

## 💰 Business Philosophy
Instead of charging for inference:  
Users provide their own compute. They choose their models, their storage, and their hardware. This keeps your infrastructure costs low while giving users more control.

---

## 📈 Long-Term Vision
```text
                 Intellix IDE
                       │
                       ▼
               Intellix Runtime
                       │
     ┌─────────────────┼──────────────────┐
     │                 │                  │
 Model Manager     Workspace Manager   Memory Manager
     │                 │                  │
     ├──────────────┬──┴───────┬──────────┤
     ▼              ▼          ▼          ▼
Ollama         llama.cpp   OpenRouter   LM Studio
```

Eventually, the same Intellix Runtime could power other CoolzTech products beyond the IDE, making it a reusable foundation for your ecosystem rather than an IDE-only component.
