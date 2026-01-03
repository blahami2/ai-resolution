# AI Resolution — Umbrella Repository

This repository is an umbrella repo that organizes multiple independent projects using Git submodules.

Each folder (e.g. week01, week02) is its own Git repository, created and managed independently (for example, by Lovable).
This repo only tracks which commit of each project is included.

## Repository Structure

```
ai-resolution/
week01/ ← git submodule
week02/ ← git submodule
week03/ ← git submodule
.gitmodules
README.md
```
Each `weekXX` folder is a separate GitHub repository linked as a submodule.

## Cloning This Repository

### Recommended (one command):

```bash
git clone --recurse-submodules git@github.com
:<you>/ai-resolution.git
```

### If already cloned without submodules:

```bash
git submodule update --init --recursive
```


## Adding a New Week (Maintainers)

From the umbrella repo root:
```bash
git submodule add git@github.com
:<you>/lovable-week04.git week04
git commit -m "Add week04 submodule"
git push
```

## Updating a Week After Changes

Submodules are pinned to a specific commit.
When a week repo advances, you must update the pointer.

```bash
cd week01
git checkout main
git pull
cd ..

git add week01
git commit -m "Update week01"
git push
```

## Connecting Subrepositories with Lovable

Each week repository is connected to Lovable independently.

### Rules:

* One Lovable project ↔ one GitHub repository
* Lovable cannot deploy from subfolders or umbrella repos

### Workflow:

1. Create a new project in Lovable.
2. Let Lovable create or connect its own GitHub repository.
3. Deploy and iterate normally in Lovable.
4. Add that GitHub repository to this umbrella repo as a submodule.
5. When Lovable pushes new commits, update the submodule pointer here.

### Important:

* Never connect Lovable to the umbrella repository.
* Never expect Lovable to read or deploy from submodules.
* Treat this repo as read-only metadata for organization.

## Important Notes

* This repo does not contain the actual source code of the weeks.
* Each submodule:
    * Has its own branches, issues, deployments, and CI
    * Is versioned independently
* Seeing “detached HEAD” inside a submodule is normal unless you explicitly work on it.
* Use the same Git URL style (SSH recommended) across all repos.

### What This Repo Is For

* High-level organization of the AI Resolution challenge
* A single entry point for all weeks
* Pinning exact versions of each project

### What This Repo Is Not For

* Editing week code directly
* Managing deployments
* Replacing individual repositories

If a week looks out of sync, update the submodule pointer and commit the change.