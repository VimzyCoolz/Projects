# Intellix IDE Architecture & Roadmap

🎯 **Vision**

Build **Intellix IDE**, a browser-based AI development environment that is local-first rather than server-first.
when i say local i mean user runs it on his machine, so in web startup request user to insert base url of his server it can be local/github workspace/vps etc

The user owns:

* their models,
* their AI memory,
* their projects,
* their workspace.

Your servers are not responsible for running the AI.

---

## 🏗 Foundation

* **✅ Build directly on your own foundation.**
* Structure everything from the ground up.
* Design a clean architecture.
* Gradually build out Intellix IDE.

The objective is to establish a robust, independent product architecture.

---

## 🔄 Architectural Model

```text
Browser
   │
Intellix Runtime (localhost)/base url
   │
LLM

```

The **Runtime** becomes the center of the system.

---

## 📦 Intellix Workspace(which will be created when user runs intellix backend)

Instead of installing multiple components separately, users create or open an Intellix Workspace.

The workspace contains following folders-some will contain files while others will come later time:

* Runtime
* Inference Engine
* AI Models(this will be downloaded when the user is on the web dashboard when user selects the model-because we have base url its easy to download to where base url is)
* Projects
* AI Memory
* Chat History
* Settings
* Cache

The workspace is portable between devices. and is created at the beginning(first launch of the site) [import workspace] [ Create workspace]-when user selects import workspace it means the intellix runtime was already running this means we should only request for base url/local host address, when he chooses create workspace thats when we request this data: BASE/LOCAL URL, MODEL NAME(MODEL NAME SHOULD have SOMETHING LIKE ollama/) but we should not limit the user by only supporting ollama, user can download other inference onother time but our runtime currently will only download ollama inference engine

### Responsibilities of local runtime:

* pull AI model using ollama(default) and if there is other engine user has installed support it
* Manage installed models.
* Start/stop models.
* Expose a localhost/base url API.
* Manage AI memory.
* Manage projects.
* import workspaces.
* export workspaces.
* Manage updates.
* download inference engine (ollama by default.)
* Detect workspace.
* Load configuration.
* Start inference engine.
* Stop inference engine.
* Health monitoring.
* API server.
* Version management.

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
* **Cloud**
* • OpenRouter
* • OpenAI
* • Anthropic


* **Local**
* • USE IT WHERE USER CAN SEARCH AI MODEL FROM HUGGING FACE AND DOWNLOAD IT TO HIS WORKSPACE





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

Each workspace contains a configuration file that allows Intellix Runtime to restore the user's environment automatically using whether localhost or any valid base url provided by the user.

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

* Docker
* Kubernetes
* Flutter
* Unity
* Git extensions
* Database tools
* Custom AI providers
* Community plugins

The Plugins folder may remain empty until plugins are installed.

## 🤖 AI Model Architecture

Model Sources

* Hugging Face
* Local Folder
* USB
* Imported Workspace

Inference Engines

* Ollama
* LM Studio
* llama.cpp

## 🔐 User Ownership

Users own:

* their models
* their projects
* their conversations
* their AI memory
* their workspace

Nothing is stored on Intellix servers unless the user explicitly chooses cloud services.

OUR IDE should focus on this ports on users local host 9320 if occupied add 1...

## runtime can be organised this way
Runtime

├── API Server

├── Workspace Service

├── Model Service

├── Engine Service

├── Memory Service

├── Update Service

├── Plugin Service

# 🚀 Intellix IDE TODO Roadmap

## 📋 Phase 0 — Planning

* [x] Define product vision.
* [x] Decide on Local-First architecture.
* [x] Decide on Intellix Workspace.
* [x] Define Runtime responsibilities.
* [x] Define Workspace structure.
* [x] Define Adapter architecture.
* [x] Create architecture documentation.

---

# 🏗 Phase 1 — Proof of Concept (Highest Priority)

Goal:
Browser (Public URL) → Intellix Runtime (localhost) → AI Model

## Runtime

* [ ] Create Intellix Runtime project.
* [ ] Choose default localhost port (9320).
* [ ] Create Runtime API server.
* [ ] Implement `/api/v1/health`.
* [ ] Implement `/api/v1/version`.
* [ ] Implement CORS support.
* [ ] Test browser ↔ localhost communication.

## Browser

* [ ] Create simple test webpage.
* [ ] Call Runtime health endpoint.
* [ ] Display Runtime status.
* [ ] Handle Runtime unavailable state.

---

# 🤖 Phase 2 — Local AI

## Model Support

* [ ] Connect llama.cpp.
* [ ] Connect Ollama.
* [ ] Connect LM Studio.
* [ ] Design Engine Manager.

## Chat

* [ ] Implement `/api/v1/chat`.
* [ ] Stream AI responses.
* [ ] Display responses in browser.

---

# 📦 Phase 3 — Workspace

## Workspace

* [ ] Create Workspace.
* [ ] Open Workspace.
* [ ] Import Workspace.
* [ ] Export Workspace.

## Workspace Structure

* [ ] Runtime/
* [ ] Models/
* [ ] Projects/
* [ ] Memory/
* [ ] Chat/
* [ ] Settings/
* [ ] Cache/
* [ ] Plugins/
* [ ] config.json

## Configuration

* [ ] Read config.json.
* [ ] Save config.json.
* [ ] Support relative paths.
* [ ] Workspace versioning.

---

# 🧠 Phase 4 — Runtime

## Runtime Managers

* [ ] Workspace Manager.
* [ ] Model Manager.
* [ ] Engine Manager.
* [ ] Memory Manager.
* [ ] API Server.
* [ ] Update Manager.

---

# 🤖 Phase 5 — AI Models

## Sources

* [ ] Hugging Face.
* [ ] Local Folder.
* [ ] USB.
* [ ] Imported Workspace.

## Model Management

* [ ] Download models.
* [ ] Delete models.
* [ ] Update models.
* [ ] Search models.
* [ ] Verify downloaded models.

---

# 🔌 Phase 6 — Adapters

## Local

* [ ] llama.cpp Adapter.
* [ ] Ollama Adapter.
* [ ] LM Studio Adapter.

## Cloud

* [ ] OpenRouter Adapter.
* [ ] OpenAI Adapter.
* [ ] Anthropic Adapter.
* [ ] Gemini Adapter.

---

# 💻 Phase 7 — IDE

## Editor

* [ ] Monaco Editor.
* [ ] File Explorer.
* [ ] Terminal.
* [ ] AI Chat.
* [ ] Settings.

## Git

* [ ] GitHub Authentication.
* [ ] Clone Repository.
* [ ] Commit.
* [ ] Push.
* [ ] Pull.
* [ ] Branch Management.

---

# 🧠 Phase 8 — Memory

* [ ] Conversation history.
* [ ] AI memory.
* [ ] Workspace memory.
* [ ] Context restoration.

---

# 🌐 Phase 9 — Offline Mode

* [ ] Offline AI chat.
* [ ] Offline project editing.
* [ ] Offline memory.
* [ ] Offline workspace.
* [ ] Detect internet availability.
* [ ] Online / Offline indicator.

---

# ☁ Phase 10 — Cloud

* [ ] Cloud login.
* [ ] Cloud providers.
* [ ] Optional cloud sync.
* [ ] Workspace sync.

---

# 🔌 Phase 11 — Plugins

* [ ] Plugin API.
* [ ] Plugin Manager.
* [ ] Install plugin.
* [ ] Remove plugin.
* [ ] Enable/Disable plugin.

---

# 🎨 Phase 12 — UI

* [ ] Workspace creation wizard.
* [ ] Runtime status.
* [ ] Model Manager UI.
* [ ] Download Manager.
* [ ] Settings redesign.
* [ ] Theme support.

---

# 🧪 Phase 13 — Foundation Setup & Integration



* [ ] Initialize foundation architecture.


* [ ] Implement core structure.


* [ ] Connect Runtime.


* [ ] Test local-first architecture.


* [ ] Finalize Intellix IDE standalone branding.



---

# 🧪 Phase 14 — Testing

* [ ] Windows.
* [ ] Linux.
* [ ] macOS.
* [ ] External SSD.
* [ ] USB Drive.
* [ ] Workspace portability.
* [ ] Offline mode.
* [ ] Cloud mode.

---

# 📚 Phase 15 — Documentation

* [ ] Installation Guide.
* [ ] Runtime Guide.
* [ ] Workspace Guide.
* [ ] Plugin Guide.
* [ ] API Documentation.
* [ ] Developer Documentation.

---

# 🎯 Future Ideas

* [ ] Workspace encryption.
* [ ] Workspace compression.
* [ ] Workspace snapshots.
* [ ] AI model marketplace.
* [ ] Plugin marketplace.
* [ ] Multi-workspace support.
* [ ] Team workspaces.
* [ ] LAN collaboration.
