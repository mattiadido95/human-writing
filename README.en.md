# Human Writing

[Italiano](README.md)

Two complementary skills for Claude Code: one writes and reviews text for human readers; the other builds a personal writing profile through exercises and user-approved corrections.

## What is a skill?

A skill is a directory containing a `SKILL.md` file and optional reference material. It gives Claude Code reusable instructions for a specific task. This repository contains Markdown instructions: it is not an application, requires no additional libraries, and does not modify the model.

See the [official Claude documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) for skill behavior and supported installation directories.

## The two skills

| Skill | Purpose | Activation |
| --- | --- | --- |
| `human-writing` | Write, rewrite, or review text using a personal profile while reducing artificial or repetitive phrasing. | Through a relevant request or `/human-writing`. |
| `writing-calibrator` | Build and update the profile through questions, A/B comparisons, short writing exercises, and draft-to-final comparisons. | Explicit invocation only: `/writing-calibrator`. |

Supported text includes emails to colleagues, managers, and clients; technical and project documentation; and presentation text. Tone and structure adapt to the channel and audience.

`human-writing` supports three modes:

- `generate`: create text from supplied facts, with placeholders for required information that is missing;
- `rewrite`: make the smallest effective changes to existing text;
- `audit`: identify problems and suggest directions for improvement without rewriting.

Accuracy takes priority over style preferences: facts, numbers, dates, quotations, technical terms, and uncertainty must be preserved. The goal is natural writing suited to the reader, without simulated mistakes or AI-detector optimization.

## Structure

```text
skills/
  human-writing/
    SKILL.md
    references/
      preservation.md
      channels.md
      ai-patterns.md
  writing-calibrator/
    SKILL.md
    references/
      exercises.md
      evidence-and-privacy.md
```

## Installing in Claude Code

Prerequisite: Claude Code with support for local skills.

Copy both directories inside `skills/` into your personal or project skills directory, keeping them side by side. Do not install the entire repository as a single skill.

| Scope | Skills directory | Profile directory |
| --- | --- | --- |
| Personal | `~/.claude/skills/` | `~/.claude/writing-profile/` |
| Project | `<project>/.claude/skills/` | `<project>/.claude/writing-profile/` |

A personal installation has this layout:

```text
~/.claude/
  skills/
    human-writing/
      SKILL.md
      references/
    writing-calibrator/
      SKILL.md
      references/
  writing-profile/
    voice-profile.md
    evidence-log.md
```

Both skills must be in the same `skills/` directory: the calibrator also reads the patterns from `human-writing`. Profile paths are relative to each skill directory (`../../writing-profile/`).

### Profile and evidence log: separate setup

This repository does not include `voice-profile.md`, `evidence-log.md`, or initialization templates. It does not ship a calibrated personal profile.

- `voice-profile.md` contains approved preferences organized by scope, with status and provisional or confirmed rules.
- `evidence-log.md` contains evidence, hypotheses, contradictions, a changelog, and calibration progress.

If the profile is missing, malformed, or has `status: vuoto`, `human-writing` can use general rules and suggests the calibrator. If either the profile or the log is missing or malformed, `writing-calibrator` stops and asks how to proceed: it does not initialize or overwrite them automatically. Initial setup of these files therefore needs to be agreed separately with the agent.

Personal files should stay outside the public repository. For a project installation, exclude `.claude/writing-profile/` from that project's version control. This repository's `.gitignore` excludes the `writing-profile/` directory.

## Usage examples

```text
/human-writing Write an email to a colleague: I need confirmation of the driver version by Friday to proceed with acceptance testing.
```

```text
/human-writing Rewrite this client email while preserving all facts and deadlines: [text]
```

```text
/human-writing Review the tone of this text without rewriting it: [text]
```

Once the profile and log have been prepared:

```text
/writing-calibrator mail cliente
```

```text
/writing-calibrator Compare this draft with the text I actually sent: [anonymized draft and final text]
```

The calibrator asks one question at a time. A single answer is evidence, not a confirmed rule; profile changes require explicit approval. `human-writing` reads the profile but does not update it.

## Languages and limitations

- The instructions are in Italian, and the initial calibration workflow covers Italian only. This English README documents the same behavior; it does not extend calibration to English.
- For English text, `human-writing` applies preservation rules, channel rules, and general patterns without automatically translating Italian preferences.
- Presentation support covers text only: these skills do not produce layouts or `.pptx` files.
- Code, SQL, JSON, configuration files, commit messages, stack traces, code comments, and technical chat answers are outside scope.
- Review generated text before sending it; the skill's final checklist does not guarantee error-free output.

## Privacy

The included exercises are synthetic. The calibrator requires anonymized examples and does not retain full texts. Its reference rules exclude credentials, regulated data, and client or confidential material from calibration; saving evidence requires consent.

Text is processed in the Claude Code environment you use: these instructions do not introduce a local processing service or change the service's data-handling terms.
