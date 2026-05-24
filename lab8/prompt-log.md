# Prompt Log Safayet Safin
**Project:** Threat Intelligence Feed Dashboard
**Team:** Jesus Alvarez, Harry Yachimba, Julian Silva-Erazo, Safayet Safin
**My Component:** Component 4 Integration, Testing & Presentation
**AI Tools Used:** GitHub Copilot

## Entry 1: Generating the Week 8 Capstone Audit Gap Analysis
**Context:** Creating the initial Checkpoint 2 readiness assessment using the Copilot interview prompt. The copilot-instructions.md file was loaded in VS Code.
**Prompt:**
> I need you to act as a capstone project advisor for a university AI integration course. I am going to describe my group project, and I need you to interview me about its current state, then produce a structured gap analysis.
**Result:** Copilot asked the 10 interview questions sequentially and then generated a gap analysis marking our project as "AT RISK" due to JSON formatting errors and missing end-to-end automation.
**Evaluation:** The output was highly accurate because it pulled our exact Airtable schema and component handoff structure from the instructions file.
**What I changed:** I formatted the output to ensure all headings and bullet points matched standard markdown syntax.
**What I learned:** Providing a highly detailed copilot-instructions.md file completely changes the quality of the AI output from generic templates to actionable project management.

## Entry 2: Debugging JSON payload errors between n8n and Flowise
**Context:** n8n HTTP Request nodes were failing to pass data cleanly to the Flowise AI Core component due to malformed JSON bodies containing special characters from the threat feed summaries.
**Prompt:**
> I am building an n8n workflow that sends a POST request to Flowise. The input text contains special characters and line breaks from an RSS feed. My current JSON body is `{"question": "{{ $json.raw_summary }}"}` but it throws a 400 Bad Request error. How do I properly escape this in n8n?
**Result:** Copilot recommended using `JSON.stringify()` in the expression or utilizing the Set node to handle string formatting before the HTTP Request node.
**Evaluation:** The suggestion to use `JSON.stringify()` was the exact fix needed to prevent the payload from breaking the Flowise endpoint.
**What I changed:** I implemented a Code node in n8n prior to the HTTP request to sanitize the inputs entirely.
**What I learned:** AI is much faster at identifying syntax errors in n8n expressions than manual trial and error.

## Entry 3: Standardizing Airtable Schema fields
**Context:** We found field name mismatches between what Component 2 outputted and what the Airtable expected. I needed Copilot to verify snake_case formatting for our JSON outputs.
**Prompt:** 
> Using the Airtable schema from copilot-instructions.md, rewrite this Flowise system prompt to ensure the output strictly uses these exact keys in snake_case: attack_type, relevance_score, severity, and indicators. 
**Result:** Copilot generated a strict JSON schema block to append to the system prompt, enforcing the specific keys and standardizing the output structure.
**Evaluation:** The result was perfect and prevented Component 3 from failing to read the data. 
**What I changed:** I added a constraint to the prompt explicitly telling the model to return "None" if an indicator of compromise was not found, rather than leaving the field null.
**What I learned:** Setting strict output constraints in the prompt is the only reliable way to integrate LLMs with structured databases like Airtable.

## Entry 4: Generating edge-case test data for Checkpoint 2
**Context:** We needed bad data to test the error routing in Component 4.
**Prompt:**
> Using the Airtable schema from my copilot-instructions.md, generate 5 edge-case test records in CSV format. Include one with a missing title, one with an extremely long raw_summary, and one with a malformed URL.
**Result:** Copilot produced a valid CSV with 5 threat intelligence records designed to break our parsing logic. 
**Evaluation:** The records were realistic and immediately highlighted a vulnerability in our dashboard refresh logic.
**What I changed:** I adjusted the severity levels of the generated records to ensure we had a mix of LOW and CRITICAL to test the dashboard filtering.
**What I learned:** Asking Copilot to generate test data saves hours of manual data entry and provides more creative edge cases than I would think of manually.

## Entry 5: Re-running the Capstone Audit for Week 9
**Context:** We successfully passed our end-to-end integration test. I needed to update the audit report to reflect that the system was now working.
**Prompt:**
> Re-run the capstone audit. Update the status to READY. We successfully passed the end-to-end test with a Hacker News article. The ingestion, AI Core, and Specialist scoring all worked, and the record is visible in the dashboard. The remaining gaps are API rate limits and some severity clustering.
**Result:** Copilot produced an updated Checkpoint 2 Readiness Assessment reflecting the passed test, downgrading the critical gaps, and outlining the next steps for Week 10.
**Evaluation:** The generated report correctly captured the transition from "AT RISK" to "READY" while maintaining focus on the new rate-limit issues.
**What I changed:** I added explicit citations to the team screenshot files to prove the test passed.
**What I learned:** Keeping the AI updated on the current state of the project allows it to generate accurate status reports that actually reflect team progress.