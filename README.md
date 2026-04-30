# Hatmada Landing Page

This folder is a static GitHub Pages package generated from the public Lovable landing page at `https://hatmada.lovable.app`.

It lives inside the main Hatmada mobile app repository. The deployment workflow at `.github/workflows/hatmada-pages.yml` uploads only this `landing-page` folder, so app source files, build artifacts, and environment files are not published.

## What is included

- The current landing page HTML, CSS, JavaScript, logo, hero image, and Open Graph image.
- The Lovable badge and Lovable analytics snippet were removed from `index.html`.
- The existing waitlist form remains wired to the same Supabase project and table already used by the Lovable site.
- `CNAME` is set to `hatmada.app`.
- `.nojekyll` is included so GitHub Pages serves the static bundle directly.
- `.github/workflows/hatmada-pages.yml` is included at the repository root for GitHub Actions based Pages deployment.

## Publish Steps

1. Commit and push `landing-page/**` and `.github/workflows/hatmada-pages.yml` to the Hatmada repository.
2. In the GitHub repository, open `Settings` -> `Pages`.
3. Under `Build and deployment`, choose `GitHub Actions`.
4. Push to the `main` branch, or open the `Deploy Hatmada Landing Page` workflow and run it manually.
5. In `Settings` -> `Pages`, set the custom domain to `hatmada.app`.
6. In your DNS provider, replace the current apex `A` records for `hatmada.app` with GitHub Pages records:

```text
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

7. Set `www.hatmada.app` as a `CNAME` pointing to your GitHub Pages default domain, usually `YOUR-GITHUB-USERNAME.github.io`.
8. After DNS finishes propagating, return to `Settings` -> `Pages` and enable `Enforce HTTPS`.

## Form Note

The form posts directly from the browser to Supabase using the same public anon key and table already embedded in the live Lovable app:

```text
landing_waitlist_subscribers
```

I did not submit a test email, so the real waitlist was not polluted. If submissions work on Lovable but fail after moving to GitHub Pages, check Supabase row-level security, allowed origins, or referrer checks for the new domain.

## Lovable Export Note

Lovable's cleanest export path is the official GitHub integration. This package is a static mirror of the public deployed site, not the editable Lovable source project.
