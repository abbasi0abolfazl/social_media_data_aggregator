# Social Media Data Aggregator (Demo)

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Code style](https://img.shields.io/badge/code%20style-black-black.svg)](https://github.com/psf/black)

A modular, scalable demonstration system for collecting and analyzing social media data across multiple platforms (X, Facebook, Instagram) using intelligent scheduling and async processing.

## Purpose

This repository demonstrates my architectural approach to building production-ready data collection systems. It is **not** a production scraper but showcases:

- **Modular Design** - Platform-specific adapters with a common interface
- **Async Processing** - High-performance concurrent data collection
- **Intelligent Scheduling** - Rate limiting, retry logic, and queue management
- **Resilience Patterns** - Exponential backoff, circuit breakers, error handling

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Job Scheduler                           │
│  (Redis Queue + Cron-like scheduling)                       │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    Base Scraper (ABC)                       │
│  - fetch() / parse() abstract methods                       │
│  - Rate limiter integration                                 │
│  - Retry & backoff logic                                    │
└─────────────────────────────────────────────────────────────┘
          │              │              │
          ▼              ▼              ▼
    ┌────────────┐  ┌───────────┐  ┌───────────┐
    │ Twitter(X) │  │  Facebook │  │ Instagram │
    │ Scraper    │  │  Scraper  │  │  Scraper  │
    └────────────┘  └───────────┘  └───────────┘
```

## Note

This is a **demonstration** project showcasing architecture patterns. For production use, you would need to:
- Add proper authentication handling
- Implement more sophisticated anti-detection measures
- Add data persistence with proper schemas
- Include monitoring and alerting
