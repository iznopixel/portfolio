# CLAUDE.md — Isabel Hankes Portfolio

Personal portfolio site for Isabel Hankes (Frontend Lead & Product Engineer), built with Astro as a static single-page site.

## Development Commands

```bash
npm install        # Install dependencies
npm run dev        # Start dev server at http://localhost:4321
npm run build      # Build for production (outputs to dist/)
npm run preview    # Preview production build locally
```

No test suite or linter is currently configured.

## Project Structure

```
src/
  components/     # Astro section components (one file per page section)
  layouts/        # BaseLayout.astro — shared HTML shell
  pages/          # index.astro — single page, composes all sections
  styles/         # global.css — design tokens, resets, utility classes
public/
  images/         # Static image assets (profile photos, project screenshots)
  favicon.svg
astro.config.mjs  # Astro config (minimal, no integrations)
tsconfig.json     # TypeScript strict mode, path aliases
```

## Page Architecture

Single-page layout. `src/pages/index.astro` composes sections in order:

```
<BaseLayout>
  <Hero />           # Full-viewport intro, nav, photo
  <Showcase />       # 2-col grid of project cards
  <ClaudeCodeBanner />
  <About />          # Bio + role chips
  <Contact />        # Links: resume, LinkedIn, email
  <Footer />
</BaseLayout>
```

## TypeScript Path Aliases

Defined in `tsconfig.json`:

| Alias          | Resolves to          |
|----------------|----------------------|
| `@components/` | `src/components/`    |
| `@layouts/`    | `src/layouts/`       |
| `@styles/`     | `src/styles/`        |

## Design System

All tokens live in `:root` in `src/styles/global.css`.

### Colors

| Token           | Value                        | Usage                        |
|-----------------|------------------------------|------------------------------|
| `--navy`        | `#152a37`                    | Hero, Showcase backgrounds   |
| `--slate`       | `#406076`                    | About, Contact backgrounds   |
| `--black`       | `#030f17`                    | Body background              |
| `--amber`       | `#f9a01b`                    | Links, accents               |
| `--teal`        | `#0ea49b`                    | Accent                       |
| `--cream`       | `#f9f7f0`                    | Primary text, buttons        |
| `--light-blue`  | `#76a2c2`                    | Tagline text, dividers       |
| `--pale-cyan`   | `#acd9e6`                    | Role chips, borders          |
| `--muted`       | `rgba(249, 247, 240, 0.65)`  | Secondary text               |

### Typography

| Token           | Stack                                    | Usage                   |
|-----------------|------------------------------------------|-------------------------|
| `--font-display`| `'Pink Average', Georgia, serif`         | Section headings (`h1`, `h2`) with `.display` class |
| `--font-body`   | `'Open Sans', system-ui, sans-serif`     | Body text               |
| `--font-ui`     | `'Open Sans', system-ui, sans-serif`     | UI text, paragraphs     |
| `--font-mono`   | `'Roboto Mono', monospace`               | Labels, `.label` class  |
| `--font-cta`    | `'Neue Machina', 'Open Sans', sans-serif`| Button text             |

Fonts loaded two ways:
- **Pink Average** — Google Fonts CDN (in `BaseLayout.astro` `<head>`)
- **Open Sans, Roboto Mono** — self-hosted via `@fontsource` npm packages (imported in `BaseLayout.astro`)

### Spacing Scale

```
--space-xs:  0.5rem
--space-sm:  1rem
--space-md:  2rem
--space-lg:  4rem
--space-xl:  6rem
--space-2xl: 8rem
```

### Layout

- `--max-width: 1200px` — `.container` max-width
- `--section-px: clamp(1.5rem, 5vw, 6rem)` — horizontal padding on all `section` elements
- `--section-py: clamp(4rem, 8vw, 7rem)` — vertical padding on all `section` elements

### Utility Classes

| Class      | Description                                                       |
|------------|-------------------------------------------------------------------|
| `.container` | Centers content, applies `max-width`                            |
| `.display`   | Display font, weight 400, tight line-height                     |
| `.label`     | Mono font, 0.7rem, bold, uppercase, wide tracking               |
| `.btn`       | Ghost button: bordered, uppercase, cream; fills cream on hover  |
| `.grainy`    | Adds SVG noise overlay via `::after` pseudo-element (subtle texture) |

## Component Notes

### `ShowcaseCard.astro`
Accepts props: `title`, `description`, `link?`, `linkLabel?`, `comingSoon?`.
Project data is hardcoded as a `const` array in `Showcase.astro`.
To add a project, append an entry to the `projects` array in `src/components/Showcase.astro`.

### `Nav.astro`
Rendered inside `Hero` (not a sticky header). Two anchor links: `#showcase`, `#contact`.

### `BaseLayout.astro`
Default `title` and `description` meta tags are set here. Override per-page by passing props.

### `.grainy` texture
Applied to `Hero`, `Showcase`, `ClaudeCodeBanner`, `Contact` sections. It uses an inline SVG `feTurbulence` filter at `opacity: 0.055`. Children of `.grainy` need `position: relative; z-index: 2` to sit above the overlay (already handled globally).

## Responsive Breakpoints

| Breakpoint     | Range           |
|----------------|-----------------|
| Mobile         | `max-width: 767px` |
| Tablet         | `768px – 1023px`   |
| Desktop        | `1024px+`          |

On mobile, grid layouts collapse to single column and decorative elements (emoji overlays) are hidden.
