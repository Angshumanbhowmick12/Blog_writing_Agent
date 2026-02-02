# Blog Writer Agent

An AI-powered blog content generation system that automatically creates technical blog posts using LangGraph, LLMs, and web research.

## 🎯 Overview

The Blog Writer Agent is a sophisticated content generation pipeline that:
- **Routes requests** based on content type (evergreen, hybrid, or news-driven)
- **Researches topics** using Tavily API for up-to-date information
- **Plans content** with structured outlines and section tasks
- **Generates sections** in parallel with targeted tone and style
- **Creates images** using AI-generated diagrams and visuals
- **Produces polished markdown** ready for publication

## 🚀 Features

- **Intelligent Routing**: Automatically determines if web research is needed
- **Multi-mode Support**: Supports closed-book, hybrid, and open-book content strategies
- **Parallel Processing**: Uses LangGraph for efficient task execution
- **Evidence-based Writing**: Cites sources and includes research links
- **Image Generation**: Automatically generates technical diagrams and visuals
- **Structured Output**: Produces clean markdown with proper formatting

## 📋 Prerequisites

- Python 3.8+
- Virtual environment (recommended)
- API Keys:
  - OpenAI API Key (`OPENAI_API_KEY`)
  - Tavily API Key (`TAVILY_API_KEY`)
  - Google API Key (`GOOGLE_API_KEY`) - for image generation

## 🔧 Installation

1. **Clone/Download the project**
   ```bash
   cd f:\projects\blog_writer_agent
   ```

2. **Create and activate virtual environment**
   ```bash
   python -m venv .venv
   .venv\Scripts\Activate.ps1
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   
   Create a `.env` file in the project root:
   ```env
   OPENAI_API_KEY="your-openai-api-key"
   TAVILY_API_KEY="your-tavily-api-key"
   GOOGLE_API_KEY="your-google-api-key"
   ```
   
   **Note:** Never commit `.env` to version control. It's in `.gitignore`.

## 📱 Usage

### Run the Streamlit Web UI
```bash
streamlit run blog_frontend.py
```

Then open your browser to `http://localhost:8501`

### Using the Application

1. **Enter Blog Topic**: Type your desired blog topic in the input field
2. **Set Publishing Date**: Choose the date for the blog (affects recency filtering)
3. **Review Plan**: The system generates a detailed outline with sections and target words
4. **Monitor Progress**: Watch real-time updates as sections are generated
5. **Download Output**: Get the final markdown, images, and evidence links

### Content Modes

- **Closed-book**: Evergreen content without web research (fast)
- **Hybrid**: Mixes evergreen knowledge with recent examples (balanced)
- **Open-book**: News/trend-focused with heavy research dependency (comprehensive)

## 📁 Project Structure

```
blog_writer_agent/
├── blog_backend.py          # Core LangGraph pipeline and logic
├── blog_frontend.py         # Streamlit UI
├── requirements.txt         # Python dependencies
├── .env                     # API keys (not tracked)
├── .gitignore              # Git ignore rules
├── README.md               # This file
├── images/                 # Generated diagrams and visuals
└── *.md                    # Output blog posts
```

## 🔐 Configuration

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `OPENAI_API_KEY` | OpenAI API key for GPT models | Yes |
| `TAVILY_API_KEY` | Tavily API key for web search | Yes |
| `GOOGLE_API_KEY` | Google API key for image generation | Yes |

### Streamlit Configuration

To customize Streamlit behavior, create `.streamlit/config.toml`:

```toml
[theme]
primaryColor = "#FF6B6B"
backgroundColor = "#FFFFFF"
secondaryBackgroundColor = "#F0F2F6"

[client]
showErrorDetails = true
```

## 🏗️ Architecture

The system uses **LangGraph** for orchestration:

```
START
  ↓
[Router] → Determines research needs
  ├→ Closed-book path (no research)
  ├→ Hybrid path (some research)
  └→ Open-book path (heavy research)
  ↓
[Research] → Tavily web search (if needed)
  ↓
[Orchestrator] → Creates detailed content plan
  ↓
[Worker] → Generates sections in parallel
  ↓
[Reducer] → Merges sections & generates images
  ↓
END
```

## 📦 Dependencies

- **LangChain**: LLM orchestration framework
- **LangGraph**: State machine for workflow management
- **Streamlit**: Web UI framework
- **Pydantic**: Data validation
- **Tavily**: Web search API client
- **langchain-openai**: OpenAI integration
- **langchain-tavily**: Tavily search integration

## 🐛 Troubleshooting

### 404 Error with OpenAI
- Verify `OPENAI_API_KEY` is correct
- Check API key hasn't expired or been revoked

### No Search Results
- Ensure `TAVILY_API_KEY` is valid
- Try with different, more specific queries

### Image Generation Fails
- Check `GOOGLE_API_KEY` is active
- Verify quota isn't exceeded
- Check internet connection

## 📝 License

Specify your license here (MIT, Apache 2.0, etc.)

## 🤝 Contributing

Contributions are welcome! Please:
1. Create a feature branch
2. Make your changes
3. Test thoroughly
4. Submit a pull request

## 📧 Support

For issues, questions, or suggestions, please open an GitHub issue.

---

**Last Updated**: February 3, 2026
