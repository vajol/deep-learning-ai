# ChatGPT Prompt Engineering for Developers

# Requirements

Notebooks in this course use older version of "openai" library. To run the code successfully, you can either pin the ld version with 'pip install openai==0.28', or use newer version of the code, as suggested in the first notebook.

# Introduction

The course aims to teach developers how to effectively use Large Language Models (LLMs) in software development, emphasizing the underappreciated potential of using LLMs through API calls for building software applications.

Course focus is on leveraging instruction-tuned LLMs for developing software applications and the emphasis on clear, effective prompting techniques.

Key details include:

- The course focuses on instruction-tuned LLMs, which are designed to follow instructions and are recommended for practical applications due to their ability to be more helpful, honest, and harmless.

- It covers prompting best practices for software development, common use cases (summarizing, inferring, transforming, expanding), and building a chatbot using an LLM.

- The distinction between base LLMs (trained to predict the next word) and instruction-tuned LLMs (trained to follow instructions and refined with RLHF - Reinforcement Learning from Human Feedback) is explained.

- Best practices for instruction-tuned LLMs involve being clear and specific in instructions, similar to how one would guide a smart individual unfamiliar with the specifics of a task.

## Guidelines for Prompting

The principles for effective prompt engineering with ChatGPT include writing clear, specific instructions and giving the model time to think.

- **Clear and Specific Instructions**: Encourage the use of delimiters to separate text elements, structure outputs (e.g., in JSON format), check for conditions before proceeding, and use few-shot prompting to provide examples for the model.

- **Time to Think**: Advise breaking down tasks into steps for the model to follow, ensuring more accurate and thoughtful responses. This includes specifying steps for complex reasoning tasks and allowing the model to compare its solution to a given one, enhancing accuracy.

The guidelines also cover setting up the OpenAI Python library to access the API, the importance of API keys, and the use of GPT-3.5 Turbo for exercises. Techniques to avoid prompt injections and hallucinations are discussed, with emphasis on generating reliable and traceable responses from the model.

## Iterative Prompt Development

This part delves into the iterative process of developing effective prompts for applications utilizing large language models (LLMs). It underscores that finding the optimal prompt rarely happens on the first attempt, emphasizing the importance of a methodical approach to refining prompts based on the results obtained from initial trials. It draws parallels between this process and machine learning model development, where an idea undergoes multiple iterations of implementation and evaluation to enhance performance.

Key insights include:

- **Iterative Development**: The process involves starting with an initial prompt, evaluating its effectiveness, and then refining it based on the outcomes. This cycle is repeated until the prompt effectively meets the application's requirements.

- **Prompt Refinement Strategies**: It illustrates how to adjust prompts to control output length, focus on specific content (e.g., technical details for a marketing description), and include precise elements (like product IDs), showcasing how different instructions can yield varied results.

- **Practical Application**: Through a concrete example of creating a product description from a fact sheet, this part demonstrates how to iteratively refine the prompt to meet specific goals, such as shortening the description, focusing on technical details, and formatting the output as HTML.

- **Evaluation Against Diverse Examples**: For more sophisticated applications, evaluating prompts against a broad set of examples is recommended to gauge average and worst-case performance, although this is typically reserved for more mature applications.

The overarching message is that effective prompt engineering is less about crafting a perfect prompt on the first try and more about engaging in a rigorous, iterative process to tailor prompts to specific application needs. This approach not only ensures that the LLM's outputs align more closely with the desired objectives but also enhances the model's utility across various applications.

## Summarizing

This chapter discusses the valuable application of large language models (LLMs) in summarizing vast amounts of text, a task increasingly relevant in today's information-rich environment. It emphasizes how summarization can make it feasible to digest more content than ever before, particularly for tasks like quickly understanding the gist of numerous articles or product reviews. This capability is highlighted as especially useful in software applications for managing and interpreting customer feedback efficiently.

Key insights from the text include:

- **Practical Application**: Summarization can transform lengthy product reviews into concise summaries, allowing for rapid assessment of customer sentiment and feedback across various departments such as shipping or pricing.
- **Customizable Summaries**: Summaries can be tailored to specific needs, such as focusing on aspects relevant to shipping times or pricing, providing targeted insights to relevant business departments.
- **Workflow Integration**: Demonstrated through a coding example, the text outlines how to implement summarization for multiple reviews. This process involves generating short summaries of each review, which can then be compiled into a dashboard for easy navigation and analysis.
- **Efficiency and Insight**: By summarizing text, businesses can quickly gain insights into customer opinions without the need for exhaustive manual review, enhancing decision-making and responsiveness to customer needs.

The main message is that LLMs offer a powerful tool for condensing and interpreting large volumes of text, enabling users to quickly grasp essential information and apply it in various contexts, such as improving product offerings or customer service strategies.

## Inferring

This chpter discusses the capabilities of large language models (LLMs) for inferring information from text, highlighting their versatility in applications like sentiment analysis, emotion detection, and information extraction without the need for traditional machine learning workflows. The author demonstrates through code examples how LLMs can quickly analyze text to classify sentiment, identify emotions, determine if a review expresses anger, and extract specific details like product names and brands—all with a simple prompt.

Key points include:

- **Versatility of LLMs**: A single LLM can perform various tasks, from sentiment analysis to extracting names and labels, simplifying the process compared to training multiple traditional models.
- **Rapid Application Development**: LLMs enable fast development of applications capable of analyzing text, as they can generate results immediately based on prompts without the need for a lengthy model training and deployment process.
- **Customizable Outputs**: LLMs can generate outputs tailored to specific needs, such as providing concise responses for easier post-processing or extracting detailed information formatted as JSON for further analysis.
- **Advanced Inferences**: Beyond basic sentiment analysis, LLMs can infer a range of emotions, assess customer sentiment towards specific aspects like pricing or shipping, and even identify topics within text, supporting applications like customer feedback analysis and content categorization.

The chapter emphasizes the efficiency and flexibility of using LLMs for NLP tasks, showcasing how they can transform application development by enabling quick, nuanced analysis of text for a variety of purposes. This approach not only streamlines the process but also opens up new possibilities for extracting valuable insights from text data.

## Transforming

The chapter discusses the versatility of large language models (LLMs) in transforming text across a wide range of applications, including language translation, tone modification, format conversion, and grammar and spelling corrections. It illustrates how LLMs, such as ChatGPT, can handle complex text transformation tasks efficiently, which traditionally required extensive manual coding or separate models for each task.

Key points include:

- **Language Translation**: LLMs can translate text into multiple languages with proficiency, enabling the creation of universal translators for global communication.
- **Tone Transformation**: They can adapt the tone of the text to suit different audiences or purposes, from casual slang to formal business language.
- **Format Conversion**: LLMs excel at converting text between various formats, such as JSON to HTML, making it easier to manipulate data across different platforms.
- **Grammar and Spelling Corrections**: They are highly effective in identifying and correcting grammar and spelling errors, improving the quality of written content.

The chapter emphasizes the efficiency and ease with which LLMs can be employed for tasks that previously required significant manual effort or specialized software, highlighting the potential for rapid application development and content enhancement across languages and formats.

## Expanding

This chapter discusses the concept of "Expanding" in the context of using large language models (LLMs) to generate more extensive text from concise inputs, such as detailed emails or essays from brief instructions or topic lists. This capability is highlighted for its positive applications like brainstorming assistance, while also cautioning against misuse, such as generating spam. It also stresses the importance of responsible usage that benefits users and maintains transparency about AI-generated content.

A walkthrough is provided on using LLMs to craft personalized email responses based on customer reviews, incorporating sentiment analysis to tailor replies. This involves a detailed explanation of using the "temperature" parameter to control the model's creativity and predictability. A lower temperature setting results in more predictable, consistent outputs, ideal for reliable application responses. In contrast, a higher temperature allows for more varied and creative outputs, useful for brainstorming or generating diverse content.

Through examples, the text demonstrates how to:

- Generate custom email replies to customer reviews, adjusting the tone based on the review's sentiment.
- Utilize the "temperature" parameter to influence the variety and creativity of the model's responses, with practical demonstrations of different temperature settings yielding varied email replies.

The chapter concludes with recommendations for using different temperature settings based on the desired application reliability or creativity, encouraging experimentation with this feature to understand its impact on output diversity.

## The Chat Format

This chapter introduces the concept of creating a custom chatbot using large language models (LLMs) like ChatGPT, with relatively minimal effort. It explains how LLMs can facilitate multi-turn conversations, simulating various roles such as AI customer service agents or order takers for restaurants. It outlines the steps to build such a chatbot, emphasizing the use of the OpenAI chat completions format for managing conversational flows.

Key components discussed include:

- **Setup**: Establishing the OpenAI Python package and defining helper functions for interacting with the model.
- **Message Structure**: Utilizing a series of messages, including system messages for setting the chatbot's behavior and user and assistant messages for the conversation.
- **System Messages**: These act as instructions to the chatbot, guiding its responses without being visible to the end user, akin to whispering instructions in the assistant's ear.
- **Creating Conversations**: Demonstrating how to construct a conversation with the chatbot, including setting the tone and behavior (e.g., speaking like Shakespeare or being a friendly chatbot).
- **Temperature Parameter**: Exploring how adjusting the temperature affects the variety and predictability of the chatbot's responses, with lower temperatures recommended for predictable outputs and higher temperatures for more creative responses.
- **Building "OrderBot"**: A step-by-step guide to developing a chatbot for taking pizza orders, including greeting customers, collecting orders, and summarizing them for processing.

The chapter concludes with a practical demonstration of using the chatbot to interactively take a pizza order, showing how to incorporate menu details and order preferences into the conversation. It also illustrates how to generate a JSON summary of the order, suitable for submission to an order processing system, highlighting the flexibility and potential of LLMs in creating tailored chatbot interactions.
