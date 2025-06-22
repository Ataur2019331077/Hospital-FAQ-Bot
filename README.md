# 📘 FAQBot: Multilingual FAQ Assistant with E5 Embeddings, MongoDB Vector Search & Gemini API
## 🚀 Overview
**FAQBot** is an intelligent multilingual assistant designed to provide precise and context-aware answers to frequently asked questions. It combines the power of:

- 🧠 [intfloat/multilingual-e5-base](https://huggingface.co/) for sentence embeddings

- 📦 [MongoDB Atlas Vector Search](https://www.mongodb.com/products/platform/atlas-vector-search) for efficient semantic retrieval

- 🔮 [Google Gemini API](https://ai.google.dev/gemini-api/docs/api-key) for generating natural language responses

This system retrieves semantically similar FAQ content and uses a large language model to respond to user queries with relevant, well-formed answers.

## ✨ Features
- 🌍 Multilingual Support — Handles English and other major languages using E5 embeddings

- ⚡ Real-Time Vector Search — Powered by MongoDB Atlas for low-latency semantic lookup

- 🤖 LLM-Powered Responses — Integrates Gemini API for fluent, context-aware answers

- 📚 Modular & Extensible Design — Easily expandable with new data, languages, or interfaces

## 🛠️ Getting Started
1. Clone the Repository
    ```
    git clone [https://github.com/yourusername/faqbot.git](https://github.com/Ataur2019331077/Hospital-FAQ-Bot.git)
    cd /Hospital-FAQ-Bot
    ```
2. Install Dependencies
    ```
    pip install -r requirements.txt
    ```
3. Configure MongoDB Atlas
    - Create a free MongoDB Atlas cluster

    - Create a collection and enable Vector Search with the following index configuration:
      ```json
      {
        "fields": [
          {
            "type": "vector",
            "path": "embedding",
            "numDimensions": 768,
            "similarity": "cosine"
          }
        ]
      }
      ```
4. Set Environment Variables
Create a .env file in the root directory:
    ```
    MONGO_URI=<your-mongodb-uri>
    GEMINI_API_KEY=<your-gemini-api-key>
    ```
## 📄 Prepare Your FAQ Data
1. Create a file named faq.txt in the root directory.

2. Write your FAQ content, with each paragraph separated by a blank line:
    ```txt
    We provide dental services such as cleanings, fillings, extractions, and screenings.
    Emergency dental care is available for severe pain or trauma.
    ```
## 📥 Store Embeddings in MongoDB

Run the embedding script to process and store the FAQ data:
```
python store_faq.py
```
This script:

- Splits the faq.txt content into paragraphs

- Generates multilingual E5 embeddings

- Stores the paragraphs and their embeddings in MongoDB

## 🤖 Running FAQBot
Launch the FAQBot query pipeline:

```
python faqbot.py
```
What it does:
- Accepts user query input

- Generates query embedding

- Searches MongoDB for top-k relevant paragraphs

- Passes retrieved context to the Gemini API

- Outputs a complete natural language response

## 💬 Sample Interaction
**Input:**
```
query_text = "What kind of dental services do you offer?"
```
**Output:**
```
FAQBot Response:
We offer cleanings, fillings, extractions, oral cancer screenings, pediatric dentistry, orthodontic consultations, gum disease treatment, and emergency dental care.
```
## 🧾 Project Structure
```
├── .env                  # Environment variables
├── faq.txt               # Raw FAQ data
├── embed_faq.py          # Embeds and stores FAQs in MongoDB
├── faqbot.py             # Main script to handle queries
├── invoke_llm.py         # Handles Gemini API communication
├── requirements.txt      # Python dependencies
└── README.md             # Project documentation
```
## 🔭 Roadmap & Future Enhancements
- 🗣️ **Advanced Multilingual Query Handling** (e.g., Bengali, French, German)

- 🖥️ **Web Interface** with Gradio or Streamlit

- 🧠 **Persistent Memory** Layer via ChromaDB or Redis

- ⚙️ **Batch Processing & Monitoring Tools**

## 🙌 Acknowledgements
- [intfloat/multilingual-e5-base](https://huggingface.co/) for sentence embeddings

- [MongoDB Atlas Vector Search](https://www.mongodb.com/products/platform/atlas-vector-search) for fast retrieval

- [Google Gemini API](https://ai.google.dev/gemini-api/docs/api-key) for fluent and informative answers

## 📄 License
This project is licensed under the [MIT License](./LICENSE.md).
