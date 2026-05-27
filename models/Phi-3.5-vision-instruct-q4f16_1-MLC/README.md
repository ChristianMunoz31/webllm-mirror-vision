---
library_name: mlc-llm
base_model: microsoft/Phi-3.5-vision-instruct
tags:
- mlc-llm
- web-llm
---

# Phi-3.5-vision-instruct-q4f16_1-MLC

This is the [Phi-3.5-vision-instruct](https://huggingface.co/microsoft/Phi-3.5-vision-instruct) model in MLC format `q4f16_1`.
The model can be used for projects [MLC-LLM](https://github.com/mlc-ai/mlc-llm) and [WebLLM](https://github.com/mlc-ai/web-llm).

## Example Usage

Here are some examples of using this model in MLC LLM.
Before running the examples, please install MLC LLM by following the [installation documentation](https://llm.mlc.ai/docs/install/mlc_llm.html#install-mlc-packages).

### Chat

In command line, run
```bash
mlc_llm chat HF://mlc-ai/Phi-3.5-vision-instruct-q4f16_1-MLC
```

### REST Server

In command line, run
```bash
mlc_llm serve HF://mlc-ai/Phi-3.5-vision-instruct-q4f16_1-MLC
```

### Python API

```python
from mlc_llm import MLCEngine

# Create engine
model = "HF://mlc-ai/Phi-3.5-vision-instruct-q4f16_1-MLC"
engine = MLCEngine(model)

# Run chat completion in OpenAI API.
for response in engine.chat.completions.create(
    messages = [
        {
            "role": "user",
            "content": [
                {
                    "type": "image_url",
                    "image_url": "https://www.ilankelman.org/stopsigns/australia.jpg",
                },
                {
                    "type": "text",
                    "text": "Describe this image please."
                },
            ],
        },
    ],
    model=model,
    stream=True,
):
    for choice in response.choices:
        print(choice.delta.content, end="", flush=True)
print("\n")

engine.terminate()
```

## Documentation

For more information on MLC LLM project, please visit our [documentation](https://llm.mlc.ai/docs/) and [GitHub repo](http://github.com/mlc-ai/mlc-llm).
