# Capstone Project Context

## Project

* **Name:** Threat Intelligence Feed Dashboard
* **Team:**
  * Jesus Alvarez (Component 1: Feed Collector)
  * Harry Yachimba (Component 2: AI Summarizer & IOC Extractor)
  * Julian Silva-Erazo (Component 3: Relevance Scorer)
  * Safayet Safin (Component 4: Integration, Testing & Presentation)
* **What it does:** This project automates the collection, summarization, IOC extraction, and prioritization of cybersecurity threat intelligence. Threat data is collected, processed through AI models, stored in Airtable, and then presented in a unified dashboard so security analysts can focus on high priority threats.
* **Project Type:** AI Threat Intelligence Dashboard

## Architecture

* **Ingestion:** n8n workflows collect threat intelligence feeds and store records in Airtable.
* **AI Core:** Flowise LLM chains using Groq models summarize articles and extract indicators of compromise.
* **Specialist:** Relevance scoring evaluates how threats impact specific tech stacks.
* **Integration (My Component):** Connects all components together, manages automation between Airtable and Flowise, and presents the final prioritized data in an Airtable Dashboard for end users.

## Tech Stack

* n8n Cloud
* Flowise Cloud
* Groq API
* Hugging Face API
* Airtable
* GitHub
* VS Code
* GitHub Copilot

## Airtable Schema

### Threat Intelligence Table

| Field | Type | Written By | Status Values |
|---|---|---|---|
| input_text | Long Text | Component 1 | |
| summary | Long Text | Component 2 | |
| severity | Single Select | Component 2 | critical, high, medium, low |
| attack_type | Text | Component 2 | |
| indicators | Long Text | Component 2 | |
| recommendations | Long Text | Component 2 | |
| relevance_score | Number | Component 3 | |
| tested_at | Date | Component 4 | |

## Conventions

* Field names: snake_case
* Status values: lowercase
* AI responses must return valid JSON
* Use POST requests for Flowise prediction endpoints

## Current State

* **What is working:** Flowise chains are functioning, n8n HTTP Request nodes connect to Flowise, and the initial Airtable integration writes data properly.
* **What is in progress:** Building out the final presentation dashboard in Airtable, testing end to end automation, and validating data handoffs across all four components.
* **Known issues:** JSON formatting errors occasionally occur in the HTTP request bodies between n8n and Flowise.
* **Next milestone:** Complete one full end to end threat intelligence workflow through all components for Checkpoint 2.

## Repository Structure

```text
.
├── .github/
│   └── copilot-instructions.md
├── docs/
│   ├── architecture.png
│   └── proposal.md
├── week-07/
├── week-08-prompt-engineering-and-copilot/
├── screenshots/
└── README.md