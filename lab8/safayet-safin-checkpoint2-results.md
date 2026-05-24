# Checkpoint 2 Results

**Date:** 2026-05-20
**Team:** Julian Silva-Erazo, Jesus Alvarez, Safayet Safin, Harry Yachimba
**Test record:** A cybersecurity news article titled "Microsoft Open-Sources RAMPART and Clarity to Secure AI Agents During Development" collected from The Hacker News RSS feed. The input included the article title, source, URL, published date, raw summary, and creation timestamp.

## End-to-End Status: PASSED

## Component-by-Component Results

### Ingestion
**Status:** Working
**What happened:** The ingestion workflow successfully collected the article from the RSS feed and populated the initial Airtable record.
**Screenshot:** running-component1.png

### AI Core
**Status:** Working
**What happened:** The AI workflow picked up the new Airtable entry and ran it through the Groq models. It successfully outputted severity classification, attack type, and extracted IOCs.
**Screenshot:** running-component2.png

### Specialist
**Status:** Working
**What happened:** The relevance scoring workflow processed the AI output and generated the final enrichment data, updating the Airtable record automatically.
**Screenshot:** running-component3.png

### Integration Dashboard
**Status:** Working
**What happened:** The fully processed threat intelligence record appeared correctly inside the final dashboard view with all analysis fields intact.
**Screenshot:** component4-dashboard.png

## Gaps Found
* AI enrichment fields occasionally return incomplete values depending on the length of the article summary. (Owner: Harry Yachimba)
* Severity classifications are heavily concentrated in MEDIUM and HIGH, with almost no LOW severity outputs. (Owner: Harry Yachimba)
* IOC extraction sometimes returns "None" when articles lack explicit indicators. (Owner: Harry Yachimba)
* The dashboard interface requires a short refresh delay before newly processed records populate. (Owner: Safayet Safin)
* API rate limits from Groq and Hugging Face occasionally slow down processing during bulk testing. (Owner: Safayet Safin)
* We had to make minor manual adjustments to Airtable field mappings to keep the workflows consistent. (Owner: Safayet Safin)

## Fix Plan
1. Improve AI prompt engineering to generate more balanced severity classifications and handle empty IOC fields gracefully. (Harry Yachimba, Medium effort)
2. Add batching and wait node logic in n8n workflows to prevent API rate limit crashes. (Safayet Safin, Medium effort)
3. Standardize Airtable field names across all workflows to prevent future integration breaks. (Safayet Safin, Low effort)