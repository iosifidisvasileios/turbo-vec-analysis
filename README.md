# Turbo-Vec Analysis for RAG Retrieval Compression

A small experiment comparing vector compression methods for RAG retrieval.

## Setup

- Dataset: `Madras1/rag-qa-fulltext-ptbr`
- Language: Portuguese
- Embedding model: `Octen/Octen-Embedding-0.6B`
- Vector count: ~1.4M
- Vector dimension: 1024
- Evaluation sample: 17K questions
- Metric: Hit Rate @ 5

## Methods Compared

- FAISS float32
- FAISS float16
- FAISS IVFPQ 8-bit
- Turbo-Vec 4-bit
- Turbo-Vec 3-bit
- Turbo-Vec 2-bit
- PCA 512 / 256 / 128 dimensions with float32
- PCA 512 / 256 / 128 dimensions with float16

## Key Result

Turbo-Vec 2-bit gave the best memory-to-retrieval-quality trade-off.

It substantially reduced vector storage while keeping Hit Rate @ 5 close to the full-vector baseline.

## Takeaway

For this setup, aggressive quantization was more effective than dimensionality reduction. FAISS float16 was the easiest low-risk optimization, while Turbo-Vec 2-bit was the most memory-efficient option.