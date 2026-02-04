---
name: uu5-install-library-skills
description: Installs shared UU5 library skills into the current project via git subtree (initial add + npm install) and ensures .prettierignore includes entries for skill templates. Use when the user asks to install uu5 skills, inject skills, set up shared skills, add uu5 library skills to this project, or run initial skills setup.
---

# Install UU5 library skills

Installs the shared UU5 library skills repo into the current project under `.cursor/skills` using git subtree, installs skill dependencies, and ensures the project has a `.prettierignore` that excludes Handlebars templates used by the skills.

Run all steps from the **root of the repository** (workspace root) where you want to use the skills.

## Step 1 – Initial add (git subtree)

1. Add the remote (only if not already present). If the remote `uu5-skills` already exists, skip adding it.

   ```bash
   git remote add uu5-skills ssh://git@uucodebase.plus4u.net:9422/52e85aa87d664ab18687e35c58706c0b/uu5_library_skillsg01.git
   ```

2. Fetch and add the subtree:

   ```bash
   git fetch uu5-skills --tags
   git subtree add --prefix=.cursor/skills uu5-skills master --squash
   ```

   This populates `.cursor/skills/` with the shared skills. Allow time for the fetch (network).

## Step 2 – Install skill dependencies

The generator skills use **node-plop**. Install dependencies under `.cursor/skills` (from project root):

```bash
npm install --prefix .cursor/skills
```

Alternatively:

```bash
cd .cursor/skills && npm install
```

Allow sufficient time for npm install (e.g. 60000 ms or more).

## Step 3 – Ensure `.prettierignore` at project root

Ensure the project has a `.prettierignore` file at the **workspace root** that excludes Handlebars templates (used by the skills). Prettier can break `.hbs` formatting (e.g. `{{name}}` placeholders).

- If `.prettierignore` does **not** exist, create it with:

  ```
  # Handlebars templates – Prettier breaks HBS formatting (e.g. {{name}} placeholders)
  *.hbs
  ```

- If `.prettierignore` **exists**, ensure it contains a line that ignores `*.hbs` (and add the comment line if helpful). If `*.hbs` or a more specific pattern (e.g. `.cursor/skills/**/*.hbs`) is already present, do not duplicate it.

## Summary

1. Add remote `uu5-skills` (if missing), then `git fetch uu5-skills --tags` and `git subtree add --prefix=.cursor/skills uu5-skills master --squash`.
2. Run `npm install --prefix .cursor/skills` (or `cd .cursor/skills && npm install`).
3. Create or update `.prettierignore` at project root so that `*.hbs` is ignored.

## Notes

- Use the same remote name (`uu5-skills`) and prefix (`.cursor/skills`) for later upgrades (subtree pull).
- If `.cursor/skills` already exists with other content, subtree add may overwrite or merge; prefer an empty or non-existent `.cursor/skills` for initial add.
- This skill is intended as a **personal skill** (~/.cursor/skills/uu5-install-library-skills) so it is available in new projects before any skills are installed.
