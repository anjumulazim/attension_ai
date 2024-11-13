# Academic Research Paper Assistant Application

## Overview
This application assists users in academic research by integrating various tools and agents to search, retrieve, store, and query research papers. It uses cutting-edge technologies like **Crewai**, **LangChain**, **Neo4j**,**Ollama** and **Groq** to offer an efficient and flexible solution for exploring academic content. The system allows users to find papers, extract relevant text, and generate research directions.

## Technologies Used
1. **CrewaI**: Manages agent workflows for automating tasks.
2. **LangChain**: Used for orchestrating large language models (LLMs) in agent interactions.
3. **Neo4j**: A graph database to store research papers and their associated data as nodes.
4. **Ollama**: Provides embeddings using the **nomic-text-embed** model to represent textual content.
5. **Groq**: Used to run the open Llama3.1:70b-versatile model for inference.

## Workflow
1. **Paper Download**: Research papers from the past 5 years are retrieved based on user input via **arXiv**.
2. **Node Creation**: Data is stored in Neo4j with nodes of type **Summary**, **Author**, and **Text**, along with vector embeddings for both summaries and text as it's properties.
3. **Query & Retrieval**: Users can query the database by year and topic. Agents return relevant information based on the user’s query.
4. **Future Works**: A dedicated agent is employed to analyze papers and identify potential future research directions.

## Tools 
1. **Download and Store Tool**: Downloads papers from **arXiv** and stores them in the Neo4j database.
2. **Search Tool**: Queries the database based on the year and topic.
3. **Vector Search Tool (Text)**: Retrieves relevant results based on user queries, using embeddings on text nodes.
4. **Vector Search Tool (Summary)**: Retrieves relevant results based on embeddings stored in summary nodes.

## Agents
1. **Search Agent**: Searches for papers based on user input and adds them to the database.
2. **Database Agent**: Queries the Neo4j database and retrieves context relevant to the user’s query, based on a specific topic and year.
3. **Q&A Agent**: A simple RAG-based agent that answers user queries using relevant context from the database.
4. **Future Works Agent**: Analyzes papers to suggest potential future works based on the content of the papers.

## Tasks
One task definition for each agent according to their role

## Setup and Installation

### Prerequisites
1. **Ollama**: Install **Ollama** and pull the **nomic-text-embed** model.
2. **Neo4j Desktop**: Install **Neo4j Desktop**, create an empty databasemwith **APOC** and **Graph Data Science Library** plugins.

### Environment Setup
1. **Clone the repository**:
   ```bash
   git clone https://github.com/anjumulazim/attension_ai
   ```

2. **Create and activate the Conda environment**:
   ```bash
   conda create --name research-assistant python=3.10
   conda activate research-assistant
   ```

3. **Install required packages**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Install Jupyter** and create a kernel for the Conda environment:
   ```bash
   conda install jupyter
   python -m ipykernel install --user --name=research-assistant
   ```

5. **Run Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```
   Select the **research-assistant** kernel in the Jupyter interface.

### Environment Variables
Set up the necessary environment variables for **Groq** and **Neo4j** in a `.env` file:
- **Groq API Key**: Obtain from Groq’s platform.
- **Neo4j Connection**: Set up the Neo4j credentials and URL.

Example `.env` file:
```bash
GROQ_API_KEY=your_groq_api_key
NEO4J_URI=neo4j://localhost:7687
NEO4J_USER=neo4j
NEO4J_PASSWORD=your_neo4j_password
```

### Groq Setup
1. Get your **Groq API Key**.
2. Choose an open model from Groq’s available options (e.g., **llama-3.1-70b-versatile**).

### Running the Notebook
1. After setting up, run the notebook to start the application.
   - The notebook will pull research papers, store them in Neo4j, and enable querying and text retrieval based on embeddings.
