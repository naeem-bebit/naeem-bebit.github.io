---
title: "Graph RAG: Adding Structure to Retrieval"
date: 2026-10-05
summary: "How knowledge graphs improve retrieval-augmented generation"
description: "How knowledge graphs improve retrieval-augmented generation"
tags:
  - LLM
  - RAG
  - Knowledge Graph
ShowToc: true
TocOpen: true
---

A quick note on Graph RAG and when it beats plain vector search.

## The problem with plain RAG

Standard RAG embeds document chunks into vectors and retrieves the chunks most similar to a question. It works well when the answer lives inside one or two chunks. It fails on **multi-hop questions** — questions where the answer is spread across several documents and requires following relationships. Example: *"Which suppliers ship parts that failed quality checks in plants served by our Hamburg warehouse?"* No single chunk answers that.

## What Graph RAG adds

Graph RAG builds a **knowledge graph** over the corpus: entities (suppliers, parts, warehouses) become nodes, relationships (ships-to, supplies, failed) become edges. Retrieval then combines:

1. **Graph traversal** — walk the relationships to collect connected facts
2. **Vector search** — retrieve semantically similar chunks as usual

The LLM answers from both the raw text and the structured neighborhood around the relevant entities.

## Typical pipeline

- **Indexing:** an LLM extracts entities and relationships from each document → graph store (e.g. Neo4j, Kùzu, or an in-memory NetworkX graph for experiments)
- **Query time:** extract entities from the question → find them in the graph → expand a neighborhood (1–2 hops) → feed subgraph + retrieved chunks into the prompt

## When it's worth it

- Yes: questions that join facts across documents, "how are A and B related" queries, global summaries (*"what themes run through all these reports?"* — this is what Microsoft's GraphRAG is optimized for)
- No: simple lookups, small corpora, when a plain vector index already answers well — graph extraction adds indexing cost and a second system to maintain

## Rule of thumb

Start with vector RAG. Add the graph layer when eval questions show answers requiring chained relationships the retriever keeps missing.
