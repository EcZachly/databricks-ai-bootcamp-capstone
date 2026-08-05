# Databricks AI Capstone Ideas

A set of capstone project options that combine **Databricks Apps**, **Lakebase**, unstructured-data retrieval (vector search / RAG), and AI agents. All ideas share the same architectural skeleton — relational tables in Lakebase, embeddings over unstructured text for semantic retrieval, and an agent with tools that can both *read* and *write* to the database.

---

## Capstone Requirements

Every project on this list, regardless of which one you choose, must include:

- **A data pipeline in Spark.**
- **Integration with at least one third-party API** (see each project's suggested APIs below).
- **Processing of unstructured data** of some kind (video, audio, images, text, etc.) — e.g. embedding plot summaries, articles, job descriptions, or news text for semantic retrieval.
- **A Databricks App with a frontend.**
- **An AI agent that does stuff** — i.e. an agent with tools that can search/retrieve and also take real actions (writes) against your data.

If you have joined the "Rise of the AI Data Engineer" boot camp, then you can submit the capstone project [here](https://learn.dataexpert.io/assignment/4904)
If you have not joined yet, you can join for free [here](https://learn.dataexpert.io/program/the-one-week-beginners-databricks-boot-camp-7129)

---

## 1. AI Movie Night Planner

Users create a group, rate movies, describe what they want to watch, and ask an agent to recommend something everyone will enjoy.

**Third-party API**
- [TMDB API](https://www.themoviedb.org/documentation/api) — movies, actors, genres, posters, plot summaries, reviews, trailers, and streaming-provider availability.
- Free for noncommercial educational use with attribution; each student needs a free API key.

**Lakebase tables**
- `users`
- `groups`
- `group_members`
- `movies`
- `ratings`
- `watchlist_items`
- `recommendations`

**Context engineering**
- Embed plot summaries, keywords, cast information, and reviews.
- Retrieve movies using semantic requests such as *"a funny sci-fi movie that isn't too violent and is under two hours."*

**Agent capabilities**
- Search and explain recommendations.
- Compare several movies.
- Add a movie to the group watchlist.
- Record ratings after the group watches it.
- Avoid movies already watched or disliked by group members.

---

## 2. AI Trip and Outdoor Activity Planner

Users save destinations and preferences, then ask an agent to build a weather-aware itinerary.

**Third-party APIs**
- [Open-Meteo Geocoding API](https://open-meteo.com/en/docs/geocoding-api) — destination names → coordinates.
- [Open-Meteo Weather API](https://open-meteo.com/en/docs) — hourly forecasts.
- [Open-Meteo Air Quality API](https://open-meteo.com/en/docs/air-quality-api) — AQI, particulate matter, UV, pollen.
- [Wikimedia APIs](https://www.mediawiki.org/wiki/API:Main_page) — destination descriptions and nearby attractions.

Open-Meteo requires no API key for noncommercial usage under its free limits.

**Lakebase tables**
- `users`
- `trips`
- `destinations`
- `activities`
- `itinerary_items`
- `weather_snapshots`
- `packing_items`

**Context engineering**
- Embed destination descriptions, attraction information, activity requirements, and user notes.
- Retrieve suitable activities based on interests and current conditions.

**Agent capabilities**
- Generate a day-by-day itinerary.
- Reschedule outdoor activities when rain or poor air quality is forecast.
- Build a packing list.
- Add, remove, or move itinerary items.
- Explain why it made each weather-based change.

---

## 3. AI Research and Learning Copilot

Users create a learning objective, discover relevant papers, save them into collections, and ask an agent to construct a personalized study plan.

**Third-party API**
- [OpenAlex API](https://docs.openalex.org/how-to-use-the-api/authentication) — papers, authors, institutions, topics, citations, abstracts, and open-access content. A free OpenAlex key currently provides a daily free allowance sufficient for normal student projects.

**Lakebase tables**
- `users`
- `learning_goals`
- `papers`
- `authors`
- `paper_authors`
- `collections`
- `collection_papers`
- `reading_progress`
- `notes`

**Context engineering**
- Embed abstracts, paper content where available, student notes, and learning goals.
- Retrieve evidence across multiple papers instead of sending the entire collection to the model.

**Agent capabilities**
- Find papers matching a learning goal.
- Summarize and compare research.
- Generate a sequenced reading plan.
- Add papers to a collection.
- Track progress and recommend the next paper.
- Include citations in its answers.

---

## 4. AI Stock Market Research Assistant

Users track a personal watchlist of tickers, describe an investing thesis or question, and ask an agent to pull real market data, summarize company fundamentals and news, and log the analysis.

**Third-party API**
- [Massive Stocks API](https://massive.com/docs/rest/stocks/overview) — real-time and historical tick data, trades, quotes, and fundamentals across all major US exchanges via REST or WebSockets, in standardized JSON/CSV. Instant free-tier access; see the [REST API Quickstart](https://massive.com/docs/rest/quickstart).

**Lakebase tables**
- `users`
- `watchlists`
- `watchlist_tickers`
- `companies`
- `price_snapshots`
- `news_articles`
- `research_notes`
- `analysis_reports`

**Context engineering**
- Embed company profiles, filings excerpts, earnings-call summaries, and news article text.
- Retrieve relevant context using semantic requests such as *"companies exposed to rising interest rates in the regional banking sector"* rather than plain ticker/keyword lookup.

**Agent capabilities**
- Pull current and historical price data for a ticker and summarize recent performance.
- Surface and summarize relevant news/filings for a company.
- Compare multiple tickers on fundamentals or recent price action.
- Add or remove tickers from a user's watchlist.
- Save a research note or generated analysis report tied to a ticker.
- Flag notable price moves or news since the user's last visit.

---

## 5. AI Job Hunting Copilot

Users describe their skills, target roles, and preferences, then ask an agent to find matching openings, tailor application materials, and track their pipeline.

**Third-party APIs**
- [Adzuna API](https://developer.adzuna.com/) — search millions of live job listings across many countries by keyword, location, category, and salary; free tier with a free API key.
- [USAJobs Search API](https://developer.usajobs.gov/api-reference/get-api-search) — official U.S. federal government job openings; free, requires a free API key and registered email.
- [RemoteOK API](https://remoteok.com/api) — remote job listings in JSON; free, no API key required.

**Lakebase tables**
- `users`
- `profiles`
- `skills`
- `job_postings`
- `applications`
- `saved_jobs`
- `interview_notes`
- `contacts`

**Context engineering**
- Embed job descriptions, required qualifications, and the user's resume/skills profile.
- Retrieve postings using semantic requests such as *"remote backend roles that don't require 5+ years of Kubernetes experience."*

**Agent capabilities**
- Search and rank job postings against a user's profile and stated preferences.
- Explain why a posting is or isn't a good match.
- Save a posting to a pipeline stage (saved, applied, interviewing, rejected, offer).
- Draft a tailored cover-letter snippet or resume bullet for a specific posting.
- Track interview notes and follow-up dates for saved applications.
- Surface stale applications that haven't been updated in a while.
