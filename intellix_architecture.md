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

The workspace contains following folders-some will contain files while others will come later time:

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

The workspace is portable between devices. and is created at the beginning(first launch of the site) the workflow download ux will be "import or Create your workspace [import workspace] [ Create workspace]
NB://During workspace creation:

- Choose storage location.
- Download Runtime.
- Download inference engine.
- Choose model source.

Examples:

- Hugging Face
- Local Folder
- USB

  then finally
- Start IDE.

### Responsibilities of local runtime:
* Download AI models.(from huggingface)
* Manage installed models.
* Start/stop models.
* Expose a localhost API.
* Manage AI memory.
* Manage projects.
* import workspaces.
* export workspaces.
* Manage updates.
* Connect to cloud providers when the user chooses.
* Detect workspace.
*Load configuration.
*Start inference engine.
*Stop inference engine.
*Health monitoring.
*API server.
*Version management.

The Runtime becomes the local execution layer for Intellix IDE.

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

Local

• GGUF Models
• Imported Models
• Hugging Face Downloads

Cloud

• OpenRouter
• OpenAI
• Anthropic
• Gemini

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
IntellixWorkspace/

├── Runtime/
│    ├── Intellix Runtime
│    └── inference engine
│
├── Models/
│
├── Projects/
│
├── Memory/
│
├── Chat/
│
├── Settings/
│
└── Cache/
```

Users choose where to save it (e.g., SSD, HDD, USB drive, External SSD).

---

## 🔄 Workspace Management

The IDE provides:

• 📂 Create Workspace

• 📂 Open Workspace

• 📦 Export Workspace

• 📥 Import Workspace

The Runtime performs all operations.

The browser simply requests them.

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
    * • NO NEED TO DOWNLOAD LOCAL AI ENGINES AGAIN SO HERE WE WILL USE IT WHERE USER CAN SEARCH AI MODEL FROM HUGGING FACE AND DOWNLOAD IT TO HIS WORKSPACE
   
      

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

## 📌 Other Important Components

### ⚙️ Configuration

Each workspace contains a configuration file that allows Intellix Runtime to restore the user's environment automatically.

Example:

```text
IntellixWorkspace/

├── Runtime/
├── Models/
├── Projects/
├── Memory/
├── Chat/
├── Settings/
├── Plugins/
├── Cache/
└── config.json
```

Example `config.json`:

```json
{
  "workspaceVersion": 1,
  "runtimeVersion": "1.0.0",
  "engine": "llama.cpp",
  "selectedModel": "Qwen3-Coder-30B",
  "modelPath": "Models/Qwen3-Coder.gguf",
  "workspaceName": "My Workspace",
  "theme": "dark"
}
```

The Runtime reads this file during startup to automatically restore the user's workspace.

---

### 🔌 Plugins

Every workspace reserves a `Plugins/` folder.

```text
IntellixWorkspace/

├── Plugins/
```

This folder allows future expansion without changing the workspace structure.

Possible future plugins include:

- Docker
- Kubernetes
- Flutter
- Unity
- Git extensions
- Database tools
- Custom AI providers
- Community plugins

The Plugins folder may remain empty until plugins are installed.

## 🤖 AI Model Architecture

Model Sources

- Hugging Face
- Local Folder
- USB
- Imported Workspace

Inference Engines

- Ollama
- LM Studio
- llama.cpp



## 🔐 User Ownership

Users own:

- their models
- their projects
- their conversations
- their AI memory
- their workspace

Nothing is stored on Intellix servers unless the user explicitly chooses cloud services.

##OUR IDE should focus on this ports on users local host 9320 if occupied add 1...

