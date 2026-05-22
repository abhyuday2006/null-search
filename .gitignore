<div align="center">

# NULL SEARCH
### A Privacy-First, High-Performance Search Engine Built in Modern C++

</div>

---

# Overview

A fully self-hosted search engine stack focused on:

- Extreme performance
- Privacy-first architecture
- Intelligent ranking
- Multilingual indexing
- Async crawling pipeline

Built almost entirely in **modern C++**, with a lightweight React frontend.

---

# 🏛️ Architecture

```txt
                ┌──────────────┐
                │   Frontend   │
                │ React + Vite │
                └──────┬───────┘
                       │
                       ▼
              ┌─────────────────┐
              │ Query/API Layer │
              │ Drogon + BM25   │
              └──────┬──────────┘
                     │
                     ▼
        ┌──────────────────────────┐
        │        Indexer           │
        │ Xapian + PageRank        │
        └──────────┬───────────────┘
                   │
                   ▼
        ┌──────────────────────────┐
        │         Crawler          │
        │ libcurl + c-ares         │
        └──────────┬───────────────┘
                   │
                   ▼
             ┌──────────┐
             │ RocksDB  │
             └──────────┘
```

---

# Features

## Distributed-Style Async Crawler

- Async HTTP batching using `libcurl multi`
- Async DNS resolution with `c-ares`
- Lock-free MPMC URL frontier
- robots.txt parsing + per-domain cache
- Token-bucket politeness system
- Simhash + Bloom filter deduplication
- HTML parsing with Gumbo
- Readability-style text extraction

---

## Intelligent Indexer

- Full-text indexing using Xapian
- Unicode-aware tokenization with ICU
- Automatic language detection via CLD3
- Link graph construction
- Sparse-matrix PageRank implementation
- Metadata-aware ranking signals

---

## Search & Ranking

- BM25 retrieval
- Custom reranking pipeline
- Signal-based ranking:
  - freshness
  - domain trust
  - content length
  - link authority
  - language matching

- Query parsing using Xapian native parser

---

## Privacy-First Design

- No analytics
- No telemetry
- No query persistence
- No external CDNs
- No Redis dependency
- User preferences stored locally only

---

# Tech Stack

## Crawler

| Component | Tech |
|---|---|
| HTTP Fetch | libcurl multi |
| HTML Parsing | Gumbo Parser |
| Text Extraction | Custom readability extraction |
| URL Frontier | Lock-free MPMC queue |
| Deduplication | Simhash + Bloom Filter |
| DNS | c-ares |
| Storage | RocksDB |

---

## Indexer

| Component | Tech |
|---|---|
| Search Index | Xapian |
| Tokenizer | ICU |
| Language Detection | CLD3 |
| Link Graph | RocksDB |
| Ranking | Custom PageRank |

---

## Query/API

| Component | Tech |
|---|---|
| HTTP Server | Drogon |
| Ranking | BM25 + Signal Reranking |
| Rate Limiting | In-process token bucket |
| Output | JSON API |

---

## Frontend

| Component | Tech |
|---|---|
| Framework | React 18 + Vite |
| Styling | TailwindCSS v4 |
| State | Zustand |
| Fonts | DM Serif + Syne + DM Mono |

---

## Infra

| Component | Tech |
|---|---|
| Reverse Proxy | Caddy |
| Monitoring | Prometheus + Grafana |
| Containers | Docker Compose |
| Build System | CMake + Ninja |

---

# System Design

## Crawling Pipeline

```txt
Seed URLs
    ↓
URL Frontier
    ↓
Async Fetcher
    ↓
HTML Parser
    ↓
Content Extractor
    ↓
Deduplication
    ↓
Storage Queue
    ↓
Indexer
```

---

## Ranking Pipeline

```txt
BM25 Score
    +
Freshness
    +
Domain Trust
    +
Link Authority
    +
Language Match
    +
Content Quality
    =
Final Ranking Score
```

---

# Storage Layout

| Storage | Purpose |
|---|---|
| RocksDB | Crawl queue |
| RocksDB | Link graph |
| Xapian | Search index |
| SQLite | Domain trust scores |
| Flat files | Raw page archive |

---

# Processes

```txt
crawler  ─────► RocksDB Queue ─────► indexer
                                      │
                                      ▼
                                   Xapian
                                      │
                                      ▼
                                   API Layer
                                      │
                                      ▼
                                   Frontend
```

---

# Build

## Requirements

- C++20
- CMake
- Ninja
- RocksDB
- Xapian
- ICU
- libcurl
- c-ares

---

## Clone

```bash
git clone https://github.com/abhyuday2006/nullsearch.git
cd nullsearch
```

---

## Build

```bash
cmake -B build -G Ninja
cmake --build build
```

---

## Run

```bash
docker compose up
```

---

# Performance Goals

| Metric | Goal |
|---|---|
| Crawl throughput | 10k+ pages/min |
| Query latency | <50ms |
| Index size | Efficient compressed storage |
| Memory footprint | Single-node deployable |
| Deployment | Self-hostable |

---

# Roadmap

- [ ] Incremental indexing
- [ ] Distributed crawling
- [ ] Vector search
- [ ] Hybrid semantic ranking
- [ ] WASM query sandbox
- [ ] Browser extension
- [ ] Snapshot caching
- [ ] Multi-region deployment

---

# Philosophy

This project is built around a few ideas:

- search should be fast
- privacy should be default
- infra should stay understandable
- software should be self-hostable
- modern C++ can still build incredible systems

---

# 🤝 Contributing

PRs, ideas, optimizations, and architecture discussions are welcome.

---

# 📜 License

MIT License

---

<div align="center">

### ©Abhyuday Bhatnagar
</div>