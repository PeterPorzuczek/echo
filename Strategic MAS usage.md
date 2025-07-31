---
title: "MAS Driven Features"
date: 2025‑07‑31
description: "A concise tour of how Multi‑Agent Systems supercharge Feature‑Driven Development."
tags: [agile, FDD, MAS, software‑engineering, process‑improvement]
---

## Strategic MAS usage - Feature definition with Multi Agentic Systems

Feature‑Driven Development (FDD) thrives on fast, feature‑centric iterations, yet it still leans on human orchestration for coordination, prioritisation and feedback cycling.  
The paper **“Multi‑Agent System Adaptation for Feature‑Driven Development Methodology”** proposes a pragmatic upgrade: embed a swarm of autonomous software agents straight into every FDD stage. The result is a pipeline that **decides, designs, builds and verifies features with far less manual friction**. :contentReference[oaicite:6]{index=6}

## Why agents fit FDD so well

* **Intrinsic modularity** – each feature already stands alone, so delegating it to a self‑contained agent matches the grain of the process.  
* **Distributed intelligence** – agents plan, sense and act concurrently, eliminating the central bottleneck that slows traditional FDD teams on large or geo‑spread projects.  
* **Continuous adaptability** – autonomy plus shared blackboards lets agents rejig priorities on the fly when requirements drift.  

The authors stress that MAS extend FDD without rewriting its DNA; they simply inhabit the five canonical activities:

| Classic FDD activity | Agent augmentation |
| --- | --- |
| Develop overall model | *Requirement Gathering Agent* refines domain concept maps collaboratively. |
| Build features list | The same agent distils user stories into a ranked backlog. |
| Plan by feature | *Design Agent* and *Development Agent* negotiate ownership and sequencing through a shared **Features Blackboard**. |
| Design by feature | *Design Agent* drafts class diagrams and hands them to developers already validated against constraints. |
| Build by feature | *Development* and *Testing Agents* run code synthesis, unit checks and integration suites in short loops, then log outcomes for stakeholders.  |

## The agent roster

| Role | Core responsibility |
| --- | --- |
| Requirement Gathering | Capture, de‑duplicate and prioritise user stories while updating the backlog in real time. |
| Design | Generate detailed design artefacts aligned with the evolving overall model. |
| Development | Implement and commit feature code, reacting to dependency signals from the blackboard. |
| Testing | Trigger automated test batteries for every new build and publish quality metrics. |
| Feedback | Aggregate stakeholder comments and performance data, closing the loop into the next sprint. |

## Blackboards: the agents’ meeting rooms

* **User Interface Blackboard** – exposes every agent action to the team so progress stays transparent.  
* **Features Blackboard** – synchronises backlog changes, design notes and dependency data.  
* **Development Blackboard** – coordinates sprint cadence and code hand‑offs inside the dev–test micro‑loop. :contentReference[oaicite:7]{index=7}  

*Figure 2 on page 5 of the paper sketches the full topology: agents orbit these boards, dropping messages, picking up tasks and never blocking one another.*

## What changes in practice

1. **Planning latency drops** because agents pre‑screen requirements and feed a continuously sorted feature list to designers.  
2. **Code quality rises** thanks to immediate, agent‑driven testing after every commit.  
3. **Scalability improves** since workload simply equals number of active agents, not size of the human team.  
4. **Documentation stays fresh** – the Feedback Agent pushes final feature data into a structured SRS table (sample provided on page 7). :contentReference[oaicite:8]{index=8}  

## Implementation hints

* Use **JADE** or an equivalent lightweight MAS framework to spin up agents quickly.  
* Model blackboards as message‑queue topics; RabbitMQ or Kafka fit well for high‑throughput scenarios.  
* Embed a language‑aware LLM inside Requirement Gathering and Design Agents to parse natural‑language stories and output UML fragments.  

## Looking forward

The authors call for live trials that compare pure FDD teams versus MAS‑enhanced teams on identical feature sets. They expect sharper cycle times, steadier velocity and more predictable quality curves once the agents settle in.  

MAS Driven Development is therefore not a wholesale methodology swap; it is a **strategic infusion of autonomy** that keeps FDD’s familiar rhythm while scrubbing out its coordination overhead.

---

*Based on* **Yousef & Darbi, 2025, “Multi‑Agent System Adaptation for Feature‑Driven Development Methodology.”** :contentReference[oaicite:9]{index=9}, Source: https://aaasjournals.com/index.php/ajapas/article/view/1316/1226