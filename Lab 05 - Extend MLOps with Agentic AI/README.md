# Lab 05: Extend MLOps with Agentic AI

This lab guides you through developing an Agentic AI solution using AgentLab in watsonx.ai. You'll create a conversational agent that allows users to query customer repurchase predictions using natural language.

---

## Overview

In this lab, you will:
- Create an AI agent using AgentLab in watsonx.ai
- Configure the agent with custom prompts
- Deploy Python Engine for custom tool execution
- Create a Python function to retrieve customer features
- Integrate with the deployed ML model endpoint
- Test the agent with natural language queries
- Optionally deploy the agent as an API

---

## Lab Steps

### [Step 1: Create AgentLab](./01-create-agentlab.md)
Set up an AI agent that can understand and process natural language queries.

**What you'll do:**
- Access your watsonx.ai project
- Create a new agent asset
- Configure agent name and description
- Set up advanced configuration with custom prompts
- Save the agent with autosave enabled

**Key Configurations:**
- **Agent Name**: Repurchase Agent
- **Purpose**: Get customer repurchase predictions via natural language
- **Configuration**: Custom prompt from prompt.txt file

---

### [Step 2: Create Python Function](./02-create-python-function.md)
Build a custom tool that connects the agent to your ML model and data sources.

**What you'll do:**
- Deploy Python Engine in deployment space
- Retrieve COS connection ID
- Configure secrets for API access
- Define custom tool with input schema
- Write Python code to query feature store
- Integrate with model endpoint for predictions
- Test the custom tool
- Test agent with natural language queries

**Key Components:**
- **Python Engine**: Executes custom Python code
- **Secrets**: API keys, URLs, connection IDs, endpoint URLs
- **Custom Tool**: Retrieves features and calls model endpoint
- **Integration**: Connects feature store, model, and agent

---

## Prerequisites

Before starting this lab, ensure you have:
- Completed [Lab 01: Create your first watsonx project](../Lab%2001%20-%20Create%20your%20first%20watsonx%20project/README.md)
- Completed [Lab 02: Perform EDA and feature engineering](../Lab%2002%20-%20Perform%20EDA%20and%20feature%20engineering/README.md)
- Completed [Lab 03: Develop and Deploy ML Model](../Lab%2003%20-%20Develop%20and%20deploy%20ML%20model/README.md)
- Completed [Lab 04: Monitor and Govern Live Model](../Lab%2004%20-%20Monitor%20and%20govern%20live%20model/README.md)
- Deployed model endpoint from Lab 03
- Feature store CSV file in Cloud Object Storage
- COS connection created in Lab 01

---

## Expected Outcomes

By the end of this lab, you will have:
- ✅ Created an AI agent using AgentLab
- ✅ Configured custom prompts for agent behavior
- ✅ Deployed Python Engine for custom tools
- ✅ Created custom tool to retrieve customer features
- ✅ Integrated agent with ML model endpoint
- ✅ Tested agent with natural language queries
- ✅ Enabled conversational interface for predictions

**Key Outputs:**
- Functional AI agent that understands natural language
- Custom Python tool for feature retrieval and prediction
- Chat interface for querying customer repurchase predictions
- Optional: Deployed agent API for third-party integration

---

## Key Concepts

**AgentLab** is IBM's platform for building AI agents that:
- Understand natural language queries
- Execute custom tools and functions
- Integrate with external APIs and data sources
- Provide conversational interfaces
- Can be deployed as APIs

**Custom Tools** enable agents to:
- Execute Python code
- Access external data sources
- Call ML model endpoints
- Process and transform data
- Return structured responses

**Agentic AI** combines:
- **Natural Language Understanding**: Interprets user queries
- **Tool Execution**: Runs custom functions to retrieve data
- **Model Integration**: Calls ML endpoints for predictions
- **Response Generation**: Provides human-readable answers

---

## Architecture

The agent workflow:
1. **User Query**: Natural language request (e.g., "get prediction for customer 1")
2. **Agent Processing**: Understands intent and extracts parameters
3. **Tool Execution**: Calls custom Python function
4. **Feature Retrieval**: Queries feature store from COS
5. **Model Prediction**: Sends features to ML endpoint
6. **Response**: Returns prediction in natural language

---

## Use Cases

This agentic AI solution enables:
- **Business Users**: Query predictions without technical knowledge
- **Customer Service**: Get real-time repurchase predictions
- **Sales Teams**: Identify high-value customers
- **Marketing**: Target customers likely to repurchase
- **API Integration**: Embed predictions in applications

---

## Additional Resources

- [IBM watsonx AgentLab Documentation](https://www.ibm.com/docs/en/watsonx/saas?topic=agents-overview)
- [Custom Tools Guide](https://www.ibm.com/docs/en/watsonx/saas?topic=agents-custom-tools)
- [Python Function Development](https://www.ibm.com/docs/en/watsonx/saas?topic=tools-python-functions)
- [Agent Deployment Guide](https://www.ibm.com/docs/en/watsonx/saas?topic=agents-deploying)
