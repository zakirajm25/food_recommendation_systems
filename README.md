# 🍲 Food Recommendation Systems: A Progressive RAG Approach

This repository demonstrates the evolution of a Food Recommendation System, progressing from a standard vector-based search to a fully realized Retrieval-Augmented Generation (RAG) application. 

The project compares three distinct architectures built using **Python**, **ChromaDB**, and **IBM watsonx.ai**, showcasing how integrating Large Language Models (LLMs) significantly enhances the user experience and recommendation quality.

---

## 🏗️ System Architectures

### 1. Basic Vector Search (ChromaDB)
The foundation of our recommendation engine.
* **Core Technology:** Python, ChromaDB.
* **How it works:** Food items (names, descriptions, ingredients) are embedded and stored in ChromaDB. When a user queries the system (e.g., "I want a high-protein breakfast"), the query is vectorized, and the system retrieves the top-K closest food items based strictly on cosine similarity.
* **Pros:** Extremely fast, simple to implement.
* **Cons:** Returns raw data without context; lacks ability to reason about complex user preferences.

### 2. Enhanced Vector Search (ChromaDB)
An optimized approach focusing on metadata and advanced querying.
* **Core Technology:** Python, ChromaDB.
* **How it works:** Builds upon the basic system by incorporating robust metadata filtering. Food vectors are stored alongside metadata tags (e.g., `cuisine`, `calories`, `dietary_restrictions`). The system performs a hybrid search—filtering by constraints *before* or *during* the semantic similarity search.
* **Pros:** Much more accurate for specific user constraints (e.g., "Find vegan desserts under 300 calories").
* **Cons:** Still returns a static list; relies entirely on the quality of the predefined metadata.

### 3. LLM-Powered RAG System (ChromaDB + IBM watsonx.ai)
The state-of-the-art conversational recommendation engine.
* **Core Technology:** Python, ChromaDB, IBM watsonx.ai.
* **How it works:** Implements a full Retrieval-Augmented Generation pipeline.
  1. **Retrieval:** Uses ChromaDB to fetch the most relevant food profiles based on the user's query.
  2. **Augmentation:** Structures the retrieved food data and the original user query into a comprehensive prompt context.
  3. **Generation:** Passes the augmented prompt to an **IBM watsonx.ai** Large Language Model. The LLM synthesizes the information to provide a personalized, conversational response, explaining *why* specific foods are recommended.
* **Pros:** Highly personalized, explains reasoning, handles complex and conversational queries gracefully.
* **Cons:** Higher latency and computational cost due to the LLM generation step.

---

## 📊 Systems Comparison

| Feature | System 1: Basic Vector Search | System 2: Enhanced Vector Search | System 3: LLM-Powered RAG |
| :--- | :--- | :--- | :--- |
| **Core Engine** | ChromaDB (Semantic) | ChromaDB (Semantic + Metadata) | ChromaDB + IBM watsonx.ai |
| **Output Format** | Raw list of matched items | Filtered list of matched items | Conversational, natural language response |
| **Contextual Awareness** | Low | Medium | **High** |
| **Reasoning Capabilities** | None | Limited (via metadata rules) | **Advanced (via LLM)** |
| **Implementation Complexity**| Low | Medium | High |
| **Latency** | Extremely Low | Low | Medium (Depends on LLM) |

---

## 🚀 Getting Started

### Prerequisites
* Python 3.8+
* IBM Cloud account with access to Watsonx.ai

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/food-recommendation-rag.git
   cd food-recommendation-rag
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up your environment variables (e.g., in a `.env` file):
   ```env
   WATSONX_API_KEY=your_ibm_cloud_api_key
   WATSONX_PROJECT_ID=your_watsonx_project_id
   ```

### Running the Systems
Each system can be run independently to observe the differences in output quality:

* **Run System 1 (Basic):** `python basic_chroma_search.py`
* **Run System 2 (Enhanced):** `python enhanced_chroma_search.py`
* **Run System 3 (RAG):** `python watsonx_rag_system.py`

*(Note: Replace the script names above with your actual file names).*

---

## 🛠️ Built With
* [ChromaDB](https://www.trychroma.com/) - The open-source AI-native vector database.
* [IBM watsonx.ai](https://www.ibm.com/products/watsonx-ai) - Enterprise studio for AI builders.
* [Python](https://www.python.org/) - The programming language used.

## 🤝 Contributing
Contributions, issues, and feature requests are welcome!

## 📝 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
