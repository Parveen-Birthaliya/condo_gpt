# 🏙️ Condo GPT

**Condo GPT** is an intelligent assistant designed for querying and analyzing condominium data in **Miami** using natural language.  
It enables real estate agents, analysts, and investors to explore insights about condo buildings, units, sales, and market trends—**without writing a single line of code**.

---

## 🚀 Overview

Condo GPT leverages **Natural Language Processing (NLP)** and **AI agents** to interpret human questions and convert them into complex SQL queries that fetch actionable insights from a structured real estate database.

A sample of the **Condo Cube** database is provided, which includes data for the following markets:

- 🏝️ South Beach  
- 🌴 Miami Beach  
- 🏗️ South of Fifth  

The tool empowers **non-technical users** to perform advanced market analysis, comparisons, and investment research that would typically require paid analysts—potentially saving brokerages **thousands of dollars per month**.

---

## ✨ Features

- 🧠 **Natural Language Interface** – Query condo data using plain English  
- 🗺️ **Google Maps Integration** – Location-based insights and visual mapping  
- 🧩 **Dynamic SQL Generation** – AI-driven construction of database queries  
- 📊 **Interactive Visuals** – Generate charts and graphs dynamically  
- 📄 **PDF Report Generation** – Export analytical summaries  
- 🧭 **Multi-Agent Architecture** – Powered by LangChain and LangGraph  

---

## 🧰 Technologies Used

| Component | Technology |
|------------|-------------|
| Backend | Python 3.x, Flask |
| Database | PostgreSQL |
| AI & NLP | OpenAI GPT, LangChain, LangGraph |
| Visualization | Chart.js |
| Mapping | Google Maps API - geocoding and directions |
| Reporting | ReportLab-PDF generation |
| Environment | virtualenv |

---


## Setup

1. Clone the repository
2. Prepare the environment and database
-  virtualenv gpt_env
-  Log in to psql as superuser (sudo -u postgres psql on Linux)
-  `CREATE DATABASE condo_gpt`;
   `CREATE USER readonly_user WITH PASSWORD 'password';`
   `GRANT CONNECT ON DATABASE condo_gpt TO readonly_user;`
   `GRANT USAGE ON SCHEMA public TO readonly_user;`
   `GRANT SELECT ON ALL TABLES IN SCHEMA public TO readonly_user;`
   `ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON TABLES TO readonly_user;`
   `\q`
3. Edit your `gpt_env/bin/activate` file and add the following environment variables
- `GPLACES_API_KEY`: Your Google Places API key
- `OPENAI_API_KEY`: Your OpenAI API key
- `FLASK_SECRET` : Flask Secret Phrase (Can be any string)
- `PG_USER`: Your postgres User you set up above
- `PG_PASSWORD`: Password for your postgres user
- `PG_PORT`: Port for your postgres database server (default 5432)
- `PG_DB`: Name of your postgres database
4. Set up the sample data
-  Ensure you are in the same directory as sample_db.sql
-  `psql -d condo_gpt < sample_db.sql`
5. Install dependencies:
- `source gpt_env/bin/activate`
- `pip install -r requirements.txt`
6. Start the application
`python server.py`

## Running the Application

1. Start the Flask server:
`python server.py`
2. Open a web browser and navigate to `http://localhost:5000`

## Usage

- Enter natural language questions about Miami condos in the input field
- The system will interpret your question, query the database, and provide relevant answers
- For location-based queries, interactive maps may be generated
- The system can create charts and graphs for data visualization
- PDF reports can be generated for more detailed analysis
- Use the 'Clear Memory' Button to clear the conversation history

## Example Prompt Sequence
- What buildings on collins had the most sales in 2023?
- Generate a graph of this data
- Put the data in an html table
- Add a third column with the total sales volume of each building
- Add a fourth column with the median sales price for each building
- Replace the third column with the closest school to the building, and the fourth column with the driving distance to that school from the building

## Project Structure

- `server.py`: Flask application server
- `main.py`: Core logic for processing questions and generating responses
- `tools.py`: Custom tools for database querying and API interactions
- `prefix.py`: System message prefix for the AI agent
- `boilerplate.py`: Boilerplate code for map and chart generation
