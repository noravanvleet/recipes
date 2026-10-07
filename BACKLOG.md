# Backlog: Recipe Website

A static website for the recipe collection. Its main feature is a spinner that randomly picks a recipe to make and shows that recipe's ingredients.

Items are listed in priority order. The **MVP** is everything up to and including the spinner epic.

## Decisions

- **Stack:** plain HTML, CSS, and JavaScript. No framework.
- **Data:** the recipe Markdown files are the source of truth. A build script turns them into `recipes.json`, which the site loads.
- **Hosting:** GitHub Pages, deployed by GitHub Actions on every push to `main`.

---

## Epic 1: Recipe Content

The spinner needs ingredients to show, but today `RECIPES.md` only lists recipe names.

### R-1: Write a recipe file for each recipe in the list

**As a** cook, **I want** every recipe written down **so that** the site has ingredients to show.

- [ ] Each of the 18 recipes in `RECIPES.md` has its own file, following the template in `CLAUDE.md`
- [ ] Each file has at least a name and an ingredient list (steps can come later)
- [ ] File names are kebab-case (e.g. `boursin-pasta.md`)

### R-2: Link the recipe list to the recipe files

- [ ] Each entry in `RECIPES.md` links to its recipe file

### R-3: Move recipe files into a `recipes/` subfolder

- [ ] Recipe files live in one folder so the build script can find them without picking up `CLAUDE.md`, `BACKLOG.md`, etc.
- [ ] Links in `RECIPES.md` still work

---

## Epic 2: Site Foundation

### S-1: Build script that generates `recipes.json`

**As a** developer, **I want** recipe files turned into JSON **so that** the static site can load them without parsing Markdown in the browser.

- [ ] Reads every file in the recipe folder
- [ ] Outputs each recipe's name, slug, servings, prep/cook time, tags, ingredients, and steps
- [ ] Fails with a clear message naming the file if a recipe is missing a name or ingredients section
- [ ] Runs with one command (e.g. `npm run build`)

### S-2: Page skeleton

- [ ] `index.html` loads `recipes.json` and shows a page title and an empty area for the spinner
- [ ] Layout works on a phone screen with no sideways scrolling
- [ ] Supports light and dark mode

### S-3: Deploy to GitHub Pages

- [ ] A GitHub Actions workflow runs the build script and publishes the site on every push to `main`
- [ ] The site is reachable at its GitHub Pages URL

---

## Epic 3: Recipe Spinner (core feature)

### SP-1: Show the spinner wheel

**As a** cook who can't decide what to make, **I want** to see all my recipes on a wheel **so that** I know what the options are.

- [ ] The wheel has one segment per recipe, labeled with the recipe name
- [ ] Segment colors alternate so neighbors are easy to tell apart
- [ ] Long names (e.g. "Green bean Italian sausage red potato dish") stay readable, by shortening or wrapping

### SP-2: Spin to pick a recipe

**As a** cook, **I want** to spin the wheel **so that** a recipe is chosen for me.

- [ ] A "Spin" button starts the wheel spinning
- [ ] The wheel slows down and stops on a segment, chosen at random with equal odds for every recipe
- [ ] The pointer clearly lands on the chosen segment, which matches the recipe shown
- [ ] The Spin button is disabled while the wheel is spinning

### SP-3: Show the chosen recipe's ingredients

**As a** cook, **I want** to see the ingredients for the chosen recipe **so that** I can check whether I have what I need.

- [ ] When the wheel stops, the recipe name and its full ingredient list appear below the wheel
- [ ] Servings and prep/cook time appear if the recipe has them
- [ ] A link opens the full recipe (see B-2)

### SP-4: Spin again

- [ ] A "Spin again" button picks a new recipe
- [ ] The new pick is never the same as the previous one

### SP-5: Accessible spinner

- [ ] The Spin button works with the keyboard
- [ ] Screen readers announce the chosen recipe when the wheel stops
- [ ] When the user has "reduce motion" turned on, the wheel skips the animation and shows the result right away

### SP-6: Handle recipes without ingredients

- [ ] If a recipe has no ingredients written yet, the result says "Ingredients not added yet" instead of showing an empty list

---

## Epic 4: Browsing

### B-1: Recipe list page

- [ ] Shows every recipe name, sorted alphabetically, each linking to its recipe page

### B-2: Recipe page

- [ ] Shows the full recipe: name, servings, times, tags, ingredients, steps, and notes

---

## Later

Ideas to consider after the MVP ships.

- **Filter the spinner by tag:** e.g. spin only "pasta" or "quick" recipes
- **Exclude recipes from a spin:** uncheck recipes you're not in the mood for
- **Ingredient checklist:** tick off ingredients you already have
- **Scale servings:** adjust quantities for more or fewer people
- **Shopping list:** copy the missing ingredients to the clipboard
- **Recent picks:** remember the last few spins in the browser
