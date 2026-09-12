# GenAI in Python Tutorial

A companion tutorial repo for learning Generative AI development in Python, built around the OpenAI API: API keys, no frameworks, the model as the backend of your own apps, plus the handful of advanced concepts you need to make those apps real. Every notebook starts with an "Open in Colab" badge and (except the Hugging Face module) is committed with real, executed outputs, so it reads like an article before you run a single cell.

Default model in every notebook: `gpt-5.6-luna`, the small, cheap model of the current generation (about $0.20 per million input tokens, $1.20 per million output). Running a whole notebook costs cents.

## Modules

| # | Module | What it covers |
|---|--------|-----------------|
| 1 | [Absolute Python Essentials](1_absolute_python_essentials/1_absolute_python_essentials.ipynb) | Core Python: variables, strings, control flow, functions. No API key needed |
| 2 | [Seven Small Apps, One API Call](2_basic_project_examples/2_basic_project_examples.ipynb) | One notebook, seven sections: the one text call and its knobs (role, streaming), plant ID from a photo, recording to notes, messy text to JSON, a fairytale with voice and picture, plain-English questions to SQL, ticket notes to a knowledge-base article |
| 3 | [Retrieval-Augmented Generation (RAG)](3_retrieval_augmented_generation_RAG/3_retrieval_augmented_generation_RAG.ipynb) | Embed, store, search, generate, built by hand with pictures of each step; top-k; grounded answers |
| 4 | [Fine-Tuning](4_fine-tuning/4_fine-tuning.ipynb) | What LoRA changes inside a model (shown with numpy), behaviour vs knowledge, what it costs on OpenAI, hosted and on your own GPU, and why you will rarely need it. CPU only, no API key |
| 5 | [Function Calling](5_function_calling/5_function_calling.ipynb) | The two-sided flow, the loop that runs your functions and hands results back, `tool_choice` |
| 6 | [Basics of Prompt Engineering](6_basics_of_prompt_engineering/6_basics_of_prompt_engineering.ipynb) | Reasoning effort and verbosity, clear instructions with reasons, roles and structure, few-shot, reducing hallucination, chaining calls |
| 7 | [Hugging Face](7_hugging_face/7_hugging_face.ipynb) | Running open-source models locally with `transformers`. **Needs a GPU, Colab T4** |
| 8 | [Structured Outputs](8_structured_outputs/8_structured_outputs.ipynb) | Pydantic + `responses.parse`, what is sent under the hood, enums, optional fields, nested lists, refusals |
| 9 | [Built-in Tools](9_tools/9_tools.ipynb) | Web search, code interpreter, file search (hosted RAG), image generation, remote MCP, combining tools |
| 10 | [Conversations, Caching, Batch, Moderation](10_conversations_caching_batch/10_conversations_caching_batch.ipynb) | Keeping conversation state three ways, prompt caching, the Batch API and flex tier, the moderation endpoint |

## How to Run

### Option A: Google Colab (recommended)

Click the "Open in Colab" badge at the top of any notebook. In Colab, add your OpenAI key as a Colab secret named `OPENAI_API_KEY` (the key icon in the left sidebar), or paste it in when prompted. Notebooks that need data files fetch them from this repository automatically.

Module 7 (Hugging Face) needs a GPU runtime: in Colab go to **Runtime > Change runtime type > T4 GPU** before running it.

### Option B: Local Python

Requirements: Python 3.10 or newer. The single `requirements.txt` in the course root covers every module except Hugging Face (tested on Python 3.10 to 3.14, September 2026).

```bash
pip install -r requirements.txt
export OPENAI_API_KEY="sk-your-key-here"
jupyter notebook
```

Each notebook's setup cell looks for the key in this order: Colab secrets, the `OPENAI_API_KEY` environment variable, an interactive prompt. Setting the environment variable lets every notebook run headlessly.

Module 7 (Hugging Face) needs a GPU and installs `torch`/`transformers` itself in its first cell, so those packages are deliberately left out of `requirements.txt`; run it on Colab's free T4 GPU rather than locally.

## Notes

- All notebooks are committed with their outputs already executed, so you can read them like a finished tutorial and still re-run every cell yourself.
- Generated audio and image files are gitignored; notebooks embed small previews as outputs. Sample data lives next to each notebook (module 2 keeps it in `data/`).
- Model and API facts (prices, model names, deprecations) were verified against the OpenAI documentation in September 2026. They age; check [developers.openai.com/api/docs/pricing](https://developers.openai.com/api/docs/pricing) when in doubt.
- This is a companion tutorial repo maintained alongside Robert Barcik's other training material repos.
