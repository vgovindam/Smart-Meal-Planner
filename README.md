# Smart Meal Planner

A single self-contained web app (`index.html` — no build step, no server, no dependencies) for high-protein, high-fiber, calorie-tracked weight loss across Mediterranean, Indian, Pakistani, Thai, Italian, American, and Mexican cuisines.

## What's in it

- **This Week** — a full 7-day plan (Mon–Sun) generated in advance so you're never deciding last-minute. Each day is themed to one cuisine for breakfast/lunch/dinner, plus two rotating high-protein snacks. Breakfasts alternate between 2 variants and lunch/dinner between 3 variants week-to-week (a 6-week cycle before anything repeats exactly). Click any meal title to see full step-by-step instructions, or tap swap to replace it with any other recipe of the same slot type. Mark meals eaten to log them. Navigate forward to preview future weeks any time.
- **Recipes** — searchable/filterable library of all 68 recipes with calories, protein, fiber, carbs, fat, satiety rating, prep/cook/marinate time, numbered cooking steps, a chef's tip on getting authentic flavor, and a shortcut note where a store-bought swap (canned beans, jarred pastes, rotisserie chicken) genuinely saves time — ingredients scale live to your household size.
- **Shopping List** — auto-aggregates and combines ingredients across the visible week, scaled to your persons count, grouped by category, with checkboxes and a copy-to-clipboard button.
- **Tracker** — today's calories/protein/fiber vs. your targets (progress bars), plus a 7-day planned-calories chart.
- **Settings** — household size (1–12), calorie/protein/fiber targets, and an optional Mifflin–St Jeor calculator that suggests a calorie target from your age/sex/height/weight/activity level and a chosen weekly-loss pace (capped at a safe minimum).

All data (persons, targets, checked meals, swaps, shopping list state) is saved in the browser's `localStorage` — nothing is sent to a server, and nothing is lost between visits on the same device/browser.

Default plan totals stay in the **~1,650–1,900 kcal, ~120–160g protein, ~28–40g fiber per day** range across all rotations — high enough in protein and fiber to stay satisfied while running a calorie deficit.

Tuned to taste: no chickpeas anywhere, no zucchini, and Thai recipes are built without fish sauce (soy sauce, lime, toasted rice powder, and garlic-chili do the flavor work instead). The Indian track leans Hyderabadi/South Indian where it makes sense — tempered curry leaves and mustard seeds, tamarind, a sambar, a Chettinad-style curry, and a peanut-sesame bagara baingan-style chicken curry — alongside familiar North Indian dishes.

## Hosting it

It's one static HTML file, so any static host works:

- **Netlify (fastest)**: go to [app.netlify.com/drop](https://app.netlify.com/drop) and drag `index.html` onto the page. You'll get a live URL in seconds.
- **GitHub Pages**: create a repo, add `index.html` to the root, enable Pages in repo Settings → Pages → Deploy from branch (`main`, `/root`).
- **Vercel**: `npx vercel` from the folder containing `index.html`, or drag-and-drop via the Vercel dashboard.
- **Just open it locally**: double-click `index.html` — it works fully offline with no server, since everything (data, logic, styling) is in the one file.

No environment variables, no API keys, no backend required.

## Notes / limits

- Nutrition numbers are reasonable per-serving estimates based on standard ingredient values, not lab-measured — treat them as planning guidance, not precise tracking.
- This is general nutrition guidance, not medical advice. Talk to a doctor or dietitian before starting an aggressive calorie deficit.
