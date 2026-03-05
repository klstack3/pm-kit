# Prompt Evaluation Criteria

Every prompt in PM-Kit is scored before inclusion. This ensures a consistent quality bar across the library.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Scoring Rubric

Each prompt is rated 1–3 across five criteria (max 15 points):

| Criteria               | 1 (Weak)                                        | 2 (Adequate)                                          | 3 (Strong)                                                                           |
| ---------------------- | ----------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Specificity**        | Vague task, no role or success criteria defined | Task is clear but role or deliverable is implicit     | Role, task, and success criteria are all explicitly defined                          |
| **Structure**          | Unstructured wall of text                       | Some organization but no clear sections or sequencing | Well-organized with distinct phases, sections, or step sequencing                    |
| **Reasoning Guidance** | No guidance on how to think through the task    | Some direction (e.g., "think step by step")           | Multiple reasoning techniques (chain-of-thought, frameworks, devil's advocate, etc.) |
| **Output Quality**     | No format specified, no examples                | Format mentioned but no examples or template          | Format specified with a template or concrete example of expected output              |
| **Robustness**         | No handling of ambiguity or edge cases          | Some acknowledgment of uncertainty                    | Actively asks clarifying questions, surfaces risks, handles edge cases               |

## Scoring Thresholds

- **Below 9:** Not ready for the repo. Needs significant rework.
- **9–12:** Solid prompt, worth including. May have room to improve in one area.
- **13–15:** Exceptional. Production-ready with strong coverage across all criteria.

## What We Look For

Our criteria synthesize best practices from multiple prompt engineering frameworks and official model provider documentation:

### Construction Frameworks

- [COSTAR](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41/) — Sheila Teo (Context, Objective, Style, Tone, Audience, Response)
- [RISEN](https://easyaibeginner.com/risen-framework-ai-prompt-for-chatgpt/) — Kyle Balmer (Role, Instructions, Steps, Expectation, Narrowing)
- [CRISPE](https://www.parloa.com/knowledge-hub/prompt-engineering-frameworks/) — OpenAI-originated (Capacity/Role, Insight, Statement, Personality, Experiment)

### Evaluation Frameworks

- [Reveriano Rubric](https://medium.com/@reveriano.francisco/from-art-to-engineering-a-practical-rubric-for-gpt-4-1-prompt-design-e4cc9f9d55de) — Francisco Reveriano (5-category × 1–3 scale, basis for our scoring system)
- [PromptBuilder 2026 Checklist](https://promptbuilder.cc/blog/prompt-engineering-best-practices-2026) — Anti-patterns and best practices

### Official Model Provider Docs

- **Anthropic (Claude):** [Prompt Engineering Overview](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview) · [Claude 4.x Best Practices](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/claude-4-best-practices)
- **OpenAI (GPT):** [Prompt Engineering Guide](https://developers.openai.com/api/docs/guides/prompt-engineering/) · [GPT-4.1 Prompting Guide](https://cookbook.openai.com/examples/gpt4-1_prompting_guide)

### Community Reference

- [Prompt Engineering Guide](https://www.promptingguide.ai/) — Community-maintained, model-agnostic resource
