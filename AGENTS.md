# Repository Guidelines

## Project Structure & Module Organization

This repository contains the Hugo source for `sivalabs.dev`. Site configuration is in `hugo.toml`. Page content lives in `content/`: the course index is `content/_index.html`, contact is `content/contact.html`, and course detail pages live in `content/courses/`. Shared templates live in `layouts/`, including `layouts/_default/baseof.html` and `layouts/partials/nav.html`. Static assets live in `static/` and are copied to the generated site root. Do not edit `public/`; it is generated output.

## Build, Test, and Development Commands

There is no package manager required. Preview the Hugo site locally with:

```bash
hugo server
```

Use `hugo server --disableFastRender` when changing templates or shared CSS and you want full rebuilds during preview.

Build the production static output into `public/` with:

```bash
hugo --cleanDestinationDir
```

Because pages use CDN-hosted Bootstrap, Google Fonts, and Font Awesome, test with network access when checking final appearance.

## Coding Style & Naming Conventions

Use 4-space indentation in HTML, CSS, JavaScript, and Hugo templates. Keep HTML semantic and Bootstrap-based; prefer existing custom class patterns such as `navbar-dark-custom`, `course-card`, `module-badge`, and `sidebar-card`. Use lowercase, hyphenated filenames for new pages, for example `content/courses/new-course-name.html`. Put shared styling in `static/css/site.css`; avoid page-local styles unless they are truly one-off. Course pages can set `accent` and `accentRgb` in front matter to drive theme colors.

## Testing Guidelines

No automated tests are present. Run `hugo --cleanDestinationDir` before handoff to verify templates and content compile. Manually check desktop and mobile widths, navbar collapse behavior, external links, favicon references, course page accordions, topic badges, and the Course Details sidebar.

## Commit & Pull Request Guidelines

Recent commits use short, imperative summaries such as `Add courses` and `Update profile subtitle`. Follow that style: keep the subject concise and describe the user-visible change. Pull requests should include a brief summary, list changed pages, link related issues when applicable, and include screenshots for visual/layout changes.

## Security & Configuration Tips

Do not commit secrets or analytics credentials. Keep CDN URLs intentional and versioned where possible. `uglyURLs = true` preserves existing `.html` URLs, so keep links like `/contact.html` and `/courses/java-fundamentals.html` unless the URL strategy changes intentionally. Preserve root-relative asset paths such as `/favicon.ico`, `/site.webmanifest`, and `/css/site.css`.
