# genai-in-python-tutorial — GenAI in Python

Public student repo of the Skillmea course "Generatívna AI v Pythone" (registry slug
`genai-in-python`, mapping key `genai-in-python`). The whole repo syncs to the Courses drive
folder `3. GenAI in Python (SYNCED)/course_materials (shared)` via `drive-push` (root files:
the intro deck, the setup docx, `requirements.txt`; one module folder per notebook). Students
open it from Colab badges or clone it; nothing here may be behind-the-scenes material.

## Layout

- `1_…` to `10_…` and `9b_decision_models/`: one notebook per module, simplest to toughest
  (Python essentials, seven small apps, conversations/caching/batch, prompt engineering,
  structured outputs, RAG, fine-tuning, built-in tools, function calling, decision models,
  Hugging Face). Module folders carry their `data/` and `images/`; diagrams are drawn by
  matplotlib cells inside the notebooks (RAG flow, function-calling flow, three primitives).
- `0_genAI_in_Python.pptx` + `0_Setting up environment and first request to API.docx`: intro
  deck and setup guide. Robert edits the deck on Drive; pull before pushing.
- `requirements.txt`: one file for the whole course, exact pin for the SDK only.
- Filming notes, update plans and Skillmea descriptions live in
  `training-ops/filming/genai-in-python/`, never here.

## Conventions that hold the course together

- **Default model `gpt-5.6-luna`** everywhere (successor of `gpt-5-nano`, which retires
  2026-12-11). Luna rejects `temperature`; the prompt-engineering notebook demonstrates it on
  `gpt-4.1-mini` on purpose. Prices in prose as "0.20 USD", never "$0.20" (two dollar signs in a
  paragraph render as LaTeX on GitHub and Colab).
- **SDK pin in two places**: `openai==3.35.1` in `requirements.txt` AND in the first install
  cell of the eight notebooks that call the API. Bump both together, then re-execute.
- **Notebooks are committed executed, with outputs, plus an "Open in Colab" badge** (hub
  convention). Module 10 (Hugging Face) is GPU-only: blank outputs + a "run in Colab with a
  T4" note. Never commit a blanked notebook over executed ones; the drive-push skill knows
  which repos keep outputs.
- `9_function_calling` keeps `get_current_weather(location, format)` because ADK-tutorial
  notebook 01 rebuilds it. `9b_decision_models` uses the OpenAI Decisions API
  (`client.decisions.create`, SDK ≥ 3.26, `gpt-6-luna` only); its prose must survive re-runs
  (warm-up + two rounds).
- Classroom voice rules: `ADK-tutorial/CLAUDE.md` (notebook style recipe, banned vocabulary).

## Refresh outputs

```
set -a; . ~/.config/training-ops/openai.env; set +a
.venv/bin/jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=1800 <module>/<module>.ipynb
```

`.venv` is Python 3.12 with `requirements.txt` installed. After executing: coalesce streamed
outputs if a streaming demo renders one word per line, dump the notebook to markdown and read
every output against its prose, grep the .ipynb for local paths (`scratchpad`, `/private/tmp`,
`.venv`) and for the key. Then `drive-push --status`, dry-run, `--apply` after Robert confirms,
and list the Drive folder.

## Renaming or reordering modules

Rename Drive folders server-side (`rclone moveto`) so student links keep their IDs, then update
`mapping.json`, the README table and the Skillmea overview tab (real xlsx on the Management
drive: export, edit with openpyxl, back up, `rclone copyto`; never the Sheets API).
