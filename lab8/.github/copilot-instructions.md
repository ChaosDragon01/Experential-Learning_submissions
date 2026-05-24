# Capstone Project Context

## Project

* **Name:** Threat Intelligence Feed Dashboard
* **Team:**
  * Jesus Alvarez (Component 1: Feed Collector)
  * Harry Yachimba (Component 2: AI Summarizer & IOC Extractor)
  * Julian Silva-Erazo (Component 3: Relevance Scorer)
  * Safayet Safin (Component 4: Integration, Testing & Presentation)
* **What it does:** This project automates the collection, summarization, IOC extraction, and prioritization of cybersecurity threat intelligence. Threat data is collected, processed through AI models, stored in Airtable, and presented in a unified dashboard so security analysts can focus on high priority threats.
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

* **What is working:** The system passed the Checkpoint 2 end-to-end integration test. A test record successfully flowed through all four components. The Airtable presentation dashboard is operational and displays the fully processed threat records.
* **What is in progress:** Implementing error handling and batching logic in n8n to address Groq and Hugging Face API rate limits encountered during the integration tests. Refining AI prompts to fix heavy concentrations in MEDIUM and HIGH severity outputs.
* **Known issues:** The dashboard interface requires a short manual refresh delay before newly processed records become visible. IOC extraction occasionally returns "None" when explicit indicators are missing from the article.
* **Next milestone:** Week 10 phase focusing on Security Orchestration, error handling, confidence-based routing, and production dashboard refinement.

## Repository Structure

```text
.
├── .github/
│   └── copilot-instructions.md
├── docs/
│   ├── architecture.png
│   └── proposal.md
├── checkpoint2-results/
├── week-07/
├── week-08-prompt-engineering-and-copilot/
├── screenshots/
└── README.md
```
