This project demonstrates an AI workflow that transforms standard recipe text into beginner-friendly cooking instructions using a structured format.

The system uses a LangGraph agent workflow with multiple steps:

- Analyze the recipe text

- Generate cooking instructions

- Critique the instructions

- Repair the instructions if needed

The goal is to produce clear step-by-step instructions that are easier for beginners to follow.

Technologies Used:

- Python

- LangGraph

- LangChain

- Groq LLM API

- Pydantic (structured outputs)

- TheMealDB API (recipe data source)

Workflow Architecture:

The workflow is implemented using LangGraph.

Recipe API
    ↓
analyze_food
    ↓
generate_itinerary
    ↓
critique_itinerary
    ↓
repair_itinerary
    ↓
Structured recipe steps

Node Descriptions:

analyze_food

Extracts:

recipe name

ingredients

main cooking actions

generate_itinerary

Generates beginner-friendly step-by-step instructions.

critique_itinerary

Evaluates the generated instructions for:

clarity

missing steps

incorrect information

repair_itinerary

Improves the instructions based on critique feedback and returns structured JSON steps.

Example Output

Example structured output:

{
  "title": "Tamiya",
  "steps": [
    "Soak the beans",
    "Drain the beans",
    "Grind the beans",
    "Add the scallions and spices",
    "Shape the bean mixture",
    "Fry the patties",
    "Serve the patties"
  ]
}
Evaluation

The workflow was tested using 10 recipes retrieved from the MealDB API.

Results:

Successful runs: 10 / 10

The critique and repair nodes helped improve consistency and reduce incorrect details.

Running the Project

Install dependencies

pip install langchain langgraph groq pydantic requests

Add a Groq API key

os.environ["GROQ_API_KEY"] = "your_key_here"

Run the notebook

The notebook will:

fetch recipes from the MealDB API

process them through the workflow

output structured recipe steps