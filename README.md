# agent-skills

Repository of reusable agent skills and workflow assets.

## Overview

This project stores local skill definitions used by coding agents.
Each skill lives in its own folder and is primarily defined by a `SKILL.md` file,
optionally with scripts, templates, references, and supporting assets.

## Structure

- `.agents/skills/`: skill catalog (one folder per skill)
- `.agents/workflows/`: reusable workflow docs
- `.agents/rules/`: project-specific rules and conventions

## Skill Anatomy

A typical skill folder contains:

- `SKILL.md`: trigger criteria and execution workflow
- `LICENSE.txt` (optional): license for bundled assets
- `scripts/`, `templates/`, `reference/`, or `examples/` (optional)

## Working In This Repo

1. Add or update skills under `.agents/skills/<skill-name>/`.
2. Keep instructions actionable and specific in `SKILL.md`.
3. Prefer reusing existing scripts/templates over duplicating logic.
4. Validate paths and references after edits.

## Notes

- This README describes the current `.agents` layout.
- Keep changes scoped; avoid touching unrelated skills when possible.
