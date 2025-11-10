# littlepantry
Agentic Recipe Generator OpenAI x Tavily Search

Structured output using libraries like Pydantic are helpful in creating reliable api responses for data driven applications.
 
Demo project.

[Langchain stuctured output example documentation](https://docs.langchain.com/oss/python/langchain/structured-output)
```python
from langchain.agents import create_agent
from langchain_tavily import TavilySearch
from pydantic import BaseModel, Field
```

```python
class RecipeInfo(BaseModel):
    ingredients: List[str] = Field(description="List of ingredients")
    steps: str = Field(description="Step by step instructions to complete the recipe.")
    name: str = Field(description="Title of the recipe")

tool = TavilySearch(max_results=1, topic="general")

agent = create_agent(
    model="openai:gpt-4o",
    tools=[tool],
    system_prompt="Given the ingredients use your 'tool' to search the web for recipes.",
    response_format=RecipeInfo
)
```


## Selection screen
![til](https://github.com/SolidUmbrella/littlepantry/blob/main/little_pantry-ezgif.com-video-to-gif-converter.gif)

## The Final Result
![til](https://github.com/SolidUmbrella/littlepantry/blob/main/little_pantry_snip.png)
