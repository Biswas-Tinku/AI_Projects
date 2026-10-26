This objective of this project is to build a complete restaurant ​recommendation platform.

I have transform restaurant descriptions, customer reviews, and food images into structured ​knowledge and use coordinated AI agents to deliver personalized recommendations.
 ​
​I will integrate multiple capabilities including ​structured data generation, multimodal retrieval, multi-agent collaboration, and tool integration ​into a complete end-to-end solution. I am using large language models (OpenAI accessed through locally hosted LLM ollama), LLMs, and multimodal LLMs to process restaurant information, ​customer reviews, and food images into structured JSON formats.

I have design prompt-based workflows, validate outputs, and build a command-line interface ​to manage and safely update a structured restaurant knowledge base.

I also have constructed multimodal vector databases, generate text and image embeddings, ​and implement similarity-based retrieval with metadata filtering.​I am also applying weighted late-fusion ranking techniques to improve cross-modal search performance.

Designed a multi-agent recommendation system by defining specialized agent roles, ​goals, and tasks. ​These agents will work together to generate personalized restaurant recommendations. The systed is expose an interactive Gradio chatbot interface for user accessibility.
 
Finally I have integrate agents, retrieval systems, and tools using Model Context Protocol ​MCP. ​This includes configuring MCP servers, clients, and an LLM-based host, validating end-to-end ​tool execution, and ensuring secure, structured interactions. 

Work flow structure

**Structure Text and Multimodal Data with LLMs**
AI capabilities are leveraged to implement data engineering techiques aiming to understand the why behind user preferences, capturing the vibe of a restaurant, dietary considerations, and standout “hero dishes” hidden inside unstructured, multimodal data. The aim is to create and validate structured JSON data hidden inside unstructured, multimodal data.

*Input data*
```txt
**The Gilded Artichoke** brings a **bohemian chic** energy to the hills of **Silver Lake**, operating as an **upscale bistro** that prioritizes **Farm-to-Table Californian** ingredients. The space feels like a high-end greenhouse with its reclaimed wood and floor-to-ceiling windows, perfectly complementing the **4.5/5** rating earned by its lavender-rubbed roasted chicken and delicate heirloom tomato tarts.  Price range: $$$$
```
*Output data*
```JSON
 {
"name": "The Gilded Artichoke",
"location": "Silver Lake",
"type": "upscale bistro",
"food_style": "Farm-to-Table Californian",
"rating": 4.5,
"price_range": 3,
"signatures": [
  "lavender-rubbed roasted chicken",
  "delicate heirloom tomato tarts"
],
"vibe": "bohemian chic",
"environment": "a high-end greenhouse with reclaimed wood and floor-to-ceiling windows",
"shortcomings": []
}
```

**Process Multimodal Data with LLMs**
The structured text allowed the app to reason over textual attributes such as cuisine type, pricing, and signature dishes in a consistent, machine-readable format.  
However, the app’s data is not limited to text. It also includes food recipes and user visit histories that reference images, capturing visual information that text alone cannot fully describe, such as presentation style, ingredients, and portion details.   
To unlock this information and integrate it with the original databases, I have use multimodal GenAI capabilities to convert images into descriptive text and enrich the structured knowledge.
