---
layout: post
title: "What it actually takes to deploy Agentic AI in the enterprise"
date: 2026-05-23
description: Lessons from building production Agentic AI systems at scale — what works, what fails, and what nobody tells you.
tags: [agentic-ai, production, enterprise, langgraph]
categories: ai-ml
---

Most Agentic AI demos look impressive. A tool-calling LLM routes between a few functions, answers questions about your data, and the audience nods approvingly. Then someone asks: "Can we put this in production?"

That's where the real work begins.

Over the past two years, I've led production deployments of Agentic AI systems serving tens of thousands of users — a unified chatbot for 80,000+ field technicians at Charter Communications, a discharge automation system for a major healthcare payer, and property valuation workflows at Fannie Mae. Here's what I've learned.

## 1. Orchestration is an architecture decision, not a library choice

Teams reach for LangChain or LangGraph (or AutoGen, or CrewAI) and assume the framework solves orchestration. It doesn't. The framework gives you primitives — nodes, edges, state. You still have to design the graph.

For Charter, we needed role-aware routing: a field tech in the Southeast asking about fiber splicing gets a different path than a NOC engineer asking about outage escalation. That's not a prompt engineering problem. That's a state machine with domain-specific branching logic.

**What works:** Design the orchestration graph on a whiteboard first. Only then pick the framework that can express it.

## 2. Retrieval quality is the ceiling

Your agent is only as good as what it retrieves. We embedded 1,000+ Confluence pages and 5,000+ technical attachments into PGVector — and spent more time on chunking strategy, metadata tagging, and hybrid search than on anything LLM-related.

Naive chunking (split every 500 tokens) consistently underperformed. Domain-aware chunking — respecting document structure, keeping procedure steps intact, tagging by product line — made a measurable difference in answer quality.

**What works:** Treat retrieval as a first-class engineering problem. Evaluate it independently from generation. Your RAG pipeline is a search engine that happens to feed an LLM.

## 3. Human-in-the-loop is not a failure mode

For CareSource's discharge automation, we built HITL (Human-in-the-Loop) into the design from day one — not as a fallback, but as a feature. Certain document types, certain confidence thresholds, certain patient flags → route to a human reviewer.

This was the right call. Healthcare has edge cases that no LLM handles gracefully. Designing for graceful handoff to humans made the system more trustworthy and actually faster to get approved by compliance.

**What works:** Identify upfront which decisions should never be fully automated. Design the escalation path before you design the happy path.

## 4. Observability or it didn't happen

A production AI system that you can't observe is a liability. We instrumented every agent node — inputs, outputs, latency, token counts, tool call results, confidence scores. We built dashboards before we launched.

This paid off immediately. Within the first week, we caught a retrieval pattern that was consistently pulling stale documentation for one product line. Without tracing, we'd have been debugging user complaints with no signal.

**What works:** Treat LLM calls like external API calls. Trace them. Log them. Set up alerts on latency and error rates. Use tools like LangSmith, Arize, or roll your own with OpenTelemetry.

## 5. The hard part is change management, not technology

The Charter chatbot reduced support call volume by 60%. That's a real number with real savings. It also meant changing how 80,000 technicians get help on the job — their muscle memory, their workflows, their trust in a system.

We ran structured rollouts by region, collected feedback loops, and iterated on the UX based on actual usage patterns. The ML model was largely stable after the first month. The adoption curve took six.

**What works:** Measure adoption alongside accuracy. A technically correct system that nobody uses is a failed system.

---

Building Agentic AI for the enterprise is a systems problem wrapped in an AI problem. The LLM is maybe 20% of the work. The rest is software engineering, data engineering, UX, and change management — applied to a stochastic component that requires more careful testing than anything deterministic you've built before.

If you're working through similar challenges, I'd be glad to connect — reach out on [LinkedIn](https://www.linkedin.com/in/dipjyotidas/).
