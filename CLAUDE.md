# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

- This repo is a small markdown knowledge base of Ubuntu/Linux development commands and related notes, not an application or library.
- All tracked content currently lives in four top-level markdown files: `ubuntu_cmd.md`, `vscode_cmd.md`, `conda_cmd.md`, and `deeplearning_package.md`.
- Changes are usually direct edits to those reference documents rather than code generation or multi-package refactors.

## Common commands
- Check repo status: `git status`
- Review recent history: `git log --oneline -5`
- Preview local edits: `git diff`
- Search content across notes: `grep -R "pattern" *.md`
- Open the main Ubuntu command notes first when the request is general: `ubuntu_cmd.md`

## Working conventions
- Keep edits concise and documentation-focused.
- Preserve the existing style: short Chinese headings, short explanatory paragraphs, and fenced command examples.
- Prefer updating an existing note over creating a new file unless the topic is clearly separate.
- When adding shell commands, keep them copy-pastable and label dangerous commands clearly, matching the existing warning style in `ubuntu_cmd.md`.

## Document map
- `ubuntu_cmd.md`: the main command reference. Currently covers proxy/network setup, SSH port forwarding, disk usage, and Git workflows including clone/push/pull/checkout/reset.
- `vscode_cmd.md`: editor-specific remote development notes, especially VS Code SSH forwarding and remote proxy configuration.
- `conda_cmd.md`: short conda/package inspection notes.
- `deeplearning_package.md`: Python/deep-learning tooling notes, currently centered on OmegaConf usage and local loading of pretrained ESM2 model files.

## Architecture overview
- The repo is organized by topic, not by executable modules.
- `ubuntu_cmd.md` is effectively the primary entrypoint because it contains the broadest, most general-purpose Linux and Git usage guidance.
- The other markdown files are specialized supplements: editor/remote workflow (`vscode_cmd.md`), environment/package management (`conda_cmd.md`), and ML-related Python snippets (`deeplearning_package.md`).
- There is no build system, test runner, linter, or package manifest in the current repository state; work here is content maintenance.

## Editing guidance for future sessions
- If asked to add a new command or workflow, first decide which existing topic file it belongs in; only create a new markdown file if the content does not fit any current topic.
- Cross-check adjacent notes before duplicating instructions. For example, remote networking guidance may belong in both `ubuntu_cmd.md` and `vscode_cmd.md`, but the general command should stay in `ubuntu_cmd.md` while VS Code-specific setup stays in `vscode_cmd.md`.
- Keep command snippets minimal and practical. This repo favors quick-reference examples over long tutorials.
