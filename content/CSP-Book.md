Awesome—got your PDF of **Gordon & Hobbs, _A Formal Theory of Commonsense Psychology: How People Think People Think_ (2017)**. Here’s a first pass that does the three things you asked: quick reading sweep, a comprehensive synthesis, and a big-picture diagram mapping how the ideas interlock. If you want a literal, chapter‑by‑chapter digest after this, I can spin that up next—it’s just long.

# What this book is doing (in plain English)

- **Claim:** Humans already use a rich, informal theory to explain people in terms of **beliefs, goals, plans, and emotions**. If we want humanlike AI (or just clearer thinking), we need to **make that theory explicit and formal** in logic.
    
- **Deliverable (their side):** a large, first‑order logical formalization: roughly **1,400 axioms**, arranged as **29 Commonsense Psychology theories** built on **16 “background” theories** (time, causality, etc.).
    
- **Method:** “**Successive formalization**” – get **breadth first** (cover everything you’ll need), then iteratively harden it into rigorous axioms and make the modules consistent across the whole system.
    
- **Motivation:** People unavoidably **anthropomorphize** systems. If computers are going to live in our world, they should at least **behave in ways that line up with our commonsense expectations** about minds— or understand those expectations well enough to communicate around them.
    

# The scaffolding they build on (Part II: 16 background theories)

These are the nuts‑and‑bolts modules that any psychological theory needs. In their system: **Eventualities & event structure**, **Time** (instants/intervals/durations), **Causality** (agents, ability, executability, difficulty), **Change of state**, **Space**, **Persons**, **Modality** (possibility/necessity/likelihood), **Logic reified** (reasoning about statements), **Defeasibility** (default reasoning), **Scales** (qualitative/ordered quantities), **Arithmetic** (measures/proportions), **Functions & sequences**, **Composite entities** (part–whole), **Traditional set theory**, and **Substitution / Typical elements / Instances**.

Why this matters: every “mind” predicate—believes, intends, remembers, fears—needs time, causality, scales (e.g., intensity, importance), and defeasible inference to make the everyday inferences we all casually make.

# The psychology proper (Part III: 29 theories)

Here are the cores and how to think about them:

**Representation & inference about minds**

- **Knowledge Management:** objects of belief; belief vs. knowledge; degrees of belief; assuming; focus/attention; inference & justification; mutual belief.
    
- **Similarity Comparisons:** how we judge two structured things “alike.”
    
- **Memory:** storing/retrieving; accessibility; associations; remembering/forgetting; prospective memory (“remembering to do”).
    
- **Envisioning:** “thinking of,” causal systems, mental simulation, how envisionment interacts with belief.
    
- **Explanation:** what counts as an explanation, when it fails, the process of moving from mystery → hypothesis.
    
- **Managing Expectations:** priors, surprise, and norm violations.
    
- **Other‑Agent Reasoning:** tracking others’ goals/beliefs.
    

**Goal–plan–action pipeline**

- **Goals** (and **Goal Themes** like thriving, pleasure/pain, short‑ vs long‑term).
    
- **Threats & Detection** (what counts as a threat, how serious, managing it).
    
- **Plans** as mental entities; **Plan Elements**; **Planning Modalities** (counterfactual, hypothetical); **Planning Goals** (constraints, preferences, enabling/blocking, minimizing/maximizing, locating instances); **Plan Construction** and **Plan Adaptation**.
    
- **Design** (artifacts, designing).
    
- **Decisions** (choice sets, deliberation, justifications, consequences).
    
- **Scheduling** (simultaneity, calendars, pending/scheduled plans, preferences).
    
- **Monitoring** (watching processes, characteristics like periodicity).
    
- **Execution Modalities** and **Execution Control** (start/stop, progress, costs, outcomes, abstraction/instantiation, aspect, distraction).
    
- **Execution Envisionment** (mentally simulating success/failure).
    
- **Causes of Failure** (taxonomy, causal complexes, explanation patterns).
    
- **Repetitive Execution** (iteration patterns).
    
- **Mind–Body Interaction** (perception, bodily action, levels of capability/activity, consciousness).
    
- **Observation of Plan Executions** (instructions, performances/specs, skill, evaluation).
    
- **Emotions** (general structure, intensity/arousal, happiness/sadness and “shades,” “raw” emotions, cognitively elaborated emotions like hope/fear/joy after success, envy/jealousy, liking/disliking, appraisal & coping).
    

# Their presuppositions & design choices (the “how”)

- **Stick with first‑order logic**, not modal slogans—then reify the right bits (events, propositions) so the system can **talk about its own beliefs**, justifications, etc.
    
- **Breadth first**: cover the whole day‑in‑the‑life mind pipeline (belief → goal → plan → schedule → execution → monitoring → explanation → adaptation), even if early axioms are rough.
    
- **Defeasible reasoning everywhere**: normal human inferences are **default** and break under new info.
    
- **Quantitative hooks** via **scales & arithmetic**: importance, cost, difficulty, intensity are **ordered**, sometimes numeric, so you can compare and reason about tradeoffs.
    
- **Time & event structure** are first‑class: states, events, subevents, iterations, aspect—because every mental predicate plays out over time and in parts.
    

# How all the pieces interconnect (and your diagram)

I mapped dependencies from the 16 background theories into the 29 commonsense‑psych modules, plus the key flows among the psychology modules (e.g., **Goals → Plans → Execution → Observation/Monitoring → Explanation/Adaptation**). You can open it and zoom around:

**[Download the concept map (PNG)](sandbox:/mnt/data/gordon_hobbs_commonsense_psych_map.png)**

Quick legend:

- **Left column (squares):** background theories (time, causality, scales, etc.).
    
- **Right column (circles):** psychology theories.
    
- Arrows show “supports” or “feeds into” relations (e.g., **Causality → Explanation / Threats / Emotions**; **Time → Scheduling / Execution Control**).
    
- Internal arrows on the right show the mind‑pipeline (e.g., **Plans → Execution Envisionment → Execution Modalities → Execution Control**, and **Causes of Failure → Plan Adaptation**).
    

# TL;DR of the big ideas

- Humans share a **robust, tacit folk theory** for explaining behavior; it’s not “cute”—it’s operational, and we use it constantly.
    
- To make software truly human‑compatible, we need a **formal, machine‑readable version** of that theory that lines up with how people **think people think**.
    
- That means **lots of meticulous axioms** covering everything from **belief and memory** to **scheduling and emotions**, all grounded in **time/causality/defeasibility/scales**.
    
- Do **coverage first**, then harden and reconcile the logic so the modules compose.
    

---

If this looks like the right level, say the word and I’ll:

1. produce **per‑chapter summaries** (≈1–2 tight paragraphs each, all 49 chapters + Appendix), and
    
2. export the **diagram as a vector PDF** and/or split it into **clustered sub‑maps** (e.g., “Goal–Plan–Action,” “Knowledge & Explanation,” “Emotion & Appraisal”) for easier printing.

```
mermaid
graph LR
%% Background theories
A1[Eventualities]:::bg
A2[Traditional Set Theory]:::bg
A3[Substitution / Typical / Instances]:::bg
A4[Logic Reified]:::bg
A5[Functions & Sequences]:::bg
A6[Composite Entities]:::bg
A7[Defeasibility]:::bg
A8[Scales]:::bg
A9[Arithmetic]:::bg
A10[Change of State]:::bg
A11[Causality]:::bg
A12[Time]:::bg
A13[Event Structure]:::bg
A14[Space]:::bg
A15[Persons]:::bg
A16[Modality]:::bg

%% Commonsense psychology theories
B1[Knowledge Management]:::cs
B2[Similarity Comparisons]:::cs
B3[Memory]:::cs
B4[Envisioning]:::cs
B5[Explanation]:::cs
B6[Managing Expectations]:::cs
B7[Other-Agent Reasoning]:::cs
B8[Goals]:::cs
B9[Goal Themes]:::cs
B10[Threats & Detection]:::cs
B11[Plans]:::cs
B12[Goal Management]:::cs
B13[Execution Envisionment]:::cs
B14[Causes of Failure]:::cs
B15[Plan Elements]:::cs
B16[Planning Modalities]:::cs
B17[Planning Goals]:::cs
B18[Plan Construction]:::cs
B19[Plan Adaptation]:::cs
B20[Design]:::cs
B21[Decisions]:::cs
B22[Scheduling]:::cs
B23[Monitoring]:::cs
B24[Execution Modalities]:::cs
B25[Execution Control]:::cs
B26[Repetitive Execution]:::cs
B27[Mind–Body Interaction]:::cs
B28[Observation of Plan Executions]:::cs
B29[Emotions]:::cs

%% Background → Commonsense links
A1 --> A13
A1 --> B13
A1 --> B24
A1 --> B25

A2 --> B1
A2 --> B2
A2 --> B3
A2 --> B4
A2 --> B5
A2 --> B6
A2 --> B7
A2 --> B8
A2 --> B9
A2 --> B10
A2 --> B11
A2 --> B12
A2 --> B13
A2 --> B14
A2 --> B15
A2 --> B16
A2 --> B17
A2 --> B18
A2 --> B19
A2 --> B20
A2 --> B21
A2 --> B22
A2 --> B23
A2 --> B24
A2 --> B25
A2 --> B26
A2 --> B27
A2 --> B28
A2 --> B29

A3 --> B15
A3 --> B18
A3 --> B28
A3 --> B11

A4 --> B1
A4 --> B5
A4 --> B6

A5 --> B22
A5 --> B18
A5 --> B11

A6 --> B15
A6 --> B20

A7 --> B1
A7 --> B5
A7 --> B10
A7 --> B6
A7 --> B8

A8 --> B8
A8 --> B12
A8 --> B17
A8 --> B29

A9 --> B8
A9 --> B12
A9 --> B17
A9 --> B21
A9 --> B22
A9 --> B29

A10 --> B13
A10 --> B14
A10 --> B5

A11 --> B5
A11 --> B4
A11 --> B10
A11 --> B14
A11 --> B29

A12 --> B22
A12 --> B24
A12 --> B25
A12 --> B23
A12 --> B13
A12 --> B26

A13 --> B11
A13 --> B24
A13 --> B25
A13 --> B23

A14 --> B28
A14 --> B23
A14 --> B20

A15 --> B7
A15 --> B27
A15 --> B29
A15 --> B28
A15 --> B1

A16 --> B16
A16 --> B1
A16 --> B6

%% Inter-theory links (Commonsense → Commonsense)
B1 --> B2
B1 --> B3
B1 --> B5
B1 --> B6
B7 --> B1
B8 --> B11
B8 --> B12
B9 --> B8
B10 --> B12
B11 --> B15
B11 --> B16
B11 --> B17
B18 --> B11
B19 --> B11
B11 --> B13
B13 --> B24
B24 --> B25
B25 --> B23
B22 --> B24
B21 --> B11
B20 --> B11
B28 --> B1
B29 --> B6
B29 --> B21
B27 --> B24
B26 --> B25
B14 --> B19

classDef bg fill:#ffefcc,stroke:#333,stroke-width:1px;
classDef cs fill:#d6eaff,stroke:#333,stroke-width:1px;

```