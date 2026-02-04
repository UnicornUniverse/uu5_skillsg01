# uu5_skillsg01

Personal Cursor skills for UU5 workflows, shared via GitHub. Install the contents of `skills/` into your Cursor personal skills directory to use them in any project.

## Skills included

- **uu5-install-library-skills** – Installs shared UU5 library skills into a project at `.cursor/skills/uu5-library-skillsg01/` via git subtree (add + npm install) and ensures `.prettierignore` for `*.hbs`. Project-specific skills can live alongside at `.cursor/skills/<your-skill>/`. Use in new library folders by asking Cursor to “install uu5 skills” or “inject skills”.

## Install (personal Cursor skill)

1. Clone this repo (or download the `skills` folder).
2. Copy the **contents** of the `skills/` directory into your Cursor personal skills directory:
   - **macOS/Linux:** `~/.cursor/skills/`
   - **Windows:** `%USERPROFILE%\.cursor\skills\`
     So you end up with e.g. `~/.cursor/skills/uu5-install-library-skills/SKILL.md`.
3. Restart Cursor or open a new project. You can then say e.g. “install uu5 skills” or “inject skills” in any project.

### Example (macOS/Linux)

```bash
git clone <this-repo-url> uu5_skillsg01
cp -r uu5_skillsg01/skills/* ~/.cursor/skills/
```
