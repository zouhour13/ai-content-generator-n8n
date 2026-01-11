# Automated Blog Content Workflow (n8n)

## Overview
This workflow automates blog content generation using Google Sheets, Tavily API, and OpenAI.  
It retrieves content ideas from a Google Sheet, searches for relevant content using the Tavily API, and generates engaging blog posts with AI. The results are then written back to the Google Sheet automatically.

This project is built using **n8n**, a workflow automation tool, and leverages AI for content generation.

---

## Workflow Description

### Nodes:

1. **Manual Trigger**  
   - Node: `When clicking ‘Execute workflow’`  
   - Starts the workflow manually when executed in n8n.

2. **Get Rows from Google Sheet**  
   - Node: `Get row(s) in sheet`  
   - Fetches content ideas from a Google Sheet.  
   - Uses OAuth2 credentials for Google Sheets.  
   - Retrieves the `content` column for further processing.

3. **HTTP Request (Tavily API)**  
   - Node: `HTTP Request`  
   - Sends a POST request to Tavily API to search content based on the idea title.  
   - Retrieves relevant content snippets.  

4. **Aggregate Content**  
   - Node: `Aggregate1`  
   - Aggregates multiple content results from Tavily into a single field for the AI agent.

5. **AI Agent (LangChain)**  
   - Node: `AI Agent`  
   - Uses aggregated content and title to generate a complete, engaging blog post.  
   - Ensures posts are at least 1000 words and suitable for website blogs.

6. **OpenAI Chat Model**  
   - Node: `OpenAI Chat Model`  
   - Optional: Uses OpenAI GPT-4.1-mini to enhance content quality and engagement.

7. **Update Google Sheet**  
   - Node: `Update row in sheet`  
   - Writes the generated blog post back to the Google Sheet in the `content` column.  
   - Matches rows by title.

---

## Features

- Reads content ideas from a Google Sheet  
- Searches related content via the [Tavily API](https://www.tavily.com/)  
- Generates blog posts using [OpenAI](https://openai.com/)  
- Updates Google Sheet automatically with generated content  
- Fully automated workflow with manual trigger  


## Setup Instructions

1. **Clone the repository**  
   ```bash
   git clone <your-repo-url>
   cd <your-repo>
2. **Create a .env file (local only)**

   ```bash
   TAVILY_API_KEY=your_tavily_api_key
   OPENAI_API_KEY=your_openai_api_key```


3. **Install n8n (if not installed)**
   ```bash
   npm install n8n -g
4. **Run n8n**
    ```bash
    n8n
 Import workflow.json.

Click Execute workflow to start.  


## 🎥 Demo Video

Découvrez une démonstration complète du projet dans la vidéo ci-dessous :

<p align="center">
  <a href="https://youtu.be/P_ZZyWOBo1Q" target="_blank">
    <img src="https://img.youtube.com/vi/P_ZZyWOBo1Q/maxresdefault.jpg" 
         alt="Demo Video" 
         width="80%" />
  </a>
</p>

<p align="center">
  ▶️ <strong><a href="https://youtu.be/P_ZZyWOBo1Q" target="_blank">Watch the demo on YouTube</a></strong>
</p>

## Security Notes

- **Secrets Management:** All API keys are stored in a `.env` file and **never committed to GitHub**.  
- **Ignored Files:** `.env`, `.env.*`, and `credentials.json` are listed in `.gitignore` to protect sensitive information.

## Dependencies

- **[n8n](https://n8n.io/)** – Workflow automation platform  
- **[Google Sheets OAuth2](https://developers.google.com/identity/protocols/oauth2)** – For reading and writing spreadsheet data  
- **[Tavily API](https://tavily.com/)** – Content search API  
- **[OpenAI API](https://platform.openai.com/docs/guides/overview)** – AI-powered text generation

   
