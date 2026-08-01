# Initialization Visibility

Ask the user whether `.init_repo/` is shared project knowledge or private local Agent material. Do not infer this choice solely from repository visibility.

Recommend sharing for collaborative or long-lived projects where design and delivery history must survive clones. Recommend local-only material for personal experiments or when the user explicitly does not want Agent records in project history.

## Shared mode

- Do not add an ignore rule for `.init_repo/`.
- If `research/` or `records/` is empty, add `.gitkeep` so the agreed structure can be tracked.
- If an existing ignore rule hides `.init_repo/`, explain it and ask before removing or overriding the rule.

## Private mode

Never modify the project's `.gitignore` or the user's global ignore configuration.

For a Git repository:

1. Resolve the repository root with `git rev-parse --show-toplevel`.
2. Resolve the repository-local exclude file with `git rev-parse --git-path info/exclude`.
3. Compute the target `.init_repo/` path relative to the Git root.
4. Add one anchored, forward-slash pattern idempotently:
   - use `/.init_repo/` when the target project is the Git root;
   - use `/<relative-project-path>/.init_repo/` when initializing a project below the Git root.
5. Preserve existing exclude entries, file encoding, and newline style.
6. Do not create `.gitkeep` files in the excluded directories.
7. Verify with `git check-ignore -v <target>/.init_repo/design/design_doc.md`.

Before applying the exclude, run `git ls-files -- <target-relative-path>/.init_repo`. Ignore rules do not affect tracked files. If any initialization files are already tracked, explain that index changes would be required and obtain separate approval; never run `git rm --cached` automatically.

For a non-Git project, create the requested local initialization material but explain that no Git-local exclude mechanism is available.

Git worktrees can share repository metadata. Treat the resolved `info/exclude` as repository-local, not necessarily exclusive to one worktree, and show the exact pattern before adding it when another worktree could match.
