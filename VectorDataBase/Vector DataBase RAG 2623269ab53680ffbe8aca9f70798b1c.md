# Vector DataBase RAG

Created by: Moulica Vani Goli

# BackGround

Vector databases are a cornerstone of efficient RAG (Retrieval-Augmented Generation) systems. These specialized databases store and index vectors (numerical representations of data) to enable fast similarity search across large datasets. Key benefits include:

- Semantic search capabilities that understand context and meaning
- Efficient nearest neighbor search algorithms for quick retrieval
- Scalable architecture designed to handle billions of vectors
- Optimized for the high-dimensional embedding vectors used in modern AI systems

Popular vector database options include Pinecone, Weaviate, Milvus and Qdrant each with unique features for different use cases.

## Vector DataBase Operations

- Database setup ( Vector Database Typically collections)
- Load Documents ( Loading Docs)
- Create Sparse Vectors for Keyword Search(Same keyword)
- Create dense vectors for Semantic Search( Meaning)
- Run Searches
- Document management (adding, updating, or removing vector representations)

### Flow :

Configure Database —> Load and Index Data —>  Perform Searches 

### What is Chunking and what is its use in Vector database Searches ?

In vector databases, data is converted into vectors using embeddings and the quality of retrieval depends heavily on the chunk size used during embedding. If too many tokens are packed into a single vector (for example, embedding an entire book as one vector), the semantic meaning becomes diluted and the database may return poor or irrelevant results. 

Proper chunking ensures each vector captures a clear, focused piece of context (example a paragraph or section), making similarity search more accurate and meaningful. Therefore, selecting the right chunk size is crucial for effective vector search.

### Chunking Strategies

- Fixed Size Chunking
    
    This approach divides text into chunks of approximately equal size, often measured by the number of tokens or characters. For example, a document might be split into 512-token chunks, with each chunk becoming a separate vector in the database. While simple to implement, fixed-size chunking may sometimes split meaningful units of information.
    
- Overlapping Chunking
    
    This technique creates chunks with a certain amount of overlap between them. For instance, if using 500-token chunks with 100 tokens of overlap, the second chunk would start 400 tokens into the document, reusing the last 100 tokens from the previous chunk. This approach helps maintain context across chunk boundaries and improves retrieval quality when relevant information spans chunk boundaries.
    
- Recursive Character Splitting
    
    This approach recursively splits documents at natural breakpoints like paragraphs, sections, or sentences. The text is first divided at the highest level (e.g., chapters), then progressively into smaller semantic units. This method preserves the hierarchical structure of documents and maintains meaningful context within each chunk.
    
- Advanced Chunking Techniques
    - Semantic Chunking
    
    Semantic chunking divides text based on meaning rather than fixed size. It analyzes the content to identify natural semantic boundaries, creating chunks that preserve complete ideas or concepts. This approach creates more coherent chunks that better represent the underlying information, improving retrieval relevance in RAG systems.
    
    - Language Based Chunking
        
        Prompting LLM to create chunks .Include Instructions on type of chunks like keeping concepts together, adding breaks when new topic starts.
        
    - Context Aware Chunking
        
        This is similar to Language Based chunking so in the previous case we don’t label for each chunk here it provides a context for each chunk just like similar to summary 
        
    

### What is Query Parsing and How is important in Vector Database Search ?

Query parsing is the process of interpreting and restructuring a user’s query to make it more precise and effective for retrieval. Since users often phrase questions in diverse and sometimes ambiguous ways, raw prompts may include unnecessary details that obscure the true intent. By applying query parsing, irrelevant information is removed and the essential meaning or keywords are extracted. In the context of vector databases, effective query parsing ensures that the embeddings generated from the query accurately capture its semantic meaning, which significantly improves similarity matching and leads to more reliable retrieval results.

### Query Parsing Strategies

- Query Rewriting
    
    Iterate on the prompt for your query rewriter
    
- Named Entity Recognition
    
    Identifies and categorizes specific types of information within queries, enabling more
    targeted search and filtering strategies.
    
- Hypothetical Document Embeddings (HyDE)
    - Normally a retriever is matching prompts to documents
    - HyDE means the retriever is  matching docs ,one is the ‘perfect hypothetical one generated from the prompt
    

### **Retrieval and Ranking Models in Vector Search**

Once the prompt reaches the LLM, it is first converted into an embedding and used to fetch a large set of potentially relevant documents from the vector database (for example, the top 100). At this point, retrieval and ranking models come into play, they score and reorder these documents to surface the most relevant ones. Finally, only a smaller subset of the highest-ranked documents (for example, the top 5–10) are placed into the LLM’s context window. This ensures the model receives the most useful evidence for generating an accurate and contextually grounded answer, while avoiding overload from irrelevant or weakly related documents.

### Techniques Used for Retrieval and Ranking

- Bi Encoders
    
    Encode query and documents separately, efficient for large-scale retrieval but less precise.
    
- Cross Encoders
    
    Jointly encode query + document pairs, very accurate but computationally expensive, best for reranking a small set of candidates.
    
- ColBert
    
    Uses late interaction to balance scalability and accuracy, near cross-encoder performance at larger scale.
    
- Hybrid Approches
    
    Combine sparse (keyword/lexical) search with dense (vector) search for improved recall and precision.