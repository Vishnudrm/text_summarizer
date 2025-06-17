# 🤖 AI-Powered Text Summarizer

> Transform lengthy texts into concise, actionable summaries using DeepSeek-R1 AI model with beautiful web interfaces.

## ✨ Features

- **🎯 Smart Summarization**: Generates precise 3-bullet-point summaries
- **🌐 Web Interface**: Interactive Gradio-based UI for easy text input
- **⚡ REST API**: FastAPI backend for programmatic access
- **🔄 Real-time Processing**: Instant summarization without streaming delays
- **📱 Responsive Design**: Works seamlessly across all devices

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Ollama installed and running locally
- DeepSeek-R1 model downloaded in Ollama

### Installation

1. **Clone or download the project files**

2. **Install dependencies**
   ```bash
   pip install gradio fastapi requests uvicorn
   ```

3. **Start Ollama service**
   ```bash
   ollama serve
   ```

4. **Pull DeepSeek-R1 model**
   ```bash
   ollama pull deepseek-r1
   ```

## 🎮 Usage

### Web Interface (Gradio)

Run the interactive web application:

```bash
python gradio_app.py
```

- Open your browser to the displayed URL (typically `http://localhost:7860`)
- Paste your text in the input box
- Click "Submit" to get your summary
- View results in the output panel

### REST API (FastAPI)

Launch the API server:

```bash
uvicorn fastapi_app:app --reload
```

**API Endpoint**: `POST /summarize/`

**Example Request**:
```bash
curl -X POST "http://localhost:8000/summarize/" \
     -H "Content-Type: application/json" \
     -d '{"text": "Your long text here..."}'
```

**Example Response**:
```json
{
  "response": "• Key point 1\n• Key point 2\n• Key point 3"
}
```

## 📁 Project Structure

```
ai-text-summarizer/
├── gradio_app.py      # Web interface application
├── fastapi_app.py     # REST API server
└── README.md          # This file
```

## 🛠️ Configuration

### Model Settings

Both applications use the DeepSeek-R1 model by default. To use a different model:

1. Change the `model` parameter in the payload
2. Ensure the model is available in your Ollama installation

### API Endpoint

The default Ollama endpoint is `http://localhost:11434/api/generate`. Update the `OLLAMA_URL` variable if your setup differs.

## 💡 Use Cases

- **📚 Research**: Quickly digest academic papers and articles
- **📰 News**: Get key points from lengthy news articles
- **📋 Reports**: Extract essential information from business documents
- **📖 Content**: Summarize blog posts and web content
- **📧 Communication**: Condense long emails and messages

## 🔧 Troubleshooting

### Common Issues

**Connection Error**: Ensure Ollama is running on port 11434
```bash
ollama serve
```

**Model Not Found**: Verify DeepSeek-R1 is installed
```bash
ollama list
ollama pull deepseek-r1
```

**Port Conflicts**: Change ports in the launch commands
```python
# For Gradio
interface.launch(server_port=7861)

# For FastAPI
uvicorn fastapi_app:app --port 8001
```

## 🎨 Customization

### Summary Format

Modify the prompt in the `summarize_text` function:

```python
"prompt": f"Summarize the following text in **5 key insights**:\n\n{text}"
```

### UI Styling

Customize the Gradio interface:

```python
interface = gr.Interface(
    # ... existing parameters ...
    theme="huggingface",
    css="custom.css"
)
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📞 Support

Having issues? Check these resources:

- [Ollama Documentation](https://ollama.ai/docs)
- [Gradio Documentation](https://gradio.app/docs)
- [FastAPI Documentation](https://fastapi.tiangolo.com)

---

**Made with ❤️ using DeepSeek-R1, Gradio, and FastAPI**