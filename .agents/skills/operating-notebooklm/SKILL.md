---
name: operating-notebooklm
description: Interacts with the NotebookLM MCP server to manage notebooks, add sources, perform deep research, and generate studio content. Use when the user asks to manage NotebookLM or synthesize information.
---

# Operating NotebookLM

## When to use this skill
- The user asks to list, create, query, or delete NotebookLM notebooks.
- The user wants to add external sources like URLs, text, or Google Drive documents to a notebook.
- The user initiates a web or Drive research task to find new sources.
- The user requests generation of study materials (flashcards, quizzes, study guides) or media overviews (audio, video, infographics) from notebook sources.

## Workflow

- [ ] **Establish Authentication**: Run `notebooklm-mcp-auth` via the Bash/terminal tool and instruct the user to log in if auth errors occur. Follow up with `refresh_auth`.
- [ ] **Manage Notebooks**: Use `notebook_list`, `notebook_create`, `notebook_get`, or `notebook_rename` to initialize the workspace context.
- [ ] **Ingest Sources**: Add existing URLs, text, or Drive docs (`notebook_add_url`, etc.), or use `research_start` to discover new ones.
- [ ] **Handle Async Tasks**: For research, poll `research_status` -> call `research_import`. For studio artifacts, poll `studio_status` to get URLs upon completion.
- [ ] **Require Confirmation**: For all generation tools (`audio_overview_create`, `video_overview_create`, `report_create`, etc.), clearly ask for user approval before invoking them with `confirm=True`.
- [ ] **Query Synthesis**: Use `notebook_query` to ask questions about the ingested sources (not for open web searches).

## Instructions

### 1. Authentication
Do not use `save_auth_tokens` manually unless the CLI fallback is explicitly requested. Run the terminal command `notebooklm-mcp-auth` and prompt the user.

### 2. Deep Research
To gather new sources automatically:
1. Call `research_start` with the query and mode (`fast` or `deep`).
2. Loop `research_status` to wait for completion. Use `compact=True` (default) to save context window.
3. Call `research_import` to finalize adding the discovered sources into the notebook.

### 3. Studio Content Generation
Tools like `audio_overview_create`, `report_create`, `flashcards_create`, `quiz_create`, `slide_deck_create`, etc.
1. Present the plan to the user.
2. Only after receiving explicit approval, call the respective tool with `confirm=True`.
3. Check `studio_status` to retrieve the results.

### 4. Drive Sync
To ensure Google Drive sources are up to date:
1. Call `source_list_drive` to check for freshness.
2. Ask for user confirmation, then call `source_sync_drive` passing the stale source IDs.

## Resources
- Uses the NotebookLM MCP internal tools.
