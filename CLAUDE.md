# Newsmash — Claude Code Guidelines

## Branching

- Never commit or push directly to `main`. `main` is the production branch and deploys live via GitHub Pages.
- Create a feature branch for every change: `git checkout -b feature/<short-description>`.
- Open a PR and merge via GitHub, not via local merge.

## Code style

- The entire app lives in `index.html`. Keep it that way — no build tools, no frameworks.
- Run `npm install` once after cloning to set up pre-commit hooks (Prettier + HTMLHint).
- Hooks run automatically on commit. Do not bypass them with `--no-verify`.

## Assets

- Icons live in `icons/`. Regenerate from `newsmash.png` using `sips` if sizes change.
- `preview.jpg` is the social share image. Replace it if the UI changes significantly.
- Update the `og:image` and `twitter:image` URLs in `index.html` if the domain changes.

## Service worker

- The cache name is versioned (`newsmash-v1` in `sw.js`). Increment the version when making changes that must invalidate the cache for existing users.

## Deployment

- GitHub Pages deploys automatically on every merge to `main`.
- The canonical URL and Open Graph URLs are set to `https://newsmash.io/`. Update these if the domain changes.
