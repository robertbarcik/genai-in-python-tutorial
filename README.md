# GenAI in Python Tutorial

A companion tutorial repo for learning Generative AI development in Python, built around the OpenAI API. Fifteen modules take you from Python basics through prompt engineering, RAG, function calling, fine-tuning, and beyond. Every notebook starts with an "Open in Colab" badge and (except the two GPU modules) is committed with real, executed outputs so it reads like an article even before you run a single cell.

## Modules

| # | Module | What it covers |
|---|--------|-----------------|
| 1 | [Absolute Python Essentials](1_absolute_python_essentials/1_absolute_python_essentials.ipynb) | Core Python: variables, strings, control flow, functions - no API key needed |
| 2 | [Basic Model Usage](2_basic_project_examples/2_basic_model_usage/2_basic_model_usage.ipynb) | First OpenAI API calls: moderation, text generation, summarization, TTS/transcription, image generation, vision |
| 3 | [Plant Identification](2_basic_project_examples/3_plant_identification/3_plant_identification.ipynb) | Multimodal AI: identifying plants from images and annotating results |
| 4 | [Extracting Knowledge from Videos](2_basic_project_examples/4_extracting_knowledge_from_videos/4_extracting_knowledge_from_videos.ipynb) | Video to audio, Whisper transcription, GPT cleanup of lecture notes |
| 5 | [Extracting Information from Unstructured Data](2_basic_project_examples/5_extracting_information_from_unstructured_data/5_extracting_information_from_unstructured_data.ipynb) | Turning free-form text (emails, tickets) into structured JSON |
| 6 | [Converting Text to Audio](2_basic_project_examples/6_converting_text_into_audio_fairytale_example/6_converting_text_to_audio_fairytale_example.ipynb) | OpenAI TTS: generating a fairytale as narrated audio |
| 7 | [Natural Language to SQL](2_basic_project_examples/7_natural_language_to_sql/7_natural_language_to_sql.ipynb) | Converting plain-English questions into executable SQL queries |
| 8 | [Content Creation](2_basic_project_examples/8_content_creation/8_content_creation.ipynb) | Generating knowledge base articles from raw support ticket notes |
| 9 | [Retrieval-Augmented Generation (RAG)](3_retrieval_augmented_generation_RAG/3_retrieval_augmented_generation_RAG.ipynb) | Embeddings, semantic search, and grounding answers in retrieved context |
| 10 | [Fine-Tuning](4_fine-tuning/4_fine-tuning.ipynb) | Modern fine-tuning approaches (SFT, DPO) and when to use them - **needs a GPU, Colab T4** |
| 11 | [Function Calling](5_function_calling/5_function_calling.ipynb) | Connecting LLMs to external functions and real-world actions |
| 12 | [Basics of Prompt Engineering](6_basics_of_prompt_engineering/6_basics_of_prompt_engineering.ipynb) | Temperature, sampling, and core prompting techniques |
| 13 | [Hugging Face](7_hugging_face/7_hugging_face.ipynb) | Transfer learning and running open-source models locally - **needs a GPU, Colab T4** |
| 14 | [Structured Outputs](8_structured_outputs/8_structured_outputs.ipynb) | Getting type-safe JSON responses from the Responses API |
| 15 | [Built-in Tools](9_tools/9_tools.ipynb) | Web search, MCP, file search / vector stores, and code interpreter |

## How to Run

### Option A: Google Colab (recommended)

Click the "Open In Colab" badge at the top of any notebook. In Colab, add your OpenAI key as a Colab secret named `OPENAI_API_KEY` (the key icon in the left sidebar), or paste it in when prompted.

Modules 10 (fine-tuning theory) and 13 (Hugging Face) need a GPU runtime: in Colab go to **Runtime > Change runtime type > T4 GPU** before running them.

### Option B: Local Python

Requirements: Python 3.10+.

```bash
pip install -r requirements.txt
export OPENAI_API_KEY="sk-your-key-here"
jupyter notebook
```

Each notebook's auth cell checks, in order: Colab secrets, then the `OPENAI_API_KEY` environment variable, then falls back to an interactive prompt. Setting the environment variable lets every notebook run headlessly.

Modules 10 and 7 (Hugging Face) install `torch`/`transformers` themselves and are best run on Colab's free T4 GPU rather than locally without a GPU.

## Notes

- All notebooks are committed with their outputs already executed, so you can read them like a finished tutorial and still re-run every cell yourself.
- Generated audio, video, and image files are gitignored to keep the repo light; small generated text, JSON, and CSV artifacts are committed alongside the notebooks that produce them.
- This is a companion tutorial repo maintained alongside Robert Barcik's other training material repos.
