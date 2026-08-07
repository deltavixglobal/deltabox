# DeltaBox

<div align="center">
<img src="assets/logo.ico" width="120" height="120" alt="DeltaBox Logo" />
  <h3>Orchestration Engine for Agentic AI</h3>
  <p>A self-hosted, highly scalable graphical environment orchestration platform designed specifically to give AI Agents a "Body".</p>
  
  <p>
    <a href="#overview">Overview</a> •
    <a href="#the-problem--the-solution">The Solution</a> •
    <a href="#core-offerings">Offerings</a> •
    <a href="#architecture">Architecture</a> •
    <a href="#installation">Installation</a> •
    <a href="#delta-control-protocol">API</a> 
  </p>
</div>

---

## 🚀 Overview

Large Language Models (LLMs) and Agentic AI have evolved to act as intelligent "Brains", capable of complex reasoning and task planning. However, they lack a dedicated "Body" to execute graphical, real-world interactions.

**DeltaBox** bridges this gap by providing **Full Computer Automation**. It is an enterprise-grade orchestration engine that instantly spins up isolated, containerized Linux desktop environments. Whether you are running highly intelligent, autonomous agents or simple, rule-based "dumb" bots, DeltaBox gives them a complete sandbox to operate in. Through the native **Delta Control Protocol** and **Model Context Protocol (MCP)**, your AI agents can visually perceive the entire screen using OS-level Accessibility Trees (AT-SPI2) and physically interact with *any* application—from web browsers to desktop terminals—using human-like mouse and keyboard movements.

## 🧠 The Problem & The Solution

**The Problem:** Traditional automation tools rely on brittle, application-specific hooks (like Puppeteer for browsers or WinAppDriver for Windows). They break instantly when UI layouts change, use Shadow DOMs, or rely heavily on dynamic rendering. They force the AI to read thousands of tokens of useless structural code just to click a button.

**The Solution:** DeltaBox provides a true **Visual Sandbox for the entire Operating System**. Your AI agent "sees" exactly what a human sees (via highly token-optimized AT-SPI2 semantic trees across the entire desktop) and clicks exactly where a human would click (via coordinate-based API commands mapped to X11). Because the interaction happens at the OS level, it is completely agnostic to underlying application code or website structure, perfectly modeling true human-computer interaction.

## ✨ Core Offerings

DeltaBox is built for massive scale, precision, and agentic autonomy.

### 1. Humanized Biomechanical Interaction
DeltaBox does not instantly teleport the mouse. The **Delta Control Protocol** includes built-in physics engines that simulate human interaction:
*   **Bezier Curve Mouse Movements**: Complex mathematical curves simulate natural hand movements to target coordinates.
*   **Micro-Tremor Injection**: Injects localized noise simulating human hand jitter.
*   **Natural Typing Cadence**: Keyboard commands simulate human typing delays and errors.

### 2. Elastic Swarm Orchestration
Manage your agent infrastructure dynamically. The Swarm Manager allows you to programmatically spin up 10, 50, or 100 isolated GUI containers on-demand, execute parallel agentic workflows, and tear them down gracefully to free up compute resources.

### 3. Integrated Proxy Management
For heavy autonomous data gathering, IP diversity is critical. DeltaBox offers native proxy integration. When spawning a new node, you can instantly attach sticky or rotating proxies to ensure that every container maintains a unique network fingerprint and origin IP.

### 4. The Cloud Console
While your AI agents operate in the background, you maintain complete oversight. The **DeltaBox Cloud Console** is a premium, web-based dashboard that allows human operators to view live streams of active nodes, interact manually with the environment if an agent gets stuck, and monitor system resources in real-time.

---

## 🏗️ Architecture

DeltaBox is designed with a microservice architecture to ensure stability and isolation:

- **The Swarm Manager (FastAPI)**: The central brain of the infrastructure. It communicates directly with the Docker daemon to allocate resources, deploy containers, and route proxy traffic.
- **Delta Nodes**: The individual execution sandboxes. Each node is a lightweight, headless X11 environment running a complete graphical desktop, an accessibility tree parser (AT-SPI), and the local API receiver.
- **Nginx Reverse Proxy**: Securely routes traffic and serves the real-time Cloud Console dashboard to operators.

---

## 📦 Installation & Setup

### Prerequisites
- Docker Engine (v24.0+)
- Docker Compose
- Minimum 4GB RAM (8GB+ recommended for multiple concurrent nodes)
- Cross-Platform: Works on **Windows (WSL2)**, **macOS (Apple Silicon & Intel)**, and **Linux**.

### 1. Clone the Repository
```bash
git clone https://github.com/deltavix/deltabox.git
cd deltabox
```

### 2. Configure Environment (Optional)
You can configure the global resource limits for the Swarm Manager in the `compose.yml` file:
```yaml
  swarm-manager:
    environment:
      - POOL_TOTAL_CPUS=4    # Max CPU cores the swarm can utilize
      - POOL_TOTAL_RAM_GB=8  # Max RAM the swarm can allocate
```

### 3. Spin Up the Stack
Initialize the orchestration stack. This builds the Swarm Manager and deploys the Cloud Console.
```bash
docker compose up -d
```

### 4. Access the Platform
Navigate to the Cloud Console to begin deploying Delta Nodes:
```
http://localhost:9090
```

---

## 🔌 Delta Control Protocol (API Reference)

Once a Delta Node is spawned, it exposes the **Delta Control Protocol V1.0**. Your AI Agent uses this API to interact with the environment. 

A full interactive Swagger UI is generated dynamically for every node at `http://localhost:<NODE_PORT>/docs`.

### Core Endpoints

#### Visual Perception
```http
GET /system/screenshot
```
Returns a high-resolution base64 or binary image of the current desktop state, ready to be ingested by Multimodal LLMs (e.g., GPT-4o, Claude 3.5 Sonnet).

#### Humanized Mouse Control
```http
POST /mouse/move
```
```json
{
  "x": 850,
  "y": 420,
  "profile": "normal"
}
```
Moves the cursor to the requested coordinates using natural Bezier curves.

#### Keyboard Interaction
```http
POST /keyboard/type
```
```json
{
  "text": "Hello, World!",
  "delay_ms": 150
}
```
Types the string into the currently focused window with simulated human keystroke delays.

#### Terminal Execution
```http
POST /system/command
```
Allows the agent to execute internal shell commands, such as launching applications or retrieving system logs.

---

## 👨‍💻 Created By

**DeltaBox** was created and open-sourced by **Palash Kumbalwar** at **Deltavix Global** to empower developers building the next generation of autonomous AI systems.

- 🔗 **LinkedIn**: [Palash Kumbalwar](https://www.linkedin.com/in/palashkumbalwar)
- 🌐 **Company**: [Deltavix Global](https://www.deltavixglobal.com)
- 📧 **Contact for Customization**: [info@deltavixglobal.com](mailto:info@deltavixglobal.com)

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
