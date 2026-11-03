# AI Website Summarizer

My first AI project built as part of the AI learning journey at Scaler.

AI Website Summarizer takes a website URL, extracts the readable page
content, and uses a large language model (LLM) to generate a concise,
friendly summary. The result is displayed in a simple Gradio web
interface.

## How it works

1.  **Enter a URL** -- Provide the website URL in the Gradio interface.
2.  **Fetch website content** -- `scraper.py` uses `requests` and
    `BeautifulSoup` to retrieve the page and extract its text, while
    removing elements such as scripts, styles, navigation, headers, and
    footers.
3.  **Generate a summary** -- `summarizer.py` sends the extracted
    content to the Groq API using the OpenAI-compatible Python client
    and the `openai/gpt-oss-20b` model.
4.  **Display the result** -- `app.py` provides the URL input and
    renders the generated summary as Markdown in Gradio.

## Tech stack

-   Python
-   Gradio -- web interface
-   Requests -- fetching website pages
-   BeautifulSoup4 -- HTML parsing and text extraction
-   OpenAI Python SDK -- API client compatible with Groq
-   Groq API -- LLM inference
-   `openai/gpt-oss-20b` -- model used for summarization
-   `python-dotenv` -- loading the API key from environment variables

## Project structure

``` text
AI Fusion/
├── app.py              # Gradio interface and app entry point
├── scraper.py          # Fetches and extracts website text
├── summarizer.py       # Sends extracted content to the LLM
├── a.py                # Small API connectivity / prompt experiment
├── groq_models.py      # Lists models available through the Groq API
├── .env.example        # Example environment variable configuration
├── .gitignore          # Files and folders excluded from Git
└── README.md           # Project documentation
```

## Getting started

### 1. Clone the repository

``` bash
git clone <your-repository-url>
cd <repository-folder>
```

### 2. Create and activate a virtual environment

Windows PowerShell:

``` powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

macOS / Linux:

``` bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

``` bash
pip install gradio requests beautifulsoup4 openai python-dotenv
```

### 4. Configure the API key

Create a `.env` file in the project root:

``` env
GROQ_API_KEY=your_groq_api_key
```

Get an API key from the [Groq Console](https://console.groq.com/).

Do not commit your real `.env` file or API key. The repository should
contain only `.env.example` with placeholder values.

### 5. Run the application

``` bash
python app.py
```

Open the local Gradio URL shown in the terminal. The app is configured
with `share=True`, which also asks Gradio to create a shareable public
link when it launches.

## Notes and limitations

-   The project is a learning exercise and a first step in exploring AI
    application development.
-   Website extraction depends on the website's accessibility and HTML
    structure. Pages that require JavaScript rendering, authentication,
    or block automated requests may not be extracted correctly.
-   The summarization call uses the Groq API. API access, model
    availability, rate limits, and usage costs depend on the provider.
-   Avoid submitting private or sensitive URLs or content.

## Learning outcomes

Through this project, I explored how to connect the pieces of a basic
LLM-powered application:

-   Fetching and parsing website content
-   Sending contextual prompts to an LLM through an API
-   Separating scraping, summarization, and UI logic into Python modules
-   Building a lightweight interactive interface with Gradio
-   Managing API credentials through environment variables

------------------------------------------------------------------------

Built as part of my AI learning journey with Scaler.
