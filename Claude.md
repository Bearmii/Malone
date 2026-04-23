# CLAUDE.md — Frontend Website Rules

## Always Do First
- **Invoke the `frontend-design` skill** before writing any frontend code, every session, no exceptions.

## Reference Images & Asset Sourcing
- **Strict Image Sourcing:** You MUST ONLY use the specific images provided by the user (either uploaded in the chat or located in the `brandassets/` folder). 
- **NO PLACEHOLDERS:** Never generate, insert, or use fake placeholder images (e.g., do not use `https://placehold.co/`, Unsplash, or random generic URLs).
- **Enhancements Permitted:** You may dynamically enhance, scale, crop, or apply CSS treatments to the provided images to maximize their impact and fit the design layout.
- If a reference layout requires more images than provided, reuse the provided images creatively or ask the user for more. Do not invent filler images.
- Match layout, spacing, and typography of any reference UI provided. Do not improve or add to the UI design structure.
- Screenshot your output, compare against reference, fix mismatches, re-screenshot. Do at least 2 comparison rounds. Stop only when no visible differences remain or user says so.

## Local Server
- **Always serve on localhost** — never screenshot a `file:///` URL.
- Start the dev server: `node serve.mjs` (serves the project root at `http://localhost:3000`)
- `serve.mjs` lives in the project root. Start it in the background before taking any screenshots.
- If the server is already running, do not start a second instance.

## Screenshot Workflow
- Puppeteer is installed at `C:/Users/nateh/AppData/Local/Temp/puppeteer-test/`. Chrome cache is at `C:/Users/nateh/.cache/puppeteer/`.
- **Always screenshot from localhost:** `node screenshot.mjs http://localhost:3000`
- Screenshots are saved automatically to `./temporary screenshots/screenshot-N.png` (auto-incremented, never overwritten).
- Optional label suffix: `node screenshot.mjs http://localhost:3000 label` → saves as `screenshot-N-label.png`
- `screenshot.mjs` lives in the project root. Use it as-is.
- After screenshotting, read the PNG from `temporary screenshots/` with the Read tool.
- When comparing, be specific: "heading is 32px but reference shows ~24px", "card gap is 16px but should be 24px"
- Check: spacing/padding, font size/weight/line-height, colors (exact hex), alignment, border-radius, shadows, image sizing

## Brand Identity: "Malone Party Boy Construction Rapper"
- **Vibe:** Post Malone meets industrial worksite. Grungy, high-energy, unapologetic streetwear/hip-hop crossover. 
- **Typography:** Brutalist, ultra-heavy impact sans-serifs for headings (think caution signs). Pair with a stark, legible sans for body text. Use tight tracking (`-0.03em`) on massive, uppercase headers.
- **Colors:** Concrete Gray, Asphalt Black, and high-visibility industrial accents (Safety Orange, Hi-Vis Neon Yellow). Add a gritty accent color (like double-cup purple or Solo cup red). NEVER use default Tailwind palettes.
- **Styling & Textures:** High contrast, thick borders (`border-4`, `border-black`). UI elements should feel physical and industrial. Gradients should be harsh or metallic. Add SVG noise/grain for a dirty, distressed feel. 
- **Shadows:** Hard, solid neo-brutalist drop shadows (e.g., `shadow-[8px_8px_0px_0px_rgba(0,0,0,1)]`). No soft, feathered `shadow-md`.
- **Image Treatments:** Apply a dark, moody gradient overlay (`bg-gradient-to-t from-black/80`) and a color treatment layer with `mix-blend-luminosity` or `mix-blend-multiply` to the provided images to make them feel raw and backstage.
- **Interactive States:** Clickables should have aggressive hover states—inverted colors, shifted hard shadows, or harsh neon borders.

## Output Defaults
- Single `index.html` file, all styles inline, unless user says otherwise.
- Tailwind CSS via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Mobile-first responsive.
- Always check the `brand_assets/` folder for logos, color guides, and the ONLY permitted image assets.

## Strict Guardrails
- **No fake images:** Only use user-provided assets. No placeholders.
- **No generic CSS:** Do not use `transition-all`. Use specific spring-style transforms.
- **No altering references:** Do not add sections, features, or content not in the reference UI.
- **Quality check:** Do not stop after one screenshot pass.