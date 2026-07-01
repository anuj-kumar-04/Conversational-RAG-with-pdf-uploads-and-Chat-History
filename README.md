# Conversational RAG with PDF Uploads and Chat History

A powerful Streamlit-based application that enables conversational Q&A interactions with PDF documents using Retrieval-Augmented Generation (RAG) and persistent chat history.

## 🎯 Overview

This application combines cutting-edge AI technologies to create an intelligent document analysis tool that:
- Uploads and processes multiple PDF files
- Uses LangChain and Groq API for advanced language understanding
- Maintains conversation context across multiple queries
- Provides accurate, concise answers based on document content
- Stores chat history for session continuity

## ✨ Features

- **PDF Upload Support**: Upload one or multiple PDF files simultaneously
- **Intelligent RAG System**: Combines document retrieval with generation for accurate answers
- **Chat History Management**: Maintains conversation context across queries within a session
- **Session Management**: Create multiple chat sessions with unique session IDs
- **Context-Aware Responses**: Understands references to previous messages in the conversation
- **HuggingFace Embeddings**: Uses state-of-the-art embeddings for semantic search
- **Groq API Integration**: Leverages powerful language models for optimal performance

## 🛠️ Tech Stack

- **Frontend**: [Streamlit](https://streamlit.io/) - Interactive web interface
- **LLM Framework**: [LangChain](https://www.langchain.com/) - Orchestration of AI components
- **Language Model**: [Groq API](https://groq.com/) - Fast language model inference
- **Embeddings**: [HuggingFace](https://huggingface.co/) - Semantic embeddings (all-MiniLM-L6-v2)
- **Vector Store**: [Chroma](https://www.trychroma.com/) - Vector database for document embeddings
- **PDF Processing**: [PyPDF](https://github.com/py-pdf/PyPDF) - PDF loading and parsing
- **Language**: Python

## 📋 Requirements

- Python 3.8 or higher
- Groq API Key (get one at [console.groq.com](https://console.groq.com))
- HuggingFace API Token (get one at [huggingface.co](https://huggingface.co))

## 🚀 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/anuj-kumar-04/Conversational-RAG-with-pdf-uploads-and-Chat-History.git
   cd Conversational-RAG-with-pdf-uploads-and-Chat-History
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
   
   Key dependencies:
   - streamlit
   - langchain
   - langchain-groq
   - langchain-chroma
   - langchain-huggingface
   - langchain-text-splitters
   - langchain-community
   - python-dotenv
   - pypdf

4. **Set up environment variables**
   
   Create a `.env` file in the project root:
   ```
   HF_TOKEN=your_huggingface_token_here
   ```

## 💻 Usage

1. **Run the application**
   ```bash
   streamlit run app.py
   ```

2. **Access the web interface**
   - The app will open at `http://localhost:8501`

3. **Using the application**
   - Enter your Groq API key in the password field
   - Create or enter a Session ID for managing chat history
   - Upload one or multiple PDF files
   - Ask questions about the PDF content
   - The assistant will provide answers based on the document content while maintaining conversation context

## 🔑 How It Works

### Architecture

```
PDF Upload → Text Splitting → Vector Embeddings → Chroma Vector Store
                                                           ↓
                                    History-Aware Retriever (LangChain)
                                                           ↓
                                    Conversational RAG Chain
                                                           ↓
                                    Groq LLM Response Generation
                                                           ↓
                                    Chat History Management
```

### Process Flow

1. **Document Processing**
   - PDFs are uploaded and converted to text using PyPDFLoader
   - Text is split into chunks (5000 characters with 500-character overlap)

2. **Vector Embeddings**
   - Chunks are converted to embeddings using HuggingFace's `all-MiniLM-L6-v2` model
   - Embeddings are stored in Chroma vector database

3. **Context Retrieval**
   - User questions are contextualized with chat history
   - Relevant document chunks are retrieved based on semantic similarity

4. **Response Generation**
   - Groq API generates concise answers (max 3 sentences) using retrieved context
   - Responses are grounded in the document content

5. **History Management**
   - Chat history is maintained per session using ChatMessageHistory
   - Enables follow-up questions that reference previous context

## 📸 Demo

Check out the included demo files:
- **DEMO IMAGE.jpeg** - Screenshot of the application interface
- **DEMO VIDEO.mp4** - Video walkthrough of the application features

## 🎓 Example Usage

```
User: "What are the main topics covered in this document?"
Assistant: [Provides overview based on document analysis]

User: "Can you elaborate on the first point?"
Assistant: [Expands on the previously mentioned topic with context awareness]

User: "How does this relate to what was mentioned earlier?"
Assistant: [Connects current query with previous conversation context]
```

## 🔧 Configuration

You can customize the following parameters in `app.py`:

- **Chunk Size**: Modify `chunk_size=5000` in the RecursiveCharacterTextSplitter
- **Chunk Overlap**: Modify `chunk_overlap=500` for context continuity
- **Model Selection**: Change the model name in `ChatGroq(model_name="qwen/qwen3.6-27b")`
- **Embedding Model**: Change `model_name="all-MiniLM-L6-v2"` in HuggingFaceEmbeddings
- **Response Length**: Adjust the system prompt for different answer lengths

## 📝 API Keys Required

1. **Groq API Key**
   - Sign up at [console.groq.com](https://console.groq.com)
   - Generate an API key
   - Enter it in the Streamlit app when prompted

2. **HuggingFace Token**
   - Sign up at [huggingface.co](https://huggingface.co)
   - Generate a token in account settings
   - Add to `.env` file as `HF_TOKEN`

## 🐛 Troubleshooting

### Issue: "Invalid Groq API Key"
- Verify your API key is correct
- Check that you're using the latest API key from Groq console

### Issue: "HuggingFace Token Not Found"
- Ensure `.env` file exists in the project root
- Verify `HF_TOKEN` is set correctly in `.env`

### Issue: PDF Upload Not Working
- Ensure PDF is not corrupted
- Try uploading a smaller PDF file first
- Check file permissions

### Issue: Slow Response Times
- Reduce chunk size for faster processing
- Use smaller PDFs for testing
- Check your internet connection

## 📚 Dependencies Details

- **LangChain**: Framework for building with language models
- **Groq**: Ultra-fast LLM API for inference
- **Chroma**: In-memory vector database for embeddings
- **PyPDF**: PDF text extraction
- **Streamlit**: Web framework for data apps

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is open source and available under the MIT License.

## 👨‍💻 Author

**Anuj Kumar**
- GitHub: [@anuj-kumar-04](https://github.com/anuj-kumar-04)

## 🙋 Support

If you encounter any issues or have questions, please:
1. Check the troubleshooting section above
2. Review the code comments in `app.py`
3. Open an issue on GitHub

## 🚀 Future Enhancements

- Support for additional document formats (DOCX, TXT, PPT)
- Advanced RAG techniques like multi-query retrieval
- Persistent storage of chat history
- User authentication and multi-user support
- Document summarization features
- Export chat history functionality

## 🔗 Resources

- [LangChain Documentation](https://python.langchain.com/)
- [Streamlit Documentation](https://docs.streamlit.io/)
- [Groq API Documentation](https://console.groq.com/docs)
- [Chroma Documentation](https://docs.trychroma.com/)

---

**Built with ❤️ using LangChain, Streamlit, and Groq API**
