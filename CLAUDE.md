# Recipes

This folder holds a personal recipe collection.

## Conventions

- One recipe per Markdown file, named in kebab-case (e.g. `lemon-garlic-chicken.md`).
- Each recipe uses this structure:

```markdown
# Recipe Name

**Serves:** 4 · **Prep:** 15 min · **Cook:** 30 min
**Tags:** dinner, chicken, weeknight

## Ingredients

- 2 tbsp olive oil
- ...

## Steps

1. ...

## Notes

Substitutions, tips, source, etc.
```

## Guidance for Claude

- Keep ingredient quantities in the units given; when converting, show both (e.g. `200 g (about 1 cup)`).
- When adding a new recipe, follow the template above and add relevant tags.
- Keep `RECIPES.md` up to date: it lists every recipe in the collection.

## Git Workflow

- **Trunk-based development:** commit directly to `main` in small, frequent commits. Avoid long-lived branches; if a branch is needed, keep it short-lived and merge it back to `main` quickly.
- **Conventional Commits:** format every commit message as `<type>(<optional scope>): <description>`.
  - `feat`: add a new recipe or feature (e.g. `feat(tacos): add tacos recipe`)
  - `fix`: correct a mistake (e.g. `fix(pierogies): correct flour quantity`)
  - `docs`: change documentation such as `CLAUDE.md` or `RECIPES.md`
  - `refactor`: restructure files without changing content
  - `chore`: maintenance, such as renaming files or updating config
- Keep the description in the imperative mood, lowercase, with no trailing period.
- Don't write a commit body. A commit is the header line, a blank line, then the footer.
- Put attribution in the footer, for example:

```
feat(tacos): add tacos recipe

Co-Authored-By: Claude <noreply@anthropic.com>
```
- When scaling a recipe, update the serving count and all quantities together.
- Don't remove the user's notes or substitutions when editing a recipe.
