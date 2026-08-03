# Intellix IDE - GitHub Codespaces + Ollama + OpenCode Setup

## 1. Install Ollama
```bash
curl -fsSL https://ollama.com/install.sh | sh
```
**Purpose:** Install the Ollama runtime.

---

## 2. Start Ollama
```bash
ollama serve
```
**Purpose:** Start the Ollama API server.

---

## 3. Check if Ollama is running(on onother terminal tab)
```bash
curl http://127.0.0.1:11434
```
**Purpose:** Verify the Ollama server is active.

---

## 4. View Installed Models
```bash
ollama list
```
**Purpose:** List all downloaded models.

---

## 5. View Running Models
```bash
ollama ps
```
**Purpose:** Show models currently loaded into memory.

---

## 6. Download Qwen2.5 Coder 7B
```bash
ollama pull qwen2.5-coder:7b
```
**Purpose:** Download the primary coding model.

---

## 7. Download Qwen2.5 Coder 3B
```bash
ollama pull qwen2.5-coder:3b
```
**Purpose:** Lightweight fallback coding model.

---

## 8. Download Qwen2.5 Coder 1.5B
```bash
ollama pull qwen2.5-coder:1.5b
```
**Purpose:** Very lightweight fallback model.

---

## 9. Download DeepSeek R1 1.5B
```bash
ollama pull deepseek-r1:1.5b
```
**Purpose:** Lightweight reasoning & coding model.

---

## 10. Download Gemma 4 12B
```bash
ollama pull gemma4:12b
```
**Purpose:** High-quality coding model (requires more RAM).

---

## 11. Run a Model
```bash
ollama run qwen2.5-coder:7b
```
**Purpose:** Start chatting with the model.

---

## 12. Remove a Model
```bash
ollama rm qwen2.5-coder:3b
```
**Purpose:** Free storage by deleting a model.

---

# OpenCode

## 13. Install OpenCode
```bash
curl -fsSL https://opencode.ai/install | bash
```
**Purpose:** Install the OpenCode AI coding agent.

---

## 14. Verify Installation
```bash
opencode --version
```
**Purpose:** Confirm OpenCode is installed.

---

## 15. Configure OpenCode(come back to this after all sub 15's are over
```bash
opencode -m ollama/qwen2.5-coder:3b
```
**Purpose:** Configure OpenCode for local/cloud models.

---

## 15.1 Prepare the config
```
 nano ~/.config/opencode/config.json
```
## 15.2 paste this code and correct the exact name
```
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "ollama": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "Ollama",
      "options": {
        "baseURL": "http://127.0.0.1:11434/v1"
      },
      "models": {
        "qwen2.5-coder:3b": {
          "tools": true
        }
      }
    }
  }
}
```

## 16. Start OpenCode
```bash
opencode
```
**Purpose:** Launch the OpenCode terminal interface.

---

## 17. Open a Specific Project
```bash
opencode /workspaces/intellixIDE
```
**Purpose:** Open a project directly.

---

## 18. OpenCode Help
```bash
opencode --help
```
**Purpose:** Show all available commands.

---

## 19. Show Providers
```bash
opencode providers
```
**Purpose:** View configured AI providers.

---

## 20. List Provider Models
```bash
opencode models ollama
```
**Purpose:** Display models available from the Ollama provider.

---

## 21. Start with a Specific Model
```bash
opencode -m ollama/qwen2.5-coder:7b
```
**Purpose:** Launch OpenCode using a specific Ollama model.

---

# Useful System Commands

## 22. Check Available Memory
```bash
free -h
```
**Purpose:** Display RAM usage.

---

## 23. Check Running Ollama Process
```bash
ps aux | grep ollama
```
**Purpose:** Verify Ollama is running.

---

## 24. Check Available Models via API
```bash
curl http://127.0.0.1:11434/api/tags
```
**Purpose:** Retrieve installed models through the Ollama API.
