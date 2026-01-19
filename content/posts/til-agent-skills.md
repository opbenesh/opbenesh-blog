---
title: "agent skills for fun and profit"
date: 2026-01-11T02:16:16+02:00
draft: true
tags: ["anthropic","agents","skills","vibe"]
author: "Ben Esh"
ShowPostNavLinks: true
---
 Learnings: Building a No-Code LLM Agent

This document summarizes the key technical and strategic learnings from building the Product Agent using Cursor's Agent Skills framework.

## 1. The No-Code Agent Philosophy

The core realization of this project was that **most infrastructure for an agentic workflow is already provided by Cursor**. 

- **Custom Framework vs. Native Skills**: We initially started with a TypeScript framework but quickly pivoted to **Agent Skills**. 
- **Instruction as Code**: In a no-code agent, the "logic" is shifted from imperative code to declarative instructions in `SKILL.md` files.
- **Workflow Orchestration**: Cursor's agent is already proficient at selecting tools, managing state, and calling APIs. Our job is to provide the **guardrails, domain knowledge, and formatting templates**.

## 2. Tokenomics & Optimization

Token usage is the primary constraint and cost driver. We optimized this through several strategies:

### Progressive Discovery (Two-Tier Lookup)
- **The Problem**: Reading a 325 KB CSV (`detectors.csv`) on every turn wastes thousands of tokens.
- **The Solution**: Created a lightweight **`detectors-index.md`** (~24 KB) that lists only keys and services. 
- **The Workflow**: The agent scans the index first. If a match is found, it uses `grep` to pull the specific row from the CSV.

### Strategic `.cursorignore`
- Large data files that are only needed for specific `grep` operations should be added to `.cursorignore`. 
- This prevents the agent from "seeing" and accidentally reading the entire file into context during a general repo scan.

### Concise Skill Definitions
- **Short Descriptions**: Kept the YAML `description` field to exactly one sentence to reduce noise during skill discovery.
- **Atomic Instructions**: Focused each `SKILL.md` on a specific stage of the workflow (e.g., separating *Research* from *Formatting*).

## 3. Agent Skills Strategy

### The 4-Stage Pipeline
Breaking the complex "create a ticket" task into four distinct stages improved reliability and formatting precision:
1. **Discovery**: Brainstorming and duplicate checking.
2. **Research**: Technical verification of APIs and metrics.
3. **Formatting**: Applying strict visual styles and templates.
4. **Integration**: Executing external actions via MCP.

### User Interaction Model
- **Interactive Prompts**: Instead of one long execution, we built a workflow that prompts the user after each stage. This prevents "runaway" token spend and ensures the agent stays aligned with the PM's intent.

## 4. MCP as the "Action" Layer

- **Standardization**: MCP (Model Context Protocol) allowed us to integrate complex services like Asana and AWS/Azure documentation without writing a single line of integration code.
- **Tool Discovery**: Cursor automatically discovers tools provided by MCP servers, making them instantly available to all skills.

## 5. Storage vs. Ignore Summary

| Content Type | Storage Strategy | Reason |
| :--- | :--- | :--- |
| **Domain Data** | `.cursorignore` + `grep` | Too large for context; only need specific chunks. |
| **Indexes** | Markdown files | Fast, human-readable, and token-efficient for scanning. |
| **Templates** | Separate `.md` files | Centralized "source of truth" for formatting skills. |
| **Instructions** | `SKILL.md` | Provides the "intelligence" and logic for the agent. |
| **Lints/Tests** | Bash scripts | Quick sanity checks that don't require LLM reasoning. |
