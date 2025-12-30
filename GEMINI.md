# Gemini Project Context: Personal Site (Astro Blog)

## Project Overview
This project is a personal blog site built with [Astro](https://astro.build) (v5). It is designed for high performance (100/100 Lighthouse), SEO friendliness, and ease of content authoring using Markdown and MDX.

**Key Technologies:**
*   **Framework:** Astro 5.x
*   **Language:** TypeScript
*   **Content:** Markdown (`.md`) and MDX (`.mdx`) via Content Collections
*   **Styling:** CSS (Global + Scoped)
*   **Integrations:** `@astrojs/mdx`, `@astrojs/sitemap`, `@astrojs/rss`

## Building and Running

### Prerequisites
*   Node.js (latest stable version recommended)
*   npm

### Key Commands
| Command | Description |
| :--- | :--- |
| `npm install` | Install dependencies. |
| `npm run dev` | Start the local development server at `localhost:4321`. |
| `npm run build` | Build the production site to the `./dist/` directory. |
| `npm run preview` | Preview the production build locally. |
| `npm run astro check` | Run Astro's diagnostic check (types, etc.). |

## Architecture & Conventions

### Directory Structure
*   `src/pages/`: File-based routing.
    *   `index.astro`: Homepage.
    *   `blog/[...slug].astro`: Dynamic route for rendering individual blog posts.
    *   `rss.xml.js`: Generates the RSS feed.
*   `src/content/`: Content Collections.
    *   `blog/`: Contains the blog post source files (`.md`, `.mdx`).
    *   `config.ts`: Defines the schema for the 'blog' collection (title, description, dates, heroImage).
*   `src/components/`: Reusable UI components (`Header`, `Footer`, `BaseHead`, `FormattedDate`).
*   `src/layouts/`: Layout components. `BlogPost.astro` is the main layout for blog entries.
*   `src/styles/`: Global styles (`global.css`).
*   `public/`: Static assets (fonts, favicon) served at the root.

### Development Conventions
*   **Content Authoring:** Blog posts are added to `src/content/blog/`. Frontmatter MUST match the schema defined in `src/content/config.ts` (requires `title`, `description`, `pubDate`).
*   **Styling:**
    *   Use `src/styles/global.css` for site-wide variables and reset.
    *   Use `<style>` blocks within `.astro` components for scoped styles.
*   **TypeScript:** Strict mode is enabled (`astro/tsconfigs/strict`). Ensure proper typing for component props.
*   **Images:**
    *   Place blog images in `src/assets/` to use Astro's image optimization (`<Image />` component).
    *   Static/unoptimized assets can go in `public/`.
*   **Configuration:**
    *   `src/consts.ts`: Update `SITE_TITLE` and `SITE_DESCRIPTION` here.
    *   `astro.config.mjs`: Project-level config (site URL, integrations).

## Key Files
*   `astro.config.mjs`: Main configuration file.
*   `src/content.config.ts`: Defines the structure and validation for content collections.
*   `src/layouts/BlogPost.astro`: The template used for rendering all blog posts.
*   `src/pages/blog/[...slug].astro`: The logic that routes and renders the blog posts based on the collection.
