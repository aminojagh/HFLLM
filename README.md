# HFLLM

Practice repository for learning and experimenting with the
[Hugging Face Large Language Models Course](https://huggingface.co/learn/llm-course/).

This repo contains my implementations, notes, and adaptations of the official
course material. It is intended as a hands-on workspace for studying the Hugging
Face ecosystem, including Transformers, Datasets, Tokenizers, Accelerate, the
Hub, and common LLM/NLP training workflows.

All credit for the original course material belongs to Hugging Face.

## Status

The course implementation in this repository is still in progress. The current
work is implemented through the end of Chapter 7, and the repository will be
updated as the course work continues.

## Repository Structure

All working code is organized under [`notebooks/`](notebooks/):

| Area | Path | Course Coverage |
| --- | --- | --- |
| Datasets deep dive | [`notebooks/datasets_deepdive.ipynb`](notebooks/datasets_deepdive.ipynb) | Chapter 5: working with the Hugging Face Datasets library, dataset transforms, streaming, dataset creation, and FAISS-based semantic search |
| Tokenizers deep dive | [`notebooks/tokenization_deepdive/`](notebooks/tokenization_deepdive/) | Chapter 6: tokenizer training, fast tokenizers, normalization, pre-tokenization, BPE, WordPiece, Unigram, and building tokenizers from lower-level blocks |
| Inference | [`notebooks/inference-examples/`](notebooks/inference-examples/) | Pipeline and non-pipeline inference examples, plus deployment-oriented examples using vLLM and llama.cpp |
| Supervised fine-tuning and pretraining | [`notebooks/fine-tune-examples/`](notebooks/fine-tune-examples/) | Chapter 7 task implementations, including causal language modeling, masked language modeling, question answering, text classification, token classification, summarization, translation, ASR, and image classification |

The fine-tuning/pretraining section contains most of the code. From an
implementation perspective, it explores both high-level Hugging Face `Trainer`
APIs and lower-level distributed training pipelines built with Accelerate and
PyTorch.

## Environment Management

This repository supports two execution modes.

### 1. Local Development with uv

Use this mode when running notebooks or scripts on a local machine. Python and
package dependencies are managed with [`uv`](https://docs.astral.sh/uv/), using
[`pyproject.toml`](pyproject.toml) and [`uv.lock`](uv.lock).

```bash
uv sync
uv run jupyter lab
```

To run a notebook with this environment, select the project virtual environment
created by `uv`, or register a kernel:

```bash
uv run python -m ipykernel install --user --name hfllm --display-name "HFLLM"
```

For Hub uploads or gated model access, create a local `.env` file with:

```bash
HF_TOKEN=your_huggingface_token
```

Some notebooks are GPU-oriented. Packages such as `vllm`, `bitsandbytes`, and
`torchvision` may require compatible CUDA drivers or hardware. Audio notebooks
using `torchcodec` also require a system FFmpeg installation.

### 2. Kaggle Notebooks

Use this mode when running the notebooks directly in Kaggle. In that case, ignore
the local `uv` setup and run the notebooks with the latest Kaggle environment.
When a notebook needs an additional package that is not available in Kaggle by
default, the notebook installs it inside its own cells.

Kaggle-specific notebooks may use Kaggle secrets, GPU accelerators, or other
Kaggle runtime features. Those cells may need small local adaptations if they are
run outside Kaggle.

## Course References

- [Hugging Face LLM Course](https://huggingface.co/learn/llm-course/)
- [Chapter 5: The Datasets library](https://huggingface.co/learn/llm-course/chapter5/1)
- [Chapter 6: The Tokenizers library](https://huggingface.co/learn/llm-course/chapter6/1)
- [Chapter 7: Classical NLP tasks](https://huggingface.co/learn/llm-course/chapter7/1)
