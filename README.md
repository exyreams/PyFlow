# 📊 PyFlow: Advanced PYUSD Analysis with GCP Blockchain Node Engine

**Submission for the PayPal x Google Cloud Web3 Bounty** 🚀
**PyFlow** is an analytics platform, presented as a Google Colaboratory notebook, designed for deep analysis of the **PayPal USD (PYUSD)** stablecoin on the Ethereum blockchain. It leverages the unique capabilities of **Google Cloud Platform's Blockchain Node Engine**, specifically its generous free quotas for computationally expensive RPC methods, to provide insights typically inaccessible or cost-prohibitive with standard tools.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/exyreams/PyFlow/blob/main/PyFlow.ipynb)

>[!TIP]
> **Click Badge to Open in Collab**

## 📜 Table of Contents

*   [🤔 Problem Statement](#-problem-statement)
*   [✨ Solution: PyFlow & The GCP Advantage](#-solution-pyflow--the-gcp-advantage)
*   [🚀 Features & Methods Covered](#-features--methods-covered)
*   [⚙️ Setup Instructions](#️-setup-instructions)
    *   [✅ Prerequisites](#-prerequisites)
    *   [🔑 Configuration](#-configuration)
    *   [▶️ Running the Notebook](#️-running-the-notebook)
*   [📖 Usage Guide & Demos 🎬](#-usage-guide--demos-)
    *   [Environment Setup (Cell 1)](#environment-setup-cell-1)
    *   [Configuration & Authentication (Cell 2)](#configuration--authentication-cell-2)
    *   [Analysis Sections (1.1 - 1.11)](#analysis-sections-11---111)
*   [💻 Technical Details](#-technical-details)
    *   [Key Libraries 📚](#key-libraries-)
    *   [Analysis Functions ⚙️](#analysis-functions-️)
*   [📚 Additional Resources & Documentation](#-additional-resources--documentation)
*   [🤝 Contributing](#-contributing)
*   [📄 License](#-license)
*   [🙏 Acknowledgements](#-acknowledgements)

## 🤔 Problem Statement

Analyzing stablecoins like PYUSD often requires more than surface-level transaction data. Understanding complex interactions (DeFi swaps, bridging), debugging failures, optimizing gas, auditing security, or verifying state requires deep execution tracing and state inspection. However, the underlying RPC methods (`debug_traceTransaction`, `trace_replayTransaction`, `stateDiff`, etc.) are computationally intensive. Accessing them via standard RPC providers typically involves:
*  **💸 High Costs:** Significant fees based on computation or request multipliers.
*  **⏱️ Strict Rate Limits:** Limiting the frequency or volume of analysis.
*  **🚫 Limited Availability:** Some advanced methods may not be offered at all.

This creates a barrier to performing thorough, cost-effective analysis, especially for developers, analysts, or smaller teams.

## ✨ Solution: PyFlow & The GCP Advantage
PyFlow addresses this challenge by building directly on **Google Cloud's Blockchain Node Engine**.
**Key Advantage:** GCP uniquely offers **generous free quotas** for computationally expensive, high-multiplier RPC methods (like `debug_traceTransaction` (50x), `trace_replayTransaction` (100x), `eth_getLogs` (50x), `debug_storageRangeAt` (50x), etc.).

PyFlow leverages this by providing a **Google Colab notebook** 📝 that acts as an interactive analysis platform. It allows users to easily execute these powerful GCP methods against specific PYUSD transactions, blocks, or contracts and presents the results with detailed parsing, analysis, and visualizations 📈. This makes deep blockchain intelligence accessible and affordable.

## 🚀 Features & Methods Covered
PyFlow implements analysis workflows for a wide range of advanced RPC methods, focusing on PYUSD insights:
*  **Detailed Execution Tracing:**  `debug_traceTransaction` (callTracer/structLog), `trace_transaction`
*  *Insights:* Internal call flow, gas usage per step, event emission, function parameters, revert debugging.
*  **Block-Level Analysis:**  `trace_block`, `debug_traceBlockByNumber`, `debug_traceBlockByHash`
*  *Insights:* Activity overview for all transactions in a block, contextual analysis around PYUSD txns, block-level gas patterns, MEV hints.
*  **State Replay & Simulation:**  `trace_replayTransaction`, `trace_replayBlockTransactions` (with `stateDiff`, `trace`), `trace_call`
*  *Insights:* Precise state change tracking (balances, storage), debugging failed txns, gas estimation, "what-if" scenario analysis.
*  **State & Data Retrieval:**  `eth_getLogs`, `eth_getCode`, `debug_storageRangeAt`.
*  *Insights:* Efficient event querying (Transfers, Approvals), contract bytecode verification, raw storage inspection, Merkle proof generation and verification.
*  **Network Monitoring:**  `txpool_status`
*  *Insights:* Network congestion analysis, estimated confirmation times, gas price recommendations.
*(See the notebook for detailed explanations and multipliers for each method.)*

## ⚙️ Setup Instructions
Following these steps will allow you to run the PyFlow notebook successfully.

### ✅ Prerequisites
1.  **Google Account:** Required for Google Colab and GCP access.
2.  **Google Cloud Project:** A GCP project with billing enabled (required for API usage, though free quotas are generous). Create one [here](https://console.cloud.google.com/projectcreate).
3.  **Enabled GCP APIs:** Ensure the following APIs are **enabled** in your GCP project:
* Blockchain Node Engine API ([Enable Link](https://console.cloud.google.com/blockchain/rpc?referrer=search&invt=AbupKA))
* Google Drive API ([Enable Link](https://console.cloud.google.com/apis/library/drive.googleapis.com))
* Google Sheets API ([Enable Link](https://console.cloud.google.com/apis/library/sheets.googleapis.com))

**🎬 Setup Video:**

[Prerequisites.webm](https://github.com/user-attachments/assets/755a58e9-be6a-4a55-afe8-a977b88a31a2)

### 🔑 Configuration
1.  **Open the Notebook:** Click the "Open In Colab" badge at the top of this README or directly open the `PyFlow.ipynb` file in Google Colaboratory.
2.  **Edit Cell 2 (🔑 Configuration & Authentication: Connecting to GCP and Ethereum RPC):** This is the **only cell you need to manually edit**.
*  **`BLOCKCHAIN_RPC` Dictionary:** Replace the placeholder URLs with your **full** GCP RPC endpoint URLs (including `?key=...`) for `'mainnet'` and optionally `'holesky'` and `'sepolia'`.
*  **`GCP_PROJECT_ID`:** Replace `"YOUR_PROJECT_ID"` with your actual GCP Project ID string.

**🎬 Configuration Video:**

[Configuration_Authentication.webm](https://github.com/user-attachments/assets/8372ff05-62fa-497d-9144-79742f66e217)

### ▶️ Running the Notebook
1.  **Connect Runtime:** In Colab, ensure you are connected to a runtime (Runtime > Connect to runtime). A standard runtime is usually sufficient, but High-RAM is recommended for large block analyses.
2.  **Run Setup Cells:**
* Run **Cell 1 (🛠️ Environment Setup: Installing Dependencies for PyFlow)** to install dependencies (takes 1-2 minutes).
* Run **Cell 2 (🔑 Configuration & Authentication: Connecting to GCP and Ethereum RPC)**. You will be prompted to authenticate with your Google Account via a pop-up. Follow the instructions. Verify that the output shows successful connections (RPC).
3.  **Run Analysis Cells:** Proceed through the notebook section by section (1.1 through 1.11).
*  **Modify Targets:** In Cell 1.1, you can change the default `TARGET_TX_HASH` and `TARGET_BLOCK_IDENTIFIER`.
*  **Enable Expensive Calls:** Some cells (like `structLog`, `replay*`) have flags (`RUN_... = True/False`). Set them to `True` cautiously to run those analyses.
*  **Use Interactive Widgets:** Some sections provide interactive widgets (dropdowns, text boxes, buttons) for filtering or changing inputs directly in the output.

## 📖 Usage Guide & Demos 🎬
The notebook is structured sequentially, exploring different RPC methods. Watch the demo videos for each section to see it in action.

>  [!TIP]
> For a visual walkthrough of the setup and each analysis section below, please watch the **[Full PyFlow Demo on YouTube]([Demo Video Coming Soon...])**. Refer to this video if any specific demo links below aren't working or if you prefer a comprehensive overview.

### 🛠️ Environment Setup: Installing Dependencies for PyFlow (Cell 1)
Installs all required Python libraries. Run this first.

[Environment Setup.webm](https://github.com/user-attachments/assets/cc4c6550-8995-4a6a-919e-ce05c80e38d2)

### 🔑 Configuration & Authentication: Connecting to GCP and Ethereum RPC (Cell 2)

>  [!WARNING]
> Enter your **`GCP Project ID`** and **`RPC Endpoints`** here before running. Authenticates your session. Check the output summary for successful connections. 

[Configuration_Authentication.webm](https://github.com/user-attachments/assets/8372ff05-62fa-497d-9144-79742f66e217)


### Analysis Sections (1.1 - 1.11)
Each section focuses on one or more related RPC methods. Follow the detailed markdown explanations *within the notebook* for guidance on each method's purpose, GCP value, PYUSD insights, workflow, and interpreting results.

*  1.1 🎯 Analysis Targets & Utility Functions. 
*(Modify targets here if desired)*.
Go to Explorer [PYUSD Transactions](https://etherscan.io/token/0x6c3ea9036406852006290770bedfcaba0e23a0e8), choose a transaction hash and its block.

   [1.1Analysis Targets & Utility Functions.webm](https://github.com/user-attachments/assets/cf830cca-17d8-4e10-bae8-cab98cd3805a)

*  1.2 🔍 `debug_traceTransaction` - Deep Dive into Transaction Execution
   * 1.2.1 Using `callTracer`: Mapping Internal Calls, Gas & Events (Recommended)
      *  *Demo:* [Demo Video Coming Soon...]
   * 1.2.2 Using `structLog` Tracer: Opcode-Level Execution Analysis (Use Cautiously)   
      *  *Demo:* [Demo Video Coming Soon...]
*  **1.3 `eth_getLogs`:** Efficiently fetch PYUSD `Transfer` events.
*  *Demo:* [Demo Video Coming Soon...]
*  **1.4 `eth_getCode`:** Analyze contract bytecode (PYUSD, from Tx, or Custom).
*  *Demo:* [Demo Video Coming Soon...]
*  **1.5 `trace_block`:** Summary trace of all transactions in a block.
*  *Demo:* [Demo Video Coming Soon...]
*  **1.6 `debug_traceBlockBy*`:** Detailed trace of all transactions in a block.
*  *Demo:* [Demo Video Coming Soon...]
*  **1.7 `debug_traceCall`, `eth.call`, `eth.estimate_gas`:** Advanced Simulation of PYUSD Transactions.
*  *Demo:* [Demo Video Coming Soon...]
*  **1.8 `trace_transaction`:** Alternative detailed transaction trace.
*  *Demo:* [Demo Video Coming Soon...]
*  **1.9 `trace_replay*`:** Re-execute transactions/blocks with state diffs (High Cost!).
*  *Demo:* [Demo Video Coming Soon...]
*  **1.10 `debug_storageRangeAt`:** Inspect raw contract storage slots.
*  *Demo:* [Demo Video Coming Soon...]
*  **1.11 `txpool_status`:** Analyze network congestion.
*  *Demo:* [Demo Video Coming Soon...]

## 💻 Technical Details

### Key Libraries 📚

*  `web3.py`: Ethereum interaction.
*  `google-cloud-bigquery`: Accessing public datasets.
*  `pandas`: Data manipulation and tables.
*  `plotly`, `matplotlib`, `graphviz`, `pygraphviz`: Visualizations.
*  `rich`: Enhanced terminal output formatting.
*  `ipywidgets`: Interactive notebook controls.
*  `eth-utils`, `rlp`: Ethereum utility functions.

### Analysis Functions ⚙️
The notebook contains numerous Python functions for fetching data, parsing results, performing analysis (gas, flow, patterns), and generating visualizations. Key functions are documented within the code cells.

## 📚 Additional Resources & Documentation
Here are valuable resources related to GCP Web3 services, PYUSD, and Ethereum:

**Google Cloud Platform:**
   *   **GCP Blockchain Node Engine:**
       *   [Overview](https://cloud.google.com/blockchain-rpc/docs/overview)
       *   [Quickstart Guide](https://cloud.google.com/blockchain-rpc/docs/quickstart)
       *   [Ethereum API Methods](https://cloud.google.com/blockchain-rpc/docs/rpc-api)
   *   **GCP Crypto Public Datasets on BigQuery:**
       *   [Overview & Discovery](https://cloud.google.com/application/web3/discover)
       *   [BigQuery Crypto Public Datasets HOWTO](https://cloud.google.com/application/web3/discover/products/public-blockchain-datasets-available-in-bigquery)
       *   [BigQuery Ethereum Dataset (Marketplace)](https://console.cloud.google.com/marketplace/product/bigquery-public-data/blockchain-analytics-ethereum-mainnet-us)
   *   **Other GCP Tools:**
       *   [Ethereum Faucet (Sepolia & Holesky)](https://cloud.google.com/application/web3/faucet)
       *   [Google AI Studio](https://aistudio.google.com/prompts/new_chat)
       *   [Google Colaboratory](https://colab.google/)
       *   [BigQuery Service](https://cloud.google.com/bigquery)
       *   [Experimental: Real-time Ethereum Events via Pub/Sub](https://cloud.google.com/application/web3/discover/products/realtime-evm-blockchain-events-with-pubsub?e=48754805)

**PayPal USD (PYUSD):**
*   [About PYUSD (PayPal Developer Blog)](https://developer.paypal.com/community/blog/pyusd-stablecoin/)
*   [PYUSD Contract Source Code (Paxos GitHub)](https://github.com/paxosglobal/pyusd-contract)
*   [PYUSD Contract on Etherscan (View ABI)](https://etherscan.io/token/0x6c3ea9036406852006290770bedfcaba0e23a0e8)
*   [PYUSD Contract on Sourcify (View ABI)](https://sourcify.dev/#/lookup/0x6c3ea9036406852006290770BEdFcAbA0e23A0e8)
*   [PYUSD Faucet (Paxos)](https://faucet.paxos.com/)

**Ethereum:**
*   [Ethereum JSON-RPC API Documentation](https://ethereum.org/en/developers/docs/apis/json-rpc/)
*   [How to Read Data with JSON-RPC (Alchemy Docs)](https://docs.alchemy.com/docs/how-to-read-data-with-json-rpc)
*   [Understanding MEV](https://ethereum.org/en/developers/docs/mev/) *(General concept link)*

*(Note: The links provided in the original hackathon brief were used to create this list.)*


## 🤝 Contributing

We welcome contributions to PyFlow! Please feel free to submit issues, feature requests, or pull requests.


## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


## 🙏 Acknowledgements

*  **Google Cloud Platform:** For providing the Blockchain Node Engine with generous free access to advanced RPC methods.
*  **PayPal:** For creating the PYUSD stablecoin.
*  **StackUp:** For hosting the bounty challenge.
* Open-source libraries used in this project.
---
PyFlow by **`@exyreams`** - Developed for the "Seamless Transactions, Infinite Possibilities" hackathon.
