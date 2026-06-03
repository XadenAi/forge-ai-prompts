# AI Agent Building Prompts

10 high-signal prompts for developers building AI agents, personas, and autonomous systems.

---

## Prompt 1: The Forge — System Prompt Architect

**Role:** AI developer designing a new autonomous agent
**Use case:** When you need to write a system prompt that gives an agent a distinct, consistent, high-performance identity.

You are a senior AI systems architect. I need you to write a production-grade system prompt for an agent named {agent_name} whose primary job is {primary_task}. The system prompt must define: (1) a clear persona with voice, tone, and decision-making style, (2) explicit behavioral constraints — what it will and will not do, (3) a priority hierarchy for when instructions conflict, and (4) a failure mode — what the agent says when it cannot complete a task. Do not use generic filler phrases like "I am a helpful assistant." Every sentence must encode a specific behavior or constraint. Output the system prompt as a single ready-to-deploy block, then add a brief annotation explaining each section's design choices.

---

## Prompt 2: Persona Stress Test

**Role:** AI developer or prompt engineer auditing an existing agent
**Use case:** When you want to harden an agent's persona against edge cases, jailbreaks, and identity drift.

You are a red team specialist for AI agent systems. I will give you the system prompt for an agent named {agent_name}. Your job is to identify every place where the persona is ambiguous, contradictory, or exploitable — then rewrite each weak section to be airtight. Focus on: (1) instructions that could be interpreted two ways, (2) missing constraints that a clever user could exploit, (3) tone guidance that could drift under pressure, and (4) missing fallback behavior when the agent is asked to do something outside its role. Output a line-by-line diff with the original and your improved version, and explain each change in one sentence.

---

## Prompt 3: Tool Description Engineer

**Role:** AI developer adding tools/functions to an agent
**Use case:** When writing function descriptions for LLM tool-calling so the model chooses and uses tools correctly every time.

You are an expert in LLM function-calling design. I need you to write a JSON function schema for a tool called {tool} that does the following: {tool_description}. The schema must include: a `name` that is snake_case and unambiguous, a `description` that tells the model exactly when to use this tool versus when NOT to (include a negative example), typed parameters with clear descriptions and enum constraints where applicable, and a `returns` annotation describing what the model should do with the output. Optimize for precision — the model should never misfire this tool or skip it when it should be used. Output the final JSON schema followed by a plain-English usage guide in 3 bullet points.

---

## Prompt 4: Tool Selection Disambiguation

**Role:** AI developer debugging an agent that calls the wrong tool
**Use case:** When an agent has multiple similar tools and keeps choosing the wrong one for a given task.

You are an LLM tool-calling debugger. I have an agent with the following tools: {tool_list}. The agent is incorrectly calling {wrong_tool} when it should be calling {correct_tool} for tasks like: {example_task}. Analyze why the model is confused — look at description overlap, parameter similarity, and missing disambiguation cues. Then rewrite the descriptions for both tools so they are mutually exclusive in the model's decision space. Add a "use this when / do NOT use this when" section to each description. Output the revised descriptions and a one-paragraph explanation of the root cause.

---

## Prompt 5: Chain-of-Thought Reasoning Scaffold

**Role:** AI developer building an agent that must reason through complex, multi-step tasks
**Use case:** When you need an agent to show its work and produce verifiable, auditable reasoning before acting.

You are a reasoning system designer. I need a chain-of-thought prompt scaffold for an agent that must complete the following type of task: {task_type}. Design a structured thinking protocol the agent must follow before taking any action. The protocol should include: (1) a task decomposition step where the agent breaks the goal into subtasks, (2) a dependency check where it identifies which steps must happen before others, (3) a risk scan where it flags anything that could go wrong, and (4) a confidence rating before executing. Format this as a system-level instruction block the agent runs internally before every response. The output format for each step should be explicit and parseable.

---

## Prompt 6: Adversarial Reasoning Probe

**Role:** AI developer or QA engineer testing an agent's reasoning quality
**Use case:** When you need to verify that an agent's chain-of-thought is genuinely doing logic, not just pattern-matching plausible-sounding steps.

You are an adversarial reasoning evaluator. I will give you a chain-of-thought output from an agent performing the following task: {task}. Your job is to audit the reasoning for: (1) steps that are stated but not justified, (2) logical leaps where a conclusion doesn't follow from the prior step, (3) missing branches where the agent should have considered an alternative path, and (4) false confidence — places where the agent asserts certainty without evidence. For each flaw you find, rate its severity (low / medium / critical) and provide the corrected reasoning. Output a structured audit report, then a revised chain-of-thought that fixes all critical and medium issues.

---

## Prompt 7: Episodic Memory Injection Protocol

**Role:** AI developer building an agent with persistent memory
**Use case:** When designing how an agent should load, prioritize, and use episodic memory at the start of a session.

You are a memory systems architect for AI agents. I need a prompt protocol for an agent named {agent_name} that, at the start of each session, reads its memory store and decides what to load into context. Design the protocol to: (1) score each memory entry by relevance to the current task using a simple rubric, (2) resolve conflicts when two memories contradict each other, (3) flag memories that are stale (older than {stale_threshold}) and deprioritize them, and (4) generate a "session briefing" — a 3-5 sentence summary of what the agent knows that is relevant right now. The protocol should be written as a system prompt instruction block and must work even when the memory store is empty or very large.

---

## Prompt 8: Memory Write Discipline Prompt

**Role:** AI developer designing what an agent chooses to remember
**Use case:** When you need an agent to write to memory selectively and usefully, not store everything or store nothing.

You are a memory curation specialist. I need a prompt that teaches an agent named {agent_name} to decide, after every interaction, what (if anything) deserves to be written to long-term memory. The decision protocol must cover: (1) facts that are stable and reusable vs. one-time context that should be discarded, (2) user preferences or corrections that should always be stored, (3) errors or failures the agent made that it should remember to avoid, and (4) a maximum memory write budget per session (e.g., {max_writes} entries) with a tiebreaker for when the budget is full. The output format for each memory entry should include: content, category, confidence, and expiry date. Write this as a concise instruction block the agent uses at the end of every session.

---

## Prompt 9: Agent Evaluation Rubric Generator

**Role:** AI developer or product team shipping an agent to production
**Use case:** When you need a rigorous, task-specific evaluation framework to score agent output quality before launch.

You are an AI evaluation framework designer. I need a production-ready evaluation rubric for an agent that performs the following task: {task}. The rubric must define: (1) 5-7 measurable criteria specific to this task (not generic like "accuracy" — be concrete), (2) a scoring scale for each criterion with explicit descriptions of what a 1, 3, and 5 score looks like, (3) a set of 3 adversarial test cases that probe the agent's most likely failure modes, and (4) a pass/fail threshold with reasoning. Format the output as a structured evaluation sheet that a human reviewer or automated harness can use directly. Include a "gotcha" column for each criterion — the single most common way agents fake quality on that dimension without actually doing well.

---

## Prompt 10: Regression Test Suite Builder

**Role:** AI developer maintaining an agent over time as the model or prompts change
**Use case:** When you need to build a test suite that catches quality regressions whenever the agent's system prompt, tools, or underlying model is updated.

You are a quality assurance engineer specializing in LLM agent systems. I need a regression test suite for an agent named {agent_name} that handles tasks of type: {task_type}. Design a suite of 10 test cases that covers: (1) the happy path — standard inputs that should always work, (2) edge cases — inputs at the boundary of the agent's defined scope, (3) refusal cases — inputs the agent should decline and how it should decline them, and (4) adversarial cases — inputs designed to make the agent produce plausible but wrong outputs. For each test case, specify: the input, the expected behavior (not just expected output — describe the behavior), and the failure signature — what a broken agent does instead. Format as a test suite table that can be run manually or fed into an automated eval harness.

---

## Prompt 11: Model Routing — Three-Step Agent Workflow

**Role:** AI systems builder designing cost-aware agent routing
**Use case:** When an agent needs to decide which model tier should handle requirements, planning, execution, escalation, and review.

You are a model-routing architect for AI development workflows. Design a routing policy for an agent that completes {task_type}. The policy must use a three-step workflow: (1) **Requirement Gathering** goes to a cheap fast model such as Flash, Mini, or Haiku-level to extract goals, constraints, missing context, acceptance criteria, and clarification questions; (2) **Planning** goes to a Sonnet-level medium premium model to create the implementation plan, dependency order, risk scan, and verification checklist; (3) **Execution** stays on Sonnet-level by default for implementation and focused testing. Add an escalation rule: only use a higher-reasoning model after two failed Sonnet-level execution attempts, or when the task is clearly too complex for Sonnet-level context and reasoning. Add a review rule: code review has higher priority than planning quality. The routing policy must require a review pass that audits the final diff against requirements, tests, security, edge cases, and maintainability before calling the task done. Output the policy as a concise decision tree plus an example run.
