# Building Systems with the ChatGPT API

## Introduction

The chapter introduces building complex applications using the ChatGPT API, emphasizing the transition from simple prompt engineering to constructing multifaceted systems that involve multiple calls to a Large Language Model (LLM). It aims to teach best practices for developing applications that require sequential processing and interaction with LLMs, using an end-to-end customer service assistant as a running example. This system demonstrates how to handle user inputs by evaluating content, identifying query types, retrieving relevant information, and generating helpful responses, all while ensuring the output is appropriate and accurate.

Key points include:

- **Sequential Processing**: The need for applications to process user inputs through multiple internal steps to produce the final output, often involving various instructions and external information sources.

- **System Improvement**: Strategies for evaluating and enhancing LLM-based applications over time to maintain their effectiveness and relevance.

## 1. Language Models, the Chat Format and Tokens

The chapter provides an introductory overview of Large Language Models (LLMs) focusing on their training, operational mechanisms, and practical applications. It emphasizes the complexity behind LLMs like ChatGPT, detailing supervised learning as the foundational training method, the significance of tokenization in processing inputs, and the advanced techniques used to refine these models for specific tasks.

Key points include:

- **Supervised Learning**: The primary method for training LLMs, where models learn from labeled data to predict outputs based on given inputs. This method underpins the ability of LLMs to generate text based on prompts.

- **Instruction Tuned LLMs**: An advancement over base LLMs, these models are fine-tuned to follow instructions more accurately, improving their utility in practical applications.

- **Tokenization**: A crucial step in LLM functioning, where input text is broken into manageable pieces, or tokens, affecting the model's output.

- **Chat Completions Format**: This format allows for specifying system and user messages, guiding the LLM's responses to align with the intended application, such as adopting a specific tone or style.

- **Practical Example**: A detailed walkthrough of using LLMs to build a custom chatbot, demonstrating how to input system and user messages to tailor the chatbot’s responses.

- **Security Practices**: The text advises on secure practices for handling API keys, recommending environmental variables over hard-coding keys in scripts.

- **Prompting Revolution**: Highlighting the shift in AI application development, the chapter underscores how prompting LLMs can drastically reduce development time from months to hours for text-based applications, though it notes this efficiency primarily applies to unstructured data applications.

The discussion aims to equip learners with an understanding of LLMs' inner workings and their application in creating sophisticated AI-driven systems, setting the stage for further exploration into building a customer service assistant system.

## 2. Evaluate Inputs: Classification

The chapter discusses a method for improving the functionality and safety of AI-driven customer service systems by evaluating user inputs through classification. It highlights the importance of categorizing customer queries into primary and secondary categories to tailor the system's responses more effectively.

Key points include:

- **Query Classification**: The process involves classifying customer service queries into predefined primary and secondary categories. This classification enables the system to apply specific instructions tailored to the nature of the query.

- **Use of Delimiters**: Delimiters, like hashtags, are employed to separate parts of the instruction or output, aiding the model in identifying different sections of a query or response.

- **Structured Output**: The system generates structured outputs in JSON format, categorizing queries into primary and secondary categories, making it easier for developers to process these classifications programmatically.

- **Practical Examples**: Demonstrations show how the model classifies a request to delete a user profile under "account management" and "close account," and a product inquiry under "general inquiry" with relevant secondary categorization.

- **Subsequent Processing**: Based on the query's classification, the system can then provide a set of detailed instructions for handling the query, such as providing additional product information or instructions for account closure.

This approach allows for more nuanced and accurate responses to customer queries, enhancing the effectiveness of AI customer service systems.

## 3. Evaluate Inputs: Moderation

The chapter outlines methods for ensuring the responsible use of AI systems by users, focusing on content moderation and the prevention of prompt injections. It introduces OpenAI's Moderation API as a tool for identifying and filtering prohibited content across various categories, like hate speech and violence, providing a framework for developers to maintain system integrity. Furthermore, it delves into strategies for detecting and mitigating prompt injections, where users attempt to manipulate the system to produce unintended outputs.

Key points include:

- **Content Moderation with OpenAI's Moderation API**: This API helps developers identify prohibited content, allowing for the creation of safer AI applications by filtering inputs and outputs based on OpenAI's usage policies.

- **Preventing Prompt Injections**: The text describes prompt injections as user attempts to bypass the intended use of an AI system, offering strategies to prevent such abuses. This includes using delimiters to separate instructions and ensuring that system responses adhere to predefined behaviors, regardless of user manipulation attempts.

- **Structured Output for Easy Processing**: By requesting outputs in JSON format, developers can easily process AI responses programmatically, applying further logic based on the AI's classification of user queries.

- **Practical Examples**: The text provides practical examples of how to implement these strategies, including how to use the Moderation API to flag inappropriate content and how to structure prompts to prevent and detect prompt injections effectively.

- **Advanced Language Models and Future Directions**: It mentions advancements in language models, such as GPT-4, which are better at following instructions and resisting prompt injections, pointing towards a future where such strategies might be less necessary but still beneficial for enhancing system security and integrity.

Overall, the chapter emphasizes the importance of building AI systems that are not only functional but also secure and responsible, guiding developers on implementing safeguards against misuse.

## 4. Process Inputs: Chain of Thought Reasoning

The chapter discusses strategies for processing inputs with Large Language Models (LLMs), focusing on "Chain of Thought Reasoning" and the concept of an "Inner Monologue." These approaches help the model reason through problems more methodically before generating a final answer, improving accuracy and relevance in responses, especially in complex scenarios like customer service.

Key points include:

- **Chain of Thought Reasoning**: This strategy involves asking the model to break down its reasoning process into steps before arriving at a conclusion, allowing it to tackle problems more methodically and avoid premature or incorrect conclusions.

- **Inner Monologue**: This approach involves hiding the model's detailed reasoning from the user, presenting only the relevant parts of the output. This can be useful in contexts where revealing the full reasoning process might be inappropriate, such as in educational applications.

- **Content Moderation and Prompt Injections**: The discussion also touches on the importance of moderating content to ensure responsible system use and strategies to prevent users from manipulating the system via prompt injections.

- **Structured Output for Easy Parsing**: By instructing the model to generate outputs in a structured format, developers can more easily parse and utilize the data in subsequent steps or applications.

Through practical examples, the chapter illustrates how these strategies can be applied in a customer service context, showing how to classify customer queries, reason about product information, and correct user misconceptions—all while maintaining a friendly and appropriate tone. This approach underscores the versatility and potential of LLMs in creating sophisticated, multi-step systems that require nuanced understanding and response generation.

## 5. Chaining Prompts

The chapter discusses a method for handling complex tasks with Large Language Models (LLMs) by breaking them into simpler subtasks and chaining multiple prompts together. This approach, compared to using a single complex prompt or chain of thought reasoning, is likened to cooking a meal in stages for better management and accuracy, or to modular programming for clearer logic and easier debugging.

Key insights include:

1. **Chaining Multiple Prompts**: This method involves handling a task through a series of simpler prompts, allowing for state maintenance and action determination based on current state, akin to cooking a meal in stages or modular programming.

2. **Benefits**: It simplifies management, ensures the model has necessary information, reduces errors, and can be more cost-effective. It also facilitates testing and potential human intervention at specific stages.

3. **Complexity Management**: The approach is particularly useful for workflows with multiple possible states or actions, making complex tasks more manageable.

4. **Use of External Tools**: Chaining prompts allows for the integration of external tools or information retrieval at certain workflow points, enhancing the model's capability.

5. **Structured Output**: Generating structured responses (e.g., in JSON format) from prompts enables easy parsing and subsequent steps, improving the system's efficiency in handling queries.

6. **Selective Information Loading**: Dynamically loading relevant information into prompts, rather than including all possible data, addresses context limitations, reduces costs, and avoids confusing the model with unnecessary information.

7. **Future Directions**: The discussion hints at advanced techniques like using text embeddings for efficient knowledge retrieval, promising more semantic search capabilities without exact keyword matches.

Through an example of a customer service query regarding products, the chapter illustrates how chaining prompts allows for detailed product information retrieval and tailored responses, showcasing the practical application and benefits of this approach. The strategy emphasizes the importance of providing LLMs with relevant context for effective reasoning and response generation, underscoring the evolving techniques for leveraging AI in complex systems.

## 6. Check Outputs

The chapter outlines methods for checking the quality, relevance, and safety of outputs generated by AI systems before presenting them to users. It emphasizes the importance of ensuring outputs meet certain standards, especially for sensitive audiences, and introduces two main approaches for output evaluation:

1. **Moderation API**: Similar to its application for evaluating inputs, the Moderation API can also be used to filter and moderate outputs generated by the system. It identifies and classifies content into specific categories, such as hate speech or violence, allowing for appropriate action if the content is flagged. This tool is critical for maintaining content compliance and ensuring responses are safe for all users.

2. **Self-Evaluation by the Model**: Another strategy involves asking the model itself to evaluate the quality of its output against predefined criteria. This could include checking if the response sufficiently answers a customer's question, if it adheres to factual accuracy based on provided product information, and if it aligns with brand guidelines or specific rubrics. This method involves structuring a prompt that includes the generated output, relevant product information, and specific questions for the model to assess its response with a simple "Yes" or "No."

The chapter suggests that while using the model for self-evaluation can provide immediate feedback on the quality of responses, it may not be necessary in most cases, especially with more advanced models like GPT-4, which are less prone to generating harmful or irrelevant content. Additionally, this approach could increase the latency and cost of the system due to the need for extra processing and evaluation steps.

Ultimately, the chapter advises caution in implementing self-evaluation in production environments, considering it more of an exploratory tool for ensuring output quality in specific scenarios where extremely low error rates are critical.

## 7. Build an End to End System

The chapter demonstrates how to create an end-to-end customer service assistant using the techniques learned throughout the course. It outlines a process that includes the following steps:

1. **Checking the User Input**: Initially, the input is checked using the moderation API to ensure it doesn't contain any inappropriate content. If flagged, the system notifies the user that the request cannot be processed.
2. **Extracting Product Information**: If the input passes moderation, the system extracts a list of mentioned products.
3. **Product Lookup**: The system attempts to find detailed information about the extracted products.
4. **Answering the User Question**: With the product information available, the model generates a response to the user's query.
5. **Moderating the Output**: Before presenting the response to the user, it is again checked with the moderation API to ensure its appropriateness.

The process involves a Python package for UI interactions and a "process_user_message" function that orchestrates these steps. The function includes conditions for handling different outcomes at each step, such as dealing with flagged content or responding when no products are found.

The demonstration continues with a UI example where a conversation with the assistant unfolds, showcasing the system's capability to answer questions about products, including identifying the cheapest and most expensive TVs and providing detailed information about specific items.

This comprehensive system represents the application of various strategies learned throughout the course, including input evaluation, product information retrieval, and output moderation. It highlights the importance of continuously monitoring and improving the system by adjusting prompts, refining steps, and exploring better information retrieval methods to enhance performance and user experience.

## 8. Evaluation Part I

The chapter discusses best practices for evaluating and improving the outputs of applications built with Large Language Models (LLMs), focusing on a development approach distinct from traditional machine learning methods. Instead of starting with a large test set, the process often involves incrementally building a set of test examples based on encountered challenges. Here's a summary of the approach and steps highlighted in the video:

1. **Quick Start with Few Examples**: Initially, prompts are tuned using a small number of examples (1-5) to get something working quickly, within minutes to hours.

2. **Incremental Addition of Tricky Examples**: As the system is tested, occasionally tricky examples that the prompt fails on are added to the test set. This helps in gradually improving the system's ability to handle diverse inputs.

3. **Development of Metrics**: Over time, as more examples are collected, it becomes cumbersome to manually check each one. At this stage, metrics like average accuracy are developed to automate the evaluation process.

4. **Optional Expansion to Randomly Sampled Sets**: If further confidence in the system's performance is needed, a larger, randomly sampled set of examples may be collected for more rigorous tuning.

5. **Use of a Hold-Out Test Set**: For an unbiased estimate of performance, especially when fine-tuning for high accuracy, a hold-out test set that is not used in tuning may be collected.

The chapter emphasizes that for many applications, particularly those with low risk of harm, stopping at the early stages of this process is often sufficient. However, for high-stakes applications where incorrect outputs could cause harm, rigorous evaluation with large test sets is crucial.

To illustrate the process, the chapter walks through an example of building a customer service assistant that categorizes user queries and retrieves relevant product information. It demonstrates how to start with a basic prompt and iteratively refine it based on a growing set of test examples. The system's workflow includes:

- Checking inputs with a moderation API.
- Extracting and looking up product information.
- Generating and moderating outputs before presenting them to users.

The chapter showcases a practical implementation, including the use of utility functions for handling product information and evaluating the model's responses against a set of desired outputs. It concludes with a demonstration of automated testing across a development set, highlighting the efficiency of prompt-based development and the iterative process of prompt tuning and evaluation.

This approach to building and evaluating LLM applications allows for rapid development and iteration, making it possible to create effective AI systems quickly, with the caveat of ensuring sufficient evaluation for applications where accuracy and safety are critical.

## 9. Evaluation Part II

The chapter explores strategies for evaluating outputs from Large Language Models (LLMs) when the generated text does not have a single correct answer. It focuses on using rubrics for evaluation and comparing outputs to ideal responses. Here's a structured summary:

1. **Introduction**: The chapter begins by acknowledging the challenge of evaluating LLM outputs when there isn't just one correct response. It sets the context with an example of generating customer service responses and the need for a methodical evaluation approach.

2. **Evaluation with Rubrics**: A rubric, a set of guidelines or criteria, is introduced as a tool for evaluating LLM outputs. The chapter demonstrates creating a prompt that instructs the LLM to evaluate its own output against this rubric, focusing on factual accuracy, consistency with provided context, and whether it answers the user's queries without introducing unverified information.

3. **Example Evaluation**: An example is shown where the LLM evaluates a customer service response based on provided context and a rubric. This method checks if the response is based solely on the provided context, if it introduces any new, unverified information, and if it satisfactorily answers the customer's questions.

4. **Use of Higher Model Versions for Evaluation**: The chapter suggests that for a more robust evaluation, one might consider using a more advanced version of the LLM, such as GPT-4, especially for evaluating outputs, even if a lower version like GPT-3.5 Turbo is used for generating responses.

5. **Evaluation with Ideal Responses**: Another approach is comparing the LLM's output against an "ideal" response written by an expert. This method assesses how closely the generated text aligns with the ideal response, using a detailed rubric to grade the comparison on several aspects, such as completeness, consistency, and factual accuracy.

6. **Using External Evaluation Frameworks**: The chapter highlights the OpenAI open-source evals framework as a resource for finding evaluation methods and contributing new ones. This framework allows for the systematic comparison of LLM outputs against ideal responses or specific evaluation criteria.

7. **Design Patterns for Evaluation**: Two key design patterns emerge from the video:

   - **Rubric-Based Evaluation**: One LLM can evaluate another's output against a predefined set of criteria.
   - **Comparison to Ideal Responses**: LLMs can compare their outputs to expert-written responses to assess quality and accuracy.

8. **Practical Implications**: The chapter emphasizes that these evaluation strategies enable continuous monitoring and improvement of LLM systems. By using rubrics and comparing outputs to ideal answers, developers can iteratively refine their models to produce more accurate and helpful responses.

The overall message is that effective evaluation of LLM outputs, especially in applications where the "correct" answer varies, requires creative use of rubrics and comparisons to ideal responses. These methods help ensure the quality and relevance of the LLM's outputs, enabling continuous improvement of the system.
