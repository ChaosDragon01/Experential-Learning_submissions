# Threat Intelligence Feed Dashboard 

## Team Members

| Name | Role/Component | GitHub Username |
|------|---------------|-----------------|
| Jesus Alvarez ] | Component 1- Feed Collector | @[username] |
| Harry Yachimba | Component 2 - AI Summarizer & IOC Extractor | @[HarryYachimba-ArmChairWarrior] |
| Julian Silva-Erazo | Component 3 - Relevance Scorer | @[Julznyc12] |
| Safayet Safin | Component 4 - Integration, Testing & Presentation | @[ChaosDragon01] |

## Problem Statement

Security analysts can often be overwhelmed by the large amounts of threat intelligence data that comes from security blogs, CVE feeds, vulnerability databases, and other sources. Reviewing this manually and being able to accurately prioritize its information takes up a lot of time and can lead to some threats being overlooked. This project is going to automate the collection, summarization, and prioritization of threat intelligence using AI. This will allow analysts to focus on more time-sensitive security threats.

## Target Users

This project would be used by security analysts and cybersecurity teams at a small-to-midsize organization that receives 100-300 threat intelligence alerts per day. Who are in need of a faster way to identify and prioritize the most relevant threats affecting their systems. 

## Architecture

![ArchitectureDiagram](https://app.diagrams.net/#G1ZZj3yySfiCTuzBBk6x8-ZCove5HU3mXb#%7B%22pageId%22%3A%22OIHx0Rzq6e4_eJkJ5iY6%22%7D)

## Component Breakdown

### Component 1: Feed Collector (Owner: Jesus Alvarez)
- **Description:** This component collects threat intelligence data from public sources (security blogs, RSS feeds, among many more) and it normalizes the collected data and stores it in Airtable for additional processing. 
- **Tools:** n8n, Airtable
- **Input:** RSS feeds, CVE APIs, security blog posts
- **Output:** Normalized threat records stored in Airtable
- **Standalone demo:** This component can run the n8n workflow to collect sample threat data from RSS feeds and store the normalized results in an Airtable table.

### Component 2: AI Summarizer & IOC Extractor (Owner: Harry Yachimba)
- **Description:** This component uses an AI model to summarize threat intelligence articles and extract IOCs. 
- **Tools:** Flowise, Groq API, Airtable
- **Input:** Threat records from Airtable
- **Output:** Enriched threat records stored in Airtable
- **Standalone demo:** This component can provide a threat article or description and show the AI workflow generating a summary and extracting IOCs.

### Component 3: Relevance Scorer (Owner: Julian Silva-Erazo)
- **Description:** This component evaluates how relevant each threat is to an organization by comparing the threat details with the organization’s technology stack and assigning it a relevance score.
- **Tools:** n8n, Groq API, Airtable
- **Input:** Enrich threat records from Airtable 
- **Output:** Prioritized threat records stored in Airtable
- **Standalone demo:** This component feeds a set of enriched threat records into the scoring system and shows how the system assigns relevance scores based on the defined tech stack.

### Component 4: Integration, Testing & Presentation (Owner: [Safayet Safin)
- **Description:** This component integrates all of the system’s components and presents the results in a dashboard that allows users to view and analyze prioritized threat intelligence. 
- **Tools:** Airtable Dashboard, GitHub, draw.io
- **Input:** Prioritized threat records from Airtable
- **Output:** Dashboard displaying prioritized threat intelligence, summaries, and indicators of compromise for security analysts. 
- **Standalone demo:** This component shows the Airtable dashboard displaying prioritized threats, filtering by severity or relevance score. 

## Data Sources

- **Primary data:** Threat intelligence data from sources such as RSS feeds, CVE, and security blogs.
- **Sample data:** Test datasets created from sample threat reports or publicly available vulnerability descriptions. 
- **Data format:** RSS feed entries, JSON API responses, Airtable records

## AI Capabilities

| Capability | Purpose | Model/API |
|-----------|---------|-----------|
| Threat Summarization | Generate concise summaries of threat reports | Groq LLaMA |
| IOC Extraction | Identify indicators of compromise from threat descriptions | Groq LLaMA |
| Relevance Scoring | Evaluate how relevant threats are to a specific technology stack | Groq LLaMA |

## Success Criteria

1. The system correctly extracts threat records from multiple public sources.
2. The AI summarization can produce clear summaries and can identify IOCs.
3. The relevance scoring can correctly prioritize threats based on the defined technology stack.
4. All four components can integrate successfully and exchange data through Airtable. 
5. The dashboard can display prioritized threats with filtering and search functions.  

## Timeline

| Week | Milestone |
|------|-----------|
| 3 (Now) | Project proposal + architecture diagram + GitHub repo |
| 4-6 | Build individual components, test with sample data |
| 7-9 | Add LLM/agent capabilities, refine AI processing |
| 10-12 | Integration, error handling, dashboard/UI |
| 13-14 | Polish, documentation, demo preparation |
| 15 | Final presentation |

