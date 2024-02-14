# Build LLM Apps with LangChain.js

## Introduction

This course introduces LangChain.js, a tool designed to simplify common steps in building LLM applications for JavaScript developers. For instance, in creating retrieval augmented generation (RAG) applications, developers must select an LLM, retrieve relevant texts, tune prompts, and structure outputs. Orchestration tools like LangChain facilitate these processes by connecting steps and allowing for easy modifications, such as swapping LLMs.

The course covers essential components of LLM applications, including data loaders, parsers, prompts, models, and modules supporting RAGs, alongside the LangChain Expression Language (LCEL) for composing complex module chains.

## 1. Building Blocks

This lesson introduces the basic building blocks of large language model (LLM) applications, focusing on prompt templates, models, parsers, and how to use LangChain Expression Language (LCEL) to create chains of these components. The motivation behind using LangChain.js is its alignment with JavaScript, the most widely used programming environment, offering easy deployment, powerful scaling features, and the ability to build across multiple platforms.

LangChain Expression Language facilitates the composition of components, or "runnables," which are key in building LLM applications. This lesson covers the implementation of runnables, including core methods and input/output types, and demonstrates how to use LangChain for creating more complex LLM applications efficiently.

The course proceeds to discuss different types of language models supported by LangChain, such as text LLMs and chat models, using OpenAI's GPT 3.5 Turbo as an example. It showcases how to initialize models, format inputs using prompt templates, and parse outputs for streamlined integration into applications. Additionally, it highlights the advantages of using prompt templates for reusable and parameterized components, making it easier to generate consistent and formatted inputs for models.

A significant part of the lesson is devoted to demonstrating how to chain together prompt templates and models using LCEL, allowing for the seamless flow of data between components and enhancing the application's functionality. It includes practical examples of invoking models, formatting prompts, and parsing outputs to produce desired results in a structured and efficient manner.

Moreover, the lesson touches on advanced features like fallbacks, parallelism, logging, and tracing integrated into LangChain through tools like LangSmith. It encourages hands-on experimentation with modifying prompts, templates, and chains to understand their interplay and potential for creating complex LLM applications.

By the end of the lesson, learners are expected to have a foundational understanding of creating and manipulating the core components of LLM applications using LangChain and LCEL, setting the stage for more advanced topics in subsequent lessons.

## 2. Loading and Preparing Data

This lesson introduces Retrieval Augmented Generation (RAG) as a significant application of large language models (LLMs), highlighting its popularity and the ease with which LangChain models facilitate its construction. RAG applications enhance LLM outputs by grounding them in context retrieved from various documents, making the generated content more relevant and informed.

The lesson outlines a basic workflow for building RAG applications:

1. **Loading Documents**: From sources like PDFs, databases, or the web, using LangChain's document loaders.
2. **Splitting Documents**: Breaking down documents into manageable chunks that fit within an LLM's context window to maintain focus and relevance.
3. **Embedding for Retrieval**: Storing document chunks in a vector store for easy retrieval based on input queries.
4. **Generation with Context**: Generating final outputs using the retrieved chunks as context.

The focus of this lesson is on the first two steps:

- loading documents and
- splitting them into suitable chunks.

For document loading, LangChain offers a variety of loaders, including one for GitHub repositories. These loaders facilitate the importation of documents from different sources, allowing for a broad definition of what constitutes data, from code files to PDF documents.

The lesson then moves to document splitting, a critical step to ensure that the LLM processes semantically related ideas together. It presents LangChain's text splitting abstractions, which allow for splitting documents based on the content's nature, such as using specific delimiters for code in GitHub files. The lesson offers examples of different strategies for splitting, including using language-specific features as separators for JavaScript code, to maintain meaningful chunks that the LLM can effectively interpret.

Further, the lesson demonstrates the application of these techniques through practical examples, such as loading and splitting the transcript of Andrew Ng's CS229 machine learning course. It emphasizes the importance of keeping chunks semantically coherent and the flexibility of LangChain's splitters to adjust parameters like chunk size and overlap for optimal splitting.

The conclusion hints at the next steps in the RAG application workflow, specifically embedding and adding chunks to a vector store for efficient retrieval, setting the stage for generating contextually enriched outputs. This introduction to RAG and document handling techniques underscores the capabilities of LangChain in simplifying the development of sophisticated LLM applications.

## 3. Vectorstores and Embeddings

This lesson dives into the integration of a vector database into the Retrieval Augmented Generation (RAG) workflow, which is pivotal for enhancing LLM applications with contextually relevant data. Following the initial steps of loading and splitting documents, this segment focuses on embedding these document chunks into a vector store for later retrieval based on input queries.

**Key Components and Process:**

- **Text Embedding Model**: Utilizes a model, such as OpenAI's hosted embeddings, to convert document contents into vectors. These vectors represent the documents in a form that a vector store can search over.

- **Vector Store**: A specialized database designed for natural language search capabilities. It allows for the retrieval of document chunks that are closely related to a user's query by searching for embeddings similar to the query's embedding.

- **Ingestion and Embedding**: The process of adding documents to the vector store involves converting the document contents into vector representations using an embeddings model. This conversion facilitates the later retrieval of relevant chunks.

**Practical Implementation:**

- The lesson illustrates how to use an in-memory vector store for demonstration purposes, acknowledging that a more robust solution would be preferred for production.

- Document chunks are embedded using OpenAI's model to generate vectors, which are then added to the vector store.

- The effectiveness of the vector store is showcased through a similarity search demonstration, highlighting how queries return relevant document chunks based on cosine similarity—a metric for comparing vector similarity.

**Retrievers:**

- Beyond direct similarity search in a vector store, the lesson introduces retrievers as a broader abstraction for fetching data relevant to a natural language query.

- Retrievers can be instantiated from a vector store and are designed to be compatible with LangChain's expression language (LCEL), enabling them to be chained with other modules like LLMs, parsers, and prompts.

- This chaining capability is critical for building complex RAG workflows that seamlessly integrate document retrieval with LLM generation.

**Educational Outcome:**

By the end of this lesson, learners are equipped with the knowledge to integrate vector databases into their RAG applications, understand the significance of embeddings in contextual retrieval, and appreciate the versatility of retrievers in orchestrating sophisticated LLM workflows. This foundation sets the stage for subsequent lessons focused on constructing retrieval chains, further advancing the learners' ability to develop enriched LLM applications.

## 4. Question Answering

This lesson focuses on constructing a conversational question-answering application using large language models (LLMs) and external data for context, demonstrating the culmination of concepts covered in previous lessons.

**Overview of the Construction Process:**

- **Initial Setup**: Begins with loading environment variables and preparing the CS229 PDF transcript through splitting and loading into a vector store using OpenAI embeddings.

- **Vector Store Initialization**: Utilizes a helper function for initializing the vector store with specified chunk size and overlap, aimed at simulating a production environment.

- **Retriever Creation**: A retriever is set up from the vector store to fetch documents relevant to a given natural language query, forming the basis for the retrieval chain.

**Building the Retrieval Chain:**

- **Document Retrieval Formatting**: Incorporates a wrapper around the retriever to format inputs and outputs, adjusting for the chain's requirements.

- **Chain Definition**: Defines a chain that takes an object as input, extracts a query, uses the retriever to fetch relevant documents, and formats these documents with XML-like tags for LLM processing.

- **Functionality Demonstration**: Tests the retrieval chain with a sample query, showcasing the ability to fetch and format document content relevant to course prerequisites.

**Synthesizing a Human-Legible Response:**

- **Prompt Construction**: Develops a prompt template for the LLM to interpret and answer questions based on the retrieved context, emphasizing the role of an experienced researcher.

- **Runnable Map Usage**: Applies a runnable map to manage input and output between document retrieval and the LLM, ensuring the prompt receives the correct format.

- **Augmented Generation Step**: Combines the document retrieval output with the LLM prompt in a sequence to generate a human-readable answer, highlighting the chain's capability to synthesize information into a concise response.

**Handling Follow-Up Questions:**

- **Challenges with Context**: Addresses the limitations of LLMs in maintaining conversational context, illustrated by attempting to answer a follow-up question without explicit reference.

- **Vector Store Query Limitation**: Demonstrates the vector store's inability to contextualize 'them' in a follow-up query, leading to irrelevant document retrieval.

**Conclusion and Next Steps:**

The lesson showcases the assembly of a retrieval-augmented LLM application for conversational question answering, highlighting the integration of document retrieval, prompt formulation, and LLM generation. It acknowledges the challenges in handling conversational context and foreshadows future lessons on improving conversational question-answering capabilities. This instructional segment effectively ties together the components of RAG applications, preparing learners for advanced topics in leveraging LLMs for contextually aware applications.

## 5. Conversational Question Answering

This lesson focuses on enhancing a question-answering chain with conversational capabilities to address the issue of memory retention across queries. By incorporating techniques to remember past interactions, the chain can handle follow-up questions more effectively, making it capable of understanding and responding to questions that reference previous answers.

**Steps to Enhance Conversational Capabilities:**

1. **Identifying the Problem**: The initial question-answering chain lacked the ability to remember past questions or answers, making it difficult to handle follow-up questions that refer to earlier interactions.

2. **Proposed Solution**: To address this, the lesson suggests incorporating chat history into the chain. This involves saving each interaction's question and the LLM's response, allowing the system to use this history as context for future questions.

3. **Implementing Chat History**: The process includes modifying the chain to store chat history and utilize it in prompts for the LLM. This enables the system to provide more contextually relevant answers by referencing past interactions.

4. **Rephrasing Questions with LLMs**: A new component is introduced to rephrase follow-up questions into standalone queries that can be understood without prior context. This step is crucial for ensuring the vector database and LLM can process the question effectively.

5. **Building a Rephrase Chain**: The lesson outlines creating a chain that takes a follow-up question and chat history, rephrases the question for clarity, and then proceeds with document retrieval and response generation based on the revised query.

6. **Testing and Iteration**: Examples demonstrate testing the enhanced chain with original and follow-up questions, illustrating how the system now effectively handles references to past information.

7. **Visualizing the Process**: The use of tracing tools like LangSmith is suggested to visualize the internal workings of the conversational chain, highlighting how chat history is utilized and how questions are rephrased and processed.

**Key Takeaways:**

- **Conversational Memory**: Incorporating chat history into the question-answering chain significantly improves the system's ability to handle conversational context, making it more adept at responding to sequences of related questions.

- **Rephrasing for Clarity**: Using an LLM to rephrase follow-up questions into standalone queries ensures that each question is understandable on its own, making the system more robust and capable of fetching relevant information from the vector database.

- **Flexibility and Customization**: The lesson emphasizes the adaptability of the chain, encouraging experimentation with prompts and parameters to optimize performance for different types of data and questions.

- **Preparation for Production**: The concluding remarks hint at future lessons focused on deploying the conversational chain in a production environment, including interactions with web APIs and HTTP, setting the stage for practical application development.

This lesson bridges the gap between basic question-answering capabilities and advanced conversational interactions, equipping learners with the skills to build more sophisticated and user-friendly LLM applications.

## 6. Shipping As a Web API

This lesson focuses on refining a conversational question-answering system by enhancing its capability to handle follow-up questions through rephrasing and incorporating an advanced output streaming mechanism for web environments. This involves integrating a rephrase question chain and an answer synthesis chain into the conversational retrieval system.

**Enhancements and Steps:**

1. **Rephrase Question Chain**: This component rephrases follow-up questions into standalone queries. It addresses the challenge of the LLM's lack of memory by converting references in follow-up questions into explicit standalone questions that the system can understand and process.

2. **Answer Synthesis Chain**: Takes the output from previous steps, including the rephrased question and the context retrieved from the vector database, and synthesizes a final response. This chain utilizes a prompt template enriched with placeholders for chat history, standalone questions, and document context, ensuring a comprehensive response grounded in the provided sources.

3. **HTTP Response Output Parser**: To adapt the system for web deployment, an HTTP response output parser is introduced. This parser facilitates the direct streaming of bytes from the LangChain output to the web server's response object, aligning with the native web response objects' expectations for byte streams rather than string streams. This adjustment allows for efficient data transfer in web applications.

4. **Session Management**: Recognizing the concurrent usage scenario of web applications, the lesson underscores the importance of managing individual user sessions. By generating a new message history for each session, the system ensures that users' interactions remain isolated, preventing cross-contamination of chat histories across different users.

5. **Server Setup and Streaming Responses**: A server is set up to handle requests, demonstrating how to parse incoming queries and session IDs from HTTP request bodies. The server utilizes the `.stream` method to initiate a streaming response, showcasing how to efficiently return the LLM's output to the client in a web environment.

6. **Security and Validation Considerations**: While the lesson focuses on the technical setup, it mentions the necessity of implementing authentication and input validation in production environments to ensure security and data integrity.

**Key Outcomes:**

- The lesson achieves a significant advancement in building conversational AI systems by addressing the limitations related to memory and context understanding. By enabling the system to rephrase follow-up questions and maintain a coherent chat history, it becomes more adept at providing relevant and accurate answers across a conversation.
- The introduction of byte stream output parsing and session-specific message history management tailors the system for scalable web deployments, where responsiveness and user isolation are critical.

- The practical demonstration of setting up a server and handling streaming responses illustrates the application of conversational AI in real-world web environments, paving the way for developers to integrate sophisticated AI-powered features into their applications.

This comprehensive approach, from enhancing conversational intelligence to adapting the system for web deployment, provides a robust framework for developing advanced AI-driven applications capable of engaging users in meaningful and context-aware conversations.
