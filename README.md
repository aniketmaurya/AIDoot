# Agents 🤖

Build Agentic workflows with function calling, powered by LangChain.

## Installation

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/aniketmaurya/python-project-template?template=false)

**Install latest branch:**

```shell
pip install git+https://github.com/aniketmaurya/agents.git@main
```

**or, for editable installation:**

```shell
  git clone https://github.com/aniketmaurya/agents.git
  cd agents
  pip install -e .
```

## Usage/Examples

LLM with access to weather API:

```python
from agents.llms.llm import LlamaCppChatCompletion
from agents.tools import get_current_weather, wikipedia_search

llm = LlamaCppChatCompletion.from_default_llm(n_ctx=0)
llm.bind_tools([get_current_weather, wikipedia_search])  # Add any tool from LangChain

messages = [
    {"role": "system", "content": "You are a helpful assistant that has access to tools and use that to help humans."},
    {"role": "user", "content": "What is the weather in London?"}
]
output = llm.chat_completion(messages)
tool_results = llm.run_tool(output)
print(tool_results)
```

<details>
    <summary>See output:</summary>

```shell
[{'tool_call_id': 'call_DnmopdelmY8Dl1NRXXx2gMDy',
  'role': 'tool',
  'name': 'get_current_weather',
  'content': [{'FeelsLikeC': '17',
    'FeelsLikeF': '62',
    'cloudcover': '50',
    'humidity': '50',
    'localObsDateTime': '2024-05-06 03:35 PM',
    'observation_time': '10:35 PM',
    'precipInches': '0.0',
    'precipMM': '0.0',
    'pressure': '1021',
    'pressureInches': '30',
    'temp_C': '17',
    'temp_F': '62',
    'uvIndex': '4',
    'visibility': '16',
    'visibilityMiles': '9',
    'weatherCode': '116',
    'weatherDesc': [{'value': 'Partly cloudy'}],
    'weatherIconUrl': [{'value': ''}],
    'winddir16Point': 'W',
    'winddirDegree': '270',
    'windspeedKmph': '28',
    'windspeedMiles': '17'}]}]
```

</details>




<!-- ## Demo

Insert gif or link to demo -->


<!-- ## FAQ

#### Question 1

Answer 1

#### Question 2

Answer 2 -->

## Acknowledgements

Built with PyCharm 🧡. Thanks to JetBrains for supporting this work by providing free credits.

<img src="https://resources.jetbrains.com/storage/products/company/brand/logos/PyCharm_icon.svg" alt="PyCharm logo.">
<img src="https://resources.jetbrains.com/storage/products/company/brand/logos/jetbrains.svg" alt="JetBrains logo.">
