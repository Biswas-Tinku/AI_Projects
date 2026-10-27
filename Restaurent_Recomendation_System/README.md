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
```Python
with open("Recipes.json", "r") as file:
    recipe_data = json.load(file)
print(recipe_data[0])
with Image.open("synthetic_recipe_images/recipe1.png") as img:
    img.show()
```
**Output**
```txt
 {'id': 1, 'name': 'Classic Margherita Pizza', 'cuisine': 'Italian', 'servings': 2, 'prep_time': '20 mins', 'cook_time': '15 mins', 'total_time': '35 mins', 'ingredients': ['1 pizza dough ball (about 260g)', '2 tablespoons tomato sauce', '1 cup shredded mozzarella cheese', '6-8 fresh basil leaves', '1 tablespoon olive oil', 'pinch of salt', 'optional: grated parmesan'], 'directions': ['Preheat oven to 250Â°C (482Â°F) with a baking stone if available.', 'Roll out dough to a 12-inch circle on a floured surface.', 'Spread tomato sauce evenly over dough, leaving a 1/2-inch border.', 'Scatter mozzarella cheese over sauce.', 'Bake on the stone for 10-12 minutes until crust is crisp and cheese melts.', 'Finish with basil leaves, drizzle with olive oil, and season with salt and optional parmesan.', 'Slice and serve immediately.']}
```
![Recipe1]("/synthetic_recipe_images/recipe1.png")

**JSON output**
```JSON
{
        "id": 2,
        "name": "Chicken Tikka Masala",
        "cuisine": "Indian",
        "servings": 4,
        "prep_time": "25 mins",
        "cook_time": "40 mins",
        "total_time": "1 hour 5 mins",
        "ingredients": [
            "500g boneless chicken thighs, cubed",
            "1 cup yogurt",
            "2 tablespoons lemon juice",
            "2 teaspoons garam masala",
            "1 teaspoon ground cumin",
            "1 teaspoon ground coriander",
            "1 onion, minced",
            "2 cloves garlic, minced",
            "1 tablespoon grated ginger",
            "1 can (400g) crushed tomatoes",
            "1 cup heavy cream or coconut cream",
            "2 tablespoons oil",
            "Salt to taste",
            "Fresh cilantro for garnish"
        ],
        "directions": [
            "Marinate chicken in yogurt, lemon juice, garam masala, cumin, coriander, and a pinch of salt for at least 30 minutes.",
            "In a large pan, heat oil and saut\u00c3\u00a9 onion until translucent.",
            "Add garlic and ginger; cook 1 minute until fragrant.",
            "Add marinated chicken; cook until browned on all sides.",
            "Stir in crushed tomatoes and simmer 15 minutes.",
            "Reduce heat and add cream; simmer 5-10 minutes until sauce thickens.",
            "Garnish with cilantro and serve with rice or naan."
        ],
        "image_description": "Here is the caption:\n\nChicken Tikka Masala: Marinated Chicken Breast in a Rich Tomato-Cream Sauce.\n\nMain Dish: Chicken Breast\n\nKey Ingredients & Visual Textures:\n- Grilled and slightly charred chicken breast, served rare\n- Blistered onions and bell peppers in a slightly caramelized state\n- Rich, creamy tomato-hollandaise sauce with a subtle sheen\n- Fresh cilantro leaves scattered on top\n\nPresentation: Served on a creamy white ceramic plate, garnished with additional cilantro sprigs and a few slices of cucumber, arranged around the plate edge."
    },
    ```