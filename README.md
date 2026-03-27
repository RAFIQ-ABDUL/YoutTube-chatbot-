# Bilingual YouTube Chatbot

It is a Retrieval-Augmented Generation (RAG) engine designed to extract and query information from YouTube video transcripts. It features a specialized pipeline that seamlessly processes content and user queries in both **English** and **Urdu/Hindi**.

##  Key Features
* **Multilingual Support:** Handles English, Urdu, and Hindi transcripts and queries.
* **Automated Translation:** Uses `llama-3.3-70b` to translate non-English text for optimized vector embedding and search accuracy.
* **Efficient Retrieval:** Utilizes **FAISS** for fast similarity searches and **LangChain's** `RunnableParallel` for optimized execution.

##  Environment & Setup

### API Keys
To run this project, you will need:
1.  A **Groq API Key** (for the LLM).
2.  A **Hugging Face API Token** (for embeddings).

### Google Colab vs. Local Execution
The provided `.ipynb` file was originally developed in **Google Colab**. 
* **In Colab:** I used the `google.colab.userdata.get()` function to retrieve API keys.
* **In Local VS Code:** You must use a `.env` file and the `python-dotenv` library to manage your keys. **Do not hardcode your keys.**

#### Local Setup (VS Code)
1. **Clone the repository.**
2. **Create a `.env` file** in the root directory and add your keys:
   ```text
   Groq=your_groq_api_key_here
   HuggingFace_API_Key=your_hf_key_here
3. **Install dependencies:**:
   ```text
   pip install -r requirements.txt

## 📖 How It Works
* **Load:** Fetches the transcript from a YouTube URL using YoutubeLoader.
* **Translate & Split:** Detects the language of text chunks. If Urdu or Hindi is detected, it translates them to English before storing them to ensure better semantic matching.
* **Embed:** Converts text into vectors using sentence-transformers/all-MiniLM-l6-v2.
* **Query:** Translates user questions into English (if necessary) and retrieves the most relevant context from the FAISS vector store to generate a response.
