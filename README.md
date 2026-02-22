# ⛓️ VyseForge

> **Multi-Agent AI Blockchain Development Platform — Built on Monad**

VyseForge is a no-code DApp factory powered by 8 specialized AI agents. Describe any blockchain project idea in plain English — VyseForge designs the architecture, writes Solidity contracts optimized for Monad, runs a full test suite on Monad Testnet, deploys the contract, generates a DApp frontend, and hosts it at a shareable URL. Zero code required from the user.

---

## 🎯 What It Does

```
User types: "Build an NFT marketplace with royalties"
                          ↓
       8 AI agents take over automatically
                          ↓
    ✅ Smart contracts written & optimized for Monad
    ✅ 5–10 tests run on Monad Testnet
    ✅ Contract deployed to Monad
    ✅ DApp frontend generated with MetaMask support
    ✅ Live hosted DApp URL delivered to user
```

---

## 🏗️ Project Category

| Category | Description |
|---|---|
| **Primary** | AI Agents + Blockchain |
| **Secondary** | Developer Tooling / No-Code |
| **Tertiary** | DApp Infrastructure on Monad |

---

## ✨ Key Features

- **8 Specialized AI Agents** — Each agent has a single focused responsibility, from parsing intent to deploying on-chain
- **Monad-Native** — Contracts are optimized specifically for Monad's parallel EVM, MonadDB storage model, and gas behavior
- **Multi-LLM Support** — Users bring their own API key from Anthropic, OpenAI, Google, Groq, or Mistral
- **Auto Test Suite** — Tester Agent runs 5–10 real test cases on Monad Testnet before deployment
- **Self-Healing Pipeline** — Review Agent triages failures and routes fixes back automatically (up to 10 retries)
- **DApp Hosting** — Generated frontend is hosted at a live shareable URL on your platform
- **No Code Required** — From idea to live DApp in one prompt

---

## 🤖 The 8 Agents

| Agent | Role |
|---|---|
| 🧠 **Intent Agent** | Parses user prompt → extracts contract type, features, chain params |
| 📚 **Knowledge Agent** | Shared Monad & Solidity oracle — always on, queried by all agents |
| 🏗️ **Architect Agent** | Designs project blueprint, asks clarifying questions if needed |
| ⚡ **Coder Agent** | Writes Solidity contracts + Web3.py deployment scripts |
| 🧪 **Tester Agent** | Runs 5–10 tests on Monad Testnet, reports pass/fail + gas |
| 🔍 **Review Agent** | Triages failures — routes fix to Coder or Architect |
| 🚀 **Deployer Agent** | Deploys verified contract to Monad, returns explorer link |
| 🖥️ **Frontend Agent** | Generates DApp HTML + MetaMask UI from contract ABI |

---

## 🛠️ Tech Stack

### Platform
| Layer | Technology |
|---|---|
| Frontend UI | HTML + Tailwind CSS + Vanilla JavaScript |
| Demo App | Streamlit |
| Backend | Django + Django Channels |
| Database | MySQL |
| Real-time | WebSockets via Django Channels |
| Cache / Broker | Redis |

### Agent Layer
| Component | Technology |
|---|---|
| Orchestration | LangGraph |
| LLM Interface | LangChain Core |
| LLM Providers | Anthropic, OpenAI, Google, Groq, Mistral |
| Knowledge Store | ChromaDB (RAG) |
| Data Validation | Pydantic v2 |
| Logging | Loguru |

### Blockchain
| Component | Technology |
|---|---|
| Chain | **Monad** (Testnet + Mainnet) |
| On-chain Interaction | Web3.py |
| Solidity Compiler | py-solc-x |
| Contract Testing | Ape Framework |
| Explorer | MonadVision (testnet.monadvision.com) |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- Node.js (for OpenZeppelin)
- MetaMask wallet
- API key from any supported LLM provider
- Testnet MON from [faucet.monad.xyz](https://faucet.monad.xyz)

### Installation

```bash
# Clone the repo
git clone https://github.com/yourusername/vyseforge.git
cd vyseforge

# Install Python dependencies
pip install streamlit web3 py-solc-x eth-account python-dotenv langchain langgraph chromadb

# Install OpenZeppelin contracts
npm init -y
npm install @openzeppelin/contracts
```

### Run the Demo App

```bash
streamlit run vyseforge_app.py
```

### Environment Setup

Create a `.env` file in your project root:

```env
DEPLOY_PRIVATE_KEY=your_wallet_private_key_here
```

> ⚠️ Never commit your `.env` file. Add it to `.gitignore` immediately.

---

## 📋 Local Deployment Guide

### Step 1 — Save Generated Files

After running the pipeline, save the three generated files:

```
your-project/
├── NFTMarketplace.sol    ← generated Solidity contract
├── deploy.py             ← generated deployment script
├── interact.py           ← generated interaction script
└── .env                  ← your private key
```

### Step 2 — Add Monad Testnet to MetaMask

| Field | Value |
|---|---|
| Network Name | Monad Testnet |
| RPC URL | https://testnet-rpc.monad.xyz |
| Chain ID | 10143 |
| Currency | MON |
| Explorer | https://testnet.monadvision.com |

### Step 3 — Get Testnet MON

Visit [faucet.monad.xyz](https://faucet.monad.xyz) and paste your wallet address to receive free testnet MON.

### Step 4 — Deploy

```bash
python deploy.py
```

Expected output:
```
✅ Compiler ready
✅ Compiled successfully
✅ Connected to Monad Testnet (Chain ID: 10143)
👛 Wallet  : 0xYourAddress
💰 Balance : 1.5 MON
🚀 Deploying to Monad Testnet...
✅ Contract verified on-chain (4821 bytes)
=======================================================
✅ CONTRACT DEPLOYED SUCCESSFULLY
=======================================================
📄 Contract : 0xYourContractAddress
🔗 Explorer : https://testnet.monadvision.com/address/0x...
⛽ Gas Used : 1,243,100
💾 Saved to deployment.json
```

### Step 5 — Interact

```bash
python interact.py
```

This will mint an NFT, list it for sale, and buy it — all confirmed on Monad Testnet.

### Step 6 — Verify On-Chain

Visit [testnet.monadvision.com](https://testnet.monadvision.com) and search your contract address to see live transactions, NFTs, and events.

---

## 🔄 Pipeline Flow

```
User Prompt
     │
     ▼
Intent Agent ──────────────────────► Knowledge Agent
     │                                    ▲  ▲  ▲
     ▼                                    │  │  │
Architect Agent ────────────────────────► │  │  │
     │ (asks user if ambiguous)           │  │  │
     ▼                                    │  │  │
Coder Agent ────────────────────────────► │  │  │
     │                                       │  │
     ▼                                       │  │
Tester Agent (5–10 tests on Monad Testnet)   │  │
     │                                          │
     ├── FAIL ──► Review Agent ─► Coder/Architect (max 10 retries)
     │
     └── PASS ──► Deployer Agent ──► Monad Mainnet/Testnet
                       │
                       ▼
                 Frontend Agent ──► Hosted DApp URL ──► User
```

---

## 🔐 Security

- User API keys encrypted with **AES-256** before storage
- Generated code runs in **Docker sandboxes** — isolated from host
- **Ephemeral wallets** generated per deployment — no shared hot wallet
- DApp frontends sanitized with **bleach** before serving
- Hosted DApps isolated on subdomain to prevent session hijacking
- Rate limiting per user to prevent pipeline abuse
- Prompt injection guardrails in all agent system prompts

---

## 💡 What You Can Build

- NFT Collections and Marketplaces
- ERC-20 Tokens with Vesting Schedules
- DeFi Staking and Yield Contracts
- DAOs with On-chain Voting and Treasury
- Token Launchpads
- Multi-sig Wallets
- Any custom smart contract

---

## 🌐 Why Monad

Monad's parallel EVM execution allows contracts generated by VyseForge to run significantly more efficiently than on standard EVM chains. The Knowledge Agent is loaded with Monad-specific documentation — parallel execution rules, MonadDB storage optimization patterns, and gas behavior — ensuring every generated contract is natively optimized for Monad rather than just being generic EVM code deployed on a new chain.

---

## 📁 Project Structure

```
vyseforge/
│
├── vyseforge_app.py          ← Streamlit demo app
│
├── agents/
│   ├── graph.py              ← LangGraph pipeline
│   ├── state.py              ← Shared state object (Pydantic)
│   ├── llm_factory.py        ← Multi-provider LLM abstraction
│   ├── intent_agent.py
│   ├── knowledge_agent.py
│   ├── architect_agent.py
│   ├── coder_agent.py
│   ├── tester_agent.py
│   ├── review_agent.py
│   ├── deployer_agent.py
│   └── frontend_agent.py
│
├── blockchain/
│   ├── compiler.py           ← py-solc-x wrapper
│   ├── deployer.py           ← Web3.py deployment
│   ├── tester.py             ← Ape Framework test runner
│   └── monad_config.py       ← RPC endpoints, chain IDs
│
├── knowledge/
│   ├── vectorstore.py        ← ChromaDB setup
│   ├── ingest.py             ← Load docs into ChromaDB
│   └── docs/                 ← Monad docs, Solidity refs, ERC standards
│
├── backend/
│   ├── manage.py             ← Django entry point
│   └── apps/
│       ├── projects/         ← Project models & API
│       ├── users/            ← Auth & API key management
│       ├── hosting/          ← DApp hosting views
│       └── websockets/       ← Django Channels consumers
│
├── .env.example
├── requirements.txt
└── docker-compose.yml
```

---

## 🗺️ Roadmap

- [x] Multi-agent pipeline design
- [x] Streamlit demo app
- [x] Smart contract generation (ERC-721)
- [x] Monad Testnet deployment
- [ ] LangGraph agent implementation
- [ ] Django backend with WebSocket streaming
- [ ] ChromaDB knowledge base with Monad docs
- [ ] DApp frontend generation from ABI
- [ ] DApp hosting on platform
- [ ] Full Django web platform
- [ ] Mainnet deployment support

---

## 👤 Author

Built for **Monad Blitz Hackathon**

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">
  <strong>Built on Monad · Powered by AI Agents · Zero Code Required</strong>
</div>
