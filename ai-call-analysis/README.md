# AI Call Analytics Automation

AI-powered automation system for processing customer calls, analyzing sentiment, and generating call statistics that can be queried through an AI agent.

The system automatically transcribes calls, classifies feedback, calculates statistics, and allows managers to request analytics in natural language.

---

# System Architecture

The project consists of four automation workflows:

- call-processing-workflow.json
- get-call-stats-tool-workflow.json
- call-analytics-agent-workflow.json
- call-analytics-error-handler-workflow.json

Together they form a complete automated call analytics system.

---

# Call Processing Pipeline

File: `call-processing-workflow.json`

This is the main automation workflow responsible for processing incoming calls.

The workflow runs automatically every **2 minutes** and performs the following steps:

1. Checks for new calls
2. Retrieves an unprocessed call
3. Marks the call as **Processing**
4. Generates a downloadable audio URL
5. Sends the audio to **AssemblyAI** for transcription
6. Waits for transcription to complete
7. Retrieves transcript data
8. Checks for transcription errors
9. Sends transcript to **OpenAI** for analysis
10. Extracts sentiment and category
11. Calculates processing costs
12. Stores processed call data
13. Updates call status to **Done**

Additional data calculated:

- call duration
- word count
- OpenAI token usage
- OpenAI processing cost
- AssemblyAI transcription cost
- total processing cost

---

# AI Call Analysis

Each call transcript is analyzed using AI to determine:

### Sentiment

- positive
- negative
- neutral

### Category

The AI classifies calls into one of the following categories:

- cake_quality
- delivery_quality
- other

---

# Data Storage

Processed calls are stored in a structured data table containing:

- recording URL
- call duration
- sentiment
- category

This data is later used for analytics and reporting.

---

# AI Agent for Call Statistics

File: `call-analytics-agent-workflow.json`

Managers can request analytics using natural language.

The AI agent receives user questions and retrieves real statistics using the statistics tool.

Example questions:

- "Скільки було негативних дзвінків за минулий місяць?"
- "Яка середня тривалість дзвінка?"
- "Покажи статистику по категоріях"

The AI agent converts these requests into tool calls and returns formatted responses.

---

# Statistics Tool

File: `get-call-stats-tool-workflow.json`

This workflow calculates statistics for a selected date range.

Input parameters:

startDate  
endDate  

The tool retrieves processed calls and calculates:

- total calls
- positive calls
- negative calls
- neutral calls
- negative call percentage
- average call duration
- category statistics

Example output:
{
"totalCalls": 10,
"positiveCalls": 4,
"negativeCalls": 3,
"neutralCalls": 3,
"negativeCallPercent": 30,
"averageDurationMinutes": 2.5,
"categories": [...]
}

The AI agent converts this JSON into a readable response.

---

# Error Handling

File: `call-analytics-error-handler-workflow.json`

The system includes a dedicated error handling workflow.

If any workflow execution fails:

1. The error trigger captures the failure
2. Error details are formatted
3. Execution information is logged

Stored error data includes:

- timestamp
- error message
- workflow name
- node where the error occurred
- execution ID
- stack trace
- execution URL

This helps quickly diagnose issues and monitor system stability.

---

# Technologies

The project uses the following technologies:

- n8n (workflow automation)
- AssemblyAI (speech-to-text transcription)
- OpenAI GPT-4o-mini (AI analysis)
- Data Tables (structured call storage)
- Google Sheets (call queue and logs)
- AI Agents with tool usage

---

# Business Impact

This automation system fully replaces manual call analysis.

Benefits:

- automatic call transcription
- AI sentiment detection
- automated statistics generation
- natural language analytics queries
- centralized error monitoring

The system significantly reduces manual work and gives management real-time insights into customer feedback.
