# Weather Query Workflow Agent

This repository contains a simple workflow-based agent that answers questions related to weather by interacting with a weather API. The agent uses `langgraph` to set up a workflow that utilizes an LLM (Language Learning Model) to respond to questions and call external tools as necessary. For example, it can respond to the question, "Will it rain in Bangalore, India today?" by querying weather data and providing the user with a clear response.

## Features

- Uses an LLM to interpret and answer questions.
- Integrates with external tools to fetch current weather data.
- Customizable workflow setup using `StateGraph` and `ToolNode` from `langgraph`.
- Supports continuous conversation flow by sending responses back to the LLM as needed.

## Installation

To set up this project, ensure you have Python installed. Then, follow these steps:

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/weather-query-agent.git
   cd weather-query-agent
2. Set Up a Virtual Environment (Optional but Recommended):

    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

3. Install Required Packages:

    ```bash
    pip install -r requirements.txt

Required packages include:
- langgraph (for building the workflow and managing LLM interactions)
- Any additional dependencies for the weather API tool (e.g., requests for making API calls)

#Usage
Quick Start
Run the script directly, and it will respond to weather-related questions such as "Will it rain in [Location] today?" by querying the weather API.

#Code Breakdown
Imports and Tool Setup
- Define and import the required tools using ToolNode.
- This example assumes a function named get_weather that interacts with a weather API.

Workflow Functions
- call_model: This function calls the LLM with the current conversation state.
- call_tools: Based on the LLM’s output, it decides whether to call external tools or end the conversation.

Workflow Initialization
- Initialize the Workflow: Use StateGraph to set up the workflow, adding nodes and edges for both LLM and tools.
- The llm node processes user queries.
- The tools node handles calls to the weather API.

Compilation and Execution
- Compile the workflow using StateGraph.compile() and send a message to the agent. The agent will then process the query and provide an appropriate response.
