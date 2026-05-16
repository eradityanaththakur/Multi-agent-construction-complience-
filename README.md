# Multi-agent-construction-compliance-
[README.md](https://github.com/user-attachments/files/27840454/README.md)
# Multi-Agent Infrastructure Compliance Engine

An intelligent, multi-agent system designed to mitigate critical administrative, technical, and socio-economic risks in large-scale infrastructure projects (like bridges and highways). The system acts as a digital surveyor, legal auditor, and intelligence officer.

## The 4 Agents

1. **Agent 1: Land & Forest Compliance Agent**
   - **Goal:** Achieve "Zero-EDS" (Essential Details Sought).
   - **Action:** Ingests the project's Detailed Project Report (DPR) via PDF, cross-references it with local forest rules (JSON Knowledge Base), and searches 10 years of historical rejections to provide a pre-emptive checklist.

2. **Agent 2: Site Clearance & Utility Intelligence Agent**
   - **Goal:** Prevent accidental utility damage during excavation.
   - **Action:** Crawls 10-15 years of government and private tenders to identify buried utilities (sewerage, OFC cables, gas lines) that might conflict with the specified excavation depth.

3. **Agent 3: Resource Compliance & Socio-Economic Intelligence**
   - **Goal:** Mitigate "Mafia Premium" and manufactured local protests.
   - **Action:** Scrapes vernacular news (Amar Ujala, Jagran) and social media (Facebook/Reddit) to gauge negative public sentiment. Compiles a directory of legally verified stone crushers and River Bed Material (RBM) suppliers.

4. **Agent 4: Regulatory & Technical Compliance Agent**
   - **Goal:** Resolve code conflicts (e.g., IS vs. IRC) and the "Revision Gap".
   - **Action:** Synthesizes the latest loading parameters from official repositories (BIS, IRC, MoRTH) and flags contradictory material choices in the DPR based on the latest state High Court orders and PWD circulars.

## Installation

1. Clone or download this repository.
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
   *(Note: Ensure Tesseract OCR and Poppler are installed on your system if you want Agent 1 to perform OCR on scanned PDFs.)*
3. Set up your environment variables. Open the `.env` file and add your API keys:
   ```env
   OPENAI_API_KEY="your_openai_api_key_here"
   SERPAPI_API_KEY="your_serpapi_api_key_here"
   TAVILY_API_KEY="your_tavily_api_key_here"
   ```

## Usage

The recommended way to use the application is via the interactive **Streamlit** dashboard. The dashboard provides live telemetry of the agents' thoughts, a manual review and approval workflow, and bilingual (English/Hindi) report generation.

```bash
streamlit run app.py
```

You can also run the entire pipeline unified via the orchestrator script in the terminal:

```bash
python main_orchestrator.py
```

Or run each agent individually for isolated testing:
```bash
python agent1_forest_compliance.py
python agent2_utility_intelligence.py
python agent3_socio_economic_intelligence.py
python agent4_regulatory_compliance.py
```

## Architecture

- **LLM Engine:** OpenAI GPT-4o (`gpt-4o` and `gpt-4o-mini`).
- **Orchestration:** LangGraph ReAct Agents.
- **Search Engine:** SerpAPI & Tavily Search, functioning as a localized "dorking" tool to bypass paywalls and scrape public records.
- **UI & Telemetry:** Streamlit.
