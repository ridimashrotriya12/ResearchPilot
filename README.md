# ResearchPilot

A small multi-agent research assistant. Give it a topic, and it searches the web, scrapes the most relevant page, writes up a structured report, and then critiques its own work — all through a Streamlit UI.

It's basically four agents doing one person's job: a search agent, a reader agent, a writer, and a critic.

## What it does

1. **Search Agent** – queries the web (via Tavily) for recent, relevant info on your topic.
2. **Reader Agent** – picks the best result and scrapes the page for deeper content.
3. **Writer Chain** – turns the combined research into a proper report (intro, key findings, conclusion, sources).
4. **Critic Chain** – reviews the report and scores it out of 10, with strengths and areas to improve.

Everything runs in sequence and shows up live in the UI as it happens, with the final report downloadable as a `.md` file.

## Tech stack

- **Streamlit** – UI
- **LangChain** + **langchain-openai** – agent/chain orchestration
- **OpenAI (gpt-4o-mini)** – the LLM behind every agent
- **Tavily** – web search
- **BeautifulSoup / requests** – scraping

## Setup

Clone the repo and install dependencies:


git clone https://github.com/ridimashrotriya12/ResearchPilot.git
cd ResearchPilot
pip install -r requirements.txt


You'll need API keys for OpenAI and Tavily. Create a `.env` file in the root:

OPENAI_API_KEY=your_openai_key
TAVILY_API_KEY=your_tavily_key


## Running it

streamlit run app.py

This opens the app in your browser. Type in a topic, hit "Run Research Pipeline," and watch it go through search → read → write → critique.

## Project structure

ResearchPilot/
├── app.py # Streamlit UI and pipeline orchestration
├── agents.py # Search/reader agents + writer and critic chains
├── tools.py # Web search (Tavily) and scraping tools
├── requirements.txt
└── .gitignore


## Notes

- Each run costs a few LLM calls, so keep that in mind if you're testing a lot of topics back to back.
- The scraper grabs plain text from the top result — it won't handle JS-heavy or paywalled pages well.
- This is a work in progress — error handling, multi-source scraping, and citation formatting are areas I'm still improving.
