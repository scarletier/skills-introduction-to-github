# CLAUDE.md - AI Assistant Guide

This document provides context for AI assistants working with this repository.

## Repository Overview

This is a **GitHub Skills** learning repository that teaches newcomers the fundamentals of GitHub through a hands-on, self-paced exercise. The repository is part of GitHub's official skills training curriculum.

**Purpose**: Teach users GitHub basics including repositories, branches, commits, and pull requests.

**License**: MIT License (GitHub, Inc.)

## Repository Structure

```
skills-introduction-to-github/
├── .github/
│   ├── steps/                    # Learning content (markdown instructions)
│   │   ├── 1-create-a-branch.md
│   │   ├── 2-commit-a-file.md
│   │   ├── 3-open-a-pull-request.md
│   │   ├── 4-merge-your-pull-request.md
│   │   └── x-review.md           # Final review/completion content
│   └── workflows/                # GitHub Actions for validating learner progress
│       ├── 0-start-exercise.yml
│       ├── 1-create-a-branch.yml
│       ├── 2-commit-a-file.yml
│       ├── 3-open-a-pull-request.yml
│       └── 4-merge-your-pull-request.yml
├── .gitignore                    # Standard gitignore for compiled files, packages, logs, OS files
├── LICENSE                       # MIT License
├── PROFILE.md                    # Sample profile file created during exercise
├── README.md                     # Exercise landing page with instructions
└── CLAUDE.md                     # This file
```

## Learning Exercise Flow

The exercise teaches four sequential steps:

### Step 1: Create a Branch
- User creates a branch named `my-first-branch`
- Workflow triggers on push to that branch name
- Teaches: Git branching, parallel development

### Step 2: Commit a File
- User creates/edits `PROFILE.md` on their branch
- Workflow triggers on push to `my-first-branch`
- Teaches: Commits, file changes, commit messages

### Step 3: Open a Pull Request
- User opens PR from `my-first-branch` to `main`
- Workflow validates PR title ("Add my first file") and description
- Teaches: Pull requests, code review process

### Step 4: Merge the Pull Request
- User merges the PR
- Workflow triggers on PR close with merge
- Teaches: Merging, branch cleanup

## GitHub Actions Workflows

### Workflow Architecture

Each workflow follows a consistent pattern:

1. **Find Exercise Issue** - Locates the tracking issue using `skills/exercise-toolkit`
2. **Check Step Work** - Validates learner completed the task correctly
3. **Post Feedback** - Comments on the issue with results and next steps
4. **Workflow Handoff** - Disables current workflow, enables next one

### Key Dependencies

- `skills/exercise-toolkit` - Reusable workflows and templates (v0.1.0, v0.4.0)
- `skills/action-text-variables@v1` - Template variable substitution
- `actions/checkout@v4` - Repository checkout

### Workflow Permissions

Workflows require:
- `contents: read/write` - Read repo, update README
- `actions: write` - Enable/disable workflows
- `issues: write` - Create/comment on issues

## Key Files

### PROFILE.md
A simple markdown file that learners create during the exercise. Contains introductory profile content.

### README.md
The landing page that greets learners with:
- Exercise introduction
- Link to the exercise issue
- Copyright and license info

### Step Files (.github/steps/*.md)
Detailed instructions for each learning step including:
- Conceptual explanations (what is a branch/commit/PR)
- Step-by-step activities with screenshots
- Troubleshooting tips in collapsible sections

## Development Conventions

### Branch Naming
- `main` - Primary branch, protected
- `my-first-branch` - Expected learner branch name (hardcoded in workflows)

### Commit Messages
- Exercise teaches: Use descriptive messages like "Add PROFILE.md"
- Follow conventional format: action + subject

### Pull Request Requirements
- Title must be: "Add my first file"
- Description must not be empty

## For AI Assistants

### When Helping Users

1. **Don't complete the exercise for them** - This is a learning exercise; guide users through steps rather than doing it for them
2. **Reference official docs** - Point users to GitHub documentation links in the step files
3. **Check workflow status** - If users report issues, the workflow files define exact validation criteria
4. **Respect the flow** - Steps must be completed in order; workflows enable sequentially

### Common Issues

- Branch name must be exactly `my-first-branch` (no prefixes/suffixes)
- PR title must be exactly "Add my first file"
- PR must have a non-empty description
- `PROFILE.md` must be in repository root

### Modifying This Repository

- Step content is in `.github/steps/`
- Workflow logic is in `.github/workflows/`
- Changes to validation criteria require workflow updates
- External toolkit versions are pinned; update cautiously

## External Resources

- [GitHub Skills](https://skills.github.com) - More learning exercises
- [GitHub Docs](https://docs.github.com) - Official documentation
- [Exercise Toolkit](https://github.com/skills/exercise-toolkit) - Reusable workflow components
