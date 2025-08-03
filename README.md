Here's a **README file** for your `Interview Trainer Agent` powered by IBM Watsonx and LangChain with Retrieval-Augmented Generation (RAG). This documentation provides an overview, setup guide, and usage instructions.

---

# 💼 Interview Trainer Agent (Powered by IBM Watsonx + LangChain)

An AI-driven Interview Preparation Assistant designed to personalize and streamline the job interview preparation process using RAG (Retrieval-Augmented Generation), IBM Watsonx, and LangChain.

---

## 📌 Overview

The **Interview Trainer Agent** generates tailored interview questions, answers, and feedback by analyzing the user's job title, resume, and experience level. It uses advanced AI models, retrieves role-specific content from reliable sources, and offers interactive preparation sessions focused on both technical and behavioral skills.

---

## 🔧 Features

* 🔍 **Retrieval-Augmented Generation (RAG)**: Fetches interview data from professional and company-specific sources
* 🎯 **Role-specific Preparation**: Analyzes job title, resume, and experience level to tailor content
* 🧠 **Powered by Meta LLaMA 3-70B on Watsonx**
* 🧰 **Tool Integration**:

  * GoogleSearch
  * DuckDuckGo
  * Wikipedia
  * Weather (for testing utility integration)
* 🧑‍🏫 **Behavioral and Technical Interview Simulation**
* 📈 **Adaptive Questioning**: Adjusts difficulty and focus areas
* 🔐 **Secure and Scalable**: Built on IBM Cloud and Granite foundation models

---

## 🏗️ Architecture

* **Model**: `meta-llama/llama-3-3-70b-instruct`
* **Platform**: IBM Watsonx + IBM Cloud
* **Framework**: LangChain + LangGraph
* **Agents**: ReAct-based agent with memory and tool support

---

## 🚀 Setup Instructions

### 1. Prerequisites

* Python 3.9+
* IBM Watsonx account with valid API token
* Access to IBM Cloud and Watsonx space
* `langchain`, `langchain_ibm`, `ibm_watsonx_ai`, `requests`, etc.

### 2. Environment Configuration

Set your Watsonx `space_id` and `service_url`:

```python
params = {
    "space_id": "your-space-id"
}
```

Ensure token generation is handled via:

```python
credentials = {
    "url": service_url,
    "token": context.generate_token()
}
```

### 3. Tool Setup

Utility tools are created via `create_utility_agent_tool()` for services like Google Search and Wikipedia. Customize the toolset in `create_tools()`.

---

## 🧠 How It Works

* The `generate()` function:

  * Reads input messages (user context, job title, resume, etc.)
  * Creates a LangChain agent with pre-defined tools
  * Runs the ReAct agent to generate interview-related content
  * Returns structured responses for rendering in UI

* The `generate_stream()` function:

  * Provides streaming support for real-time interactions
  * Streams both messages and tool invocations

---

## 📝 Sample Prompt

```json
{
  "messages": [
    { "role": "user", "content": "I am a software engineer with 3 years of experience applying for a backend role at Google. Help me prepare." }
  ]
}
```

---

## ✅ Example Output

```json
{
  "choices": [{
    "message": {
      "role": "assistant",
      "content": "Here are some backend interview questions you should prepare for..."
    }
  }]
}
```

---

## 📂 File Structure

```
interview_trainer_agent/
│
├── agent.py                # Main implementation
├── README.md               # This file
└── requirements.txt        # Required Python packages
```

---

## 🛠️ Customization

* Modify the system prompt in `create_agent()` to tailor the assistant's personality and behavior.
* Extend `create_custom_tool()` to add proprietary or domain-specific tools.
* Restrict tool usage strictly to interview-related domains for focused responses.

---

## 📦 Dependencies

```txt
langchain
langchain_ibm
ibm_watsonx_ai
requests
```

Install with:

```bash
pip install -r requirements.txt
```

---

## 📌 Notes

* Agent uses memory via `MemorySaver()` for multi-turn interactions.
* IBM token-based auth handled dynamically via context.
* Only interview-related questions and tasks should be processed.

---

## 📞 Support

For IBM Watsonx setup or integration help, refer to [IBM Watsonx Documentation](https://dataplatform.cloud.ibm.com/docs/content/wsj/getting-started/welcome-main.html).

---

Let me know if you want this exported to Markdown or a downloadable format.
