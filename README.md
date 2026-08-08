# Smart Meal Planner

A single self-contained web app (`index.html` — no build step, no server, no dependencies) for high-protein, high-fiber, calorie-tracked weight loss across Mediterranean, Indian, Pakistani, Thai, Italian, American, and Mexican cuisines.

## What's in it

- **This Week** — a full 7-day plan (Mon–Sun) generated in advance so you're never deciding last-minute. Each day is themed to one cuisine for breakfast/lunch/dinner, plus two rotating high-protein snacks. Breakfast/lunch/dinner each rotate independently through that cuisine's full recipe list week-to-week (a long combinatorial cycle before anything repeats exactly — Indian/Pakistani/American run a 6–7 week cycle per slot). Click any meal title to see full step-by-step instructions, or tap swap to replace it with any other recipe of the same slot type. Mark meals eaten to log them. Navigate forward to preview future weeks any time.
- **Recipes** — searchable/filterable library of all **128 recipes** with calories, protein, fiber, carbs, fat, satiety rating, prep/cook/marinate time, numbered cooking steps, a chef's tip on getting authentic flavor, and a shortcut note where a store-bought swap (canned beans, jarred pastes, rotisserie chicken) genuinely saves time — ingredients scale live to your household size. Filter by cuisine, meal type, or **protein source** (Egg, Chicken, Goat, Shrimp, Paneer, Salmon, Turkey, Dairy, Veg).
  - Indian, Pakistani, American: 6 breakfasts + 7 lunches + 7 dinners each.
  - Mediterranean, Thai, Italian, Mexican: 3 breakfasts + 5 lunches + 5 dinners each.
  - 16 rotating snacks.
- **Shopping List** — grouped by **store first, then category**, matching an actual shopping trip: Costco (bulk proteins, pantry staples, nuts, oils), HEB (fresh produce, dairy, canned goods, everyday spices), and Indian Grocery (South Asian spices, lentils, ghee, paneer, curry leaves, specialty pastes). Quantities scale to your persons count and merge correctly across recipes — a full week's list runs about 100 clean line items instead of listing near-duplicates like "Diced onion," "Onion," and "Red onion" separately. Checkboxes and a store-grouped copy-to-clipboard button.
- **Tracker** — today's calories/protein/fiber vs. your targets (progress bars), automatically including your protein shake if enabled, plus a 7-day planned-calories chart.
- **Workout** (placeholder) — a Mon–Sun grid of free-text notes so you can jot your routine per day. Ready for a real structured schedule whenever you share one.
- **Settings** — household size (1–12), calorie/protein/fiber targets, an optional Mifflin–St Jeor calculator, a **Protein Shake** panel (see below), and a **Notifications** panel (see below).

All data (persons, targets, checked meals, swaps, shopping list state, meal times, workout notes, notification and shake preferences) is saved in the browser's `localStorage` — nothing is sent to a server, and nothing is lost between visits on the same device/browser.

### Protein priorities

Recipes are weighted toward your stated priorities: **egg, chicken, and goat** are the primary proteins (Chicken 38 recipes, Egg 18, Goat 17 — including goat dishes across every cuisine: Rogan Josh, Dum Biryani-style, Karahi, Nihari, Birria, Kleftiko-style, Massaman). **Shrimp and paneer** are second tier (16 and 9 recipes). **Salmon** appears least often (7 recipes) — strictly fewer than either shrimp or paneer. **Beef and pork are excluded from the entire app, with no exceptions.**

Default plan totals run **~1,300–1,700 kcal, ~110–150g protein, ~25–40g fiber per day** from recipes alone across all rotations — with your protein shake(s) added on top if enabled in Settings, giving real headroom to hit a high protein target without over-shooting calories.

### Ingredient system (shopping list fix)

Every one of the 128 recipes was rewritten to pull ingredients from a single canonical list (~215 items) instead of each recipe describing the same grocery item in its own words. That's what makes the shopping list actually merge correctly — "1 tsp ginger-garlic paste" in one recipe and "1 tbsp" in another now combine into one line instead of listing separately, and prep-instruction words ("diced," "chopped," "minced") no longer leak into the ingredient name. Each canonical ingredient also carries a **store tag** (Costco / HEB / Indian Grocery) used to group the shopping list.

Tuned to taste: no chickpeas anywhere, no zucchini, and Thai recipes are built without fish sauce (soy sauce, lime, toasted rice powder, and garlic-chili do the flavor work instead). The Indian track leans Hyderabadi/South Indian where it makes sense — proper tadka technique (mustard seeds and curry leaves popped in hot ghee), a Chettinad pepper chicken, a peanut-sesame bagara-style curry, dal tadka with a double tempering, and a dum biryani-style bowl — alongside familiar North Indian dishes. Pakistani recipes lean into real technique: karahi's tomato-reduction method, nihari's overnight-style low braise, achaari pickling-spice blends toasted fresh, and chapli kebab's diced (not minced) filling. Every recipe was rewritten this round for restaurant-level technique — proper searing and resting, pan sauces built by deglazing and mounting with butter, spice blooming, dry-brining, compound sauces (salsa verde, gremolata, chimichurri-adjacent chutneys) — while keeping every ingredient realistically available at Costco, HEB, or an Indian grocery store, nothing exotic or hard to source.

### Protein shake

If you drink a protein shake daily, Settings → Protein Shake lets you set protein/calories per serving and servings per day (defaults: 24g protein, 120 kcal, 2×/day — a chocolate whey shake). When enabled, it's added automatically to the Tracker's daily totals as a standing supplement — it's not tied to any meal slot, so there's nothing to check off, it just counts.

### Meal-time notifications

Settings → Notifications lets you set a target clock time for each of the 5 daily slots (breakfast, snack, lunch, snack, dinner). Once enabled, the app works backward from each recipe's prep + cook (+ marinate, where relevant) time and fires a browser notification when it's time to start marinating, time to start cooking, and when the meal should be ready — so meals land on the same schedule every day.

**This only works while the page is open in a tab** (Chrome, Safari, Edge, etc. on desktop) — it uses the standard browser Notification API, polling every 20 seconds, with no server or service worker involved. It will **not** send notifications if the tab or browser is fully closed, and **iOS Safari does not support this API for regular websites at all**, so it won't work on an iPhone home-screen tab. This is an honest constraint of a single static HTML file with no backend — true always-on phone push would require a push server and a native app or PWA with a service worker, which is out of scope here.

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
