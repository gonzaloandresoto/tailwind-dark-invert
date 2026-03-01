# tailwind-dark-invert

Auto-invert Tailwind CSS v4 palette colors in dark mode. One import, zero config.

When the `.dark` class is active, `bg-rose-50` becomes the `rose-950` value, `text-blue-100` becomes the `blue-900` value, and so on — across all 26 color families.

## Install

```bash
npm install tailwind-dark-invert
```

## Usage

Import it alongside Tailwind CSS in your CSS file:

```css
@import "tailwindcss";
@import "tailwind-dark-invert";
```

That's it. Every Tailwind palette color now auto-inverts in dark mode.

## Custom generation

The package ships a pre-built CSS file that works out of the box. If you want to generate a version matched to your exact Tailwind installation (e.g. after a Tailwind update), use the CLI:

```bash
# Output to a file
npx tailwind-dark-invert -o dark-palette.css

# Output to stdout
npx tailwind-dark-invert
```

Then import your generated file instead:

```css
@import "tailwindcss";
@import "./dark-palette.css";
```

## How it works

Tailwind v4 defines palette colors as CSS custom properties (`--color-rose-50`, `--color-blue-300`, etc.). This package overrides those variables inside a `.dark` selector, swapping each shade with its mirror:

| Light mode shade | Dark mode shade |
|------------------|-----------------|
| 50               | 950             |
| 100              | 900             |
| 200              | 800             |
| 300              | 700             |
| 400              | 600             |
| 500              | 500 (unchanged) |
| 600              | 400             |
| 700              | 300             |
| 800              | 200             |
| 900              | 100             |
| 950              | 50              |

Shade 500 is the midpoint and stays the same.

## Color families

All 26 Tailwind v4 color families are covered:

red, orange, amber, yellow, lime, green, emerald, teal, cyan, sky, blue, indigo, violet, purple, fuchsia, pink, rose, slate, gray, zinc, neutral, stone, mauve, olive, mist, taupe

## Works with AI-generated code

AI tools pick Tailwind colors for light mode. This package makes them work in dark mode too. No `dark:` variants, no double classes, no fixing the output.

## Requirements

- Tailwind CSS v4
- A `.dark` class on an ancestor element (e.g. `<html class="dark">`)

## License

MIT
