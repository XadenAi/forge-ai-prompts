# Developer Productivity Prompts

10 high-signal AI prompts for developers. Zero filler.

---

## Prompt 1: Code Review — Bug Hunter

**Role:** Developer submitting code for review
**Use case:** When you want a senior engineer's eye on a PR before it hits production.

You are a senior {language} engineer with 10+ years of experience. Review the following code for correctness, edge cases, and potential bugs. For every issue you find, explain: (1) what the bug is, (2) under what conditions it triggers, and (3) the exact fix with corrected code. After the bug list, give a 3-sentence summary of overall code quality and the single highest-priority change. Do not praise what works — only surface what needs attention.

```
{code}
```

---

## Prompt 2: Architecture Decision — Pattern Selector

**Role:** Engineer or tech lead evaluating design options
**Use case:** When you're about to commit to an architecture and need a rigorous tradeoffs analysis before you do.

I'm building {feature_description} in a {codebase} using {language/stack}. I'm considering the following approaches: {option_1}, {option_2}, {option_3}. For each option, give me: scalability ceiling, failure modes, maintenance burden at 12 months, and which team size it's optimized for. End with a single recommendation and the one assumption that, if wrong, would invalidate it. Be direct — I need a decision, not a survey.

---

## Prompt 3: Debugging — Root Cause Analyst

**Role:** Developer staring at an error they can't crack
**Use case:** When you've been stuck on a bug for more than 20 minutes and need a methodical outside view.

I'm seeing the following error in my {language} application: `{error}`. Here is the relevant stack trace and surrounding code: {stack_trace_and_code}. Walk me through root cause analysis: (1) what this error class typically means, (2) the 3 most likely causes ranked by probability given my code, (3) the exact diagnostic steps to confirm which cause it is, and (4) the fix for each possible cause. Do not guess — trace the logic.

---

## Prompt 4: Documentation — Function Doc Writer

**Role:** Developer writing or reviewing inline documentation
**Use case:** When you need production-quality docstrings/comments for a function without spending 15 minutes writing them yourself.

Write a complete {language}-style docstring for the following function. Include: a one-line summary, a longer description of what it does and why (not just what the code says), all parameters with types and what they represent, return value with type and meaning, any exceptions that can be raised and when, and one usage example that covers the non-obvious case. Match the tone and format of the {docstring_format} standard (e.g., Google, NumPy, JSDoc).

```
{function_code}
```

---

## Prompt 5: Git Commits — Atomic Commit Crafter

**Role:** Developer committing changes to a shared repository
**Use case:** When you've made meaningful changes and need a commit message that will make sense to your future self and your teammates in 6 months.

I made the following changes to {codebase}: {diff_or_description}. Write a git commit message following the Conventional Commits spec. Line 1: type(scope): imperative summary under 72 chars. Lines 3+: bullet points explaining *why* the change was made, not what changed (the diff shows what). Include any breaking changes, linked issue numbers ({issue_format}), and one sentence on the approach chosen if a non-obvious decision was made. No filler phrases like "updated" or "fixed stuff."

---

## Prompt 6: Code Review — Improvement Advisor

**Role:** Developer doing a self-review before requesting teammates' time
**Use case:** When you want to improve code quality, readability, and maintainability before opening a PR.

You are a principal engineer reviewing this {language} code for a production {codebase}. Do not look for bugs — assume it works. Instead, identify: (1) readability issues that will slow down the next developer, (2) abstractions that are either missing or over-engineered, (3) performance optimizations worth making vs. premature optimizations to skip, and (4) any violations of the SOLID principles or {style_guide}. For each finding, show the before and after. Rank by impact, highest first.

```
{code}
```

---

## Prompt 7: Debugging — Silent Failure Investigator

**Role:** Developer debugging a system that fails without throwing errors
**Use case:** When your code runs successfully but produces wrong output and you have no stack trace to follow.

My {language} function is producing incorrect output with no error thrown. Expected: {expected_output}. Actual: {actual_output}. Input: {input}. Code: {code}. Analyze this systematically: check for off-by-one errors, type coercion issues, mutated state, incorrect assumptions about input shape, and logic branches that silently return the wrong value. For each candidate, show me the exact condition that would produce my observed output and the one-line fix. Start with the most likely cause.

---

## Prompt 8: Architecture Decision — Refactor Roadmap

**Role:** Tech lead planning a refactor of legacy code
**Use case:** When you need to migrate messy legacy code to a clean architecture without breaking production.

I have a {language} codebase with the following structure: {current_structure}. It has these known pain points: {pain_points}. I want to migrate toward {target_architecture} (e.g., hexagonal, clean architecture, event-driven). Give me a phased refactor plan where each phase: (1) can be shipped independently without breaking existing behavior, (2) has a clear "done" criteria, and (3) reduces risk rather than increasing it. Flag any refactors that require a feature freeze and explain why. I need this ordered by business risk, not technical elegance.

---

## Prompt 9: Documentation — README Generator

**Role:** Developer open-sourcing or handing off a project
**Use case:** When you need a complete, professional README that makes strangers actually want to use your project.

Write a complete README.md for the following project: {project_name}. The project does: {what_it_does}. Tech stack: {stack}. Here is the entry point / main module: {code_or_description}. The README must include: a one-paragraph hook that sells the project in plain English, a prerequisites section, step-by-step installation that works on a fresh machine, a usage section with at least 2 real examples (not "Hello World"), a configuration reference table, and a contributing section. Use concrete commands. Assume the reader has never seen this codebase.

---

## Prompt 10: Git Commits — PR Description Writer

**Role:** Developer opening a pull request for team review
**Use case:** When you need a PR description that gives reviewers everything they need to review fast and merge with confidence.

Write a pull request description for the following changes to {codebase}: {diff_or_summary}. Structure it as: (1) **What** — one paragraph on what changed and what it enables, (2) **Why** — the problem this solves or the requirement it fulfills, referencing {issue_or_ticket} if applicable, (3) **How** — the key technical decisions made and any alternatives considered, (4) **Testing** — how to verify it works, including the exact steps a reviewer should run, (5) **Risks** — anything that could go wrong and how it was mitigated. Write for a reviewer who is smart but has zero context on this ticket.
