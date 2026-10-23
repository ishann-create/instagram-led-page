# Nihon Design Award 2027 — Landing Page

A responsive, Japanese-inspired landing page for the Nihon Design Award 2027 early-entry campaign. Built with plain HTML, CSS, and JavaScript.

## Features

- Responsive hero section and Japanese-inspired visual theme
- Mount Fuji, cherry blossom, and temple artwork in `assets/`
- Animated design-category ticker
- Award overview and benefits section
- Signup form with client-side validation
- Supabase REST API integration for lead capture
- UTM campaign parameters captured with each signup
- Accessible status messages and reduced-motion support

## Project structure

```text
.
├── index.html
├── assets/
│   ├── nihon-fuji-hero.jpg
│   ├── nihon-fuji-ink.jpg
│   └── nihon-temple-panel.jpg
└── README.md
```

## Run locally

No build tools are required.

1. Download or clone this repository.
2. Open `index.html` in a browser, or serve the folder using a local static server.
3. For example, if Python is installed:

   ```bash
   python -m http.server 8000
   ```

   Then open `http://localhost:8000`.

## Deploy with GitHub Pages

1. Create a GitHub repository.
2. Upload `index.html`, the `assets/` folder, and this README to the repository root.
3. In GitHub, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select your default branch (usually `main`) and the `/(root)` folder, then save.
6. Wait for GitHub Pages to publish the site.

The page uses relative asset paths, so the images will load when deployed from the repository root or a GitHub Pages project site.

## Supabase setup

The form currently submits to the Supabase project configured in `index.html`. It expects a table named `public.minimalisam_leads` with the fields used by the form:

- `name`
- `email`
- `country`
- `gender`
- `portfolio_url`
- `discipline`
- `consent`
- `consent_version`
- `consented_at`
- `source`
- `utm_source`
- `utm_medium`
- `utm_campaign`

If your database table does not have all of these fields, the form submission will fail until you add them or adjust the form payload.

### Required database permissions

Enable Row Level Security (RLS) on the leads table. Permit anonymous users to **insert only** valid, consented submissions. Do not create public `SELECT`, `UPDATE`, or `DELETE` policies for leads. Never put a Supabase `service_role` key or secret key in browser code.

Use Supabase's SQL Editor to apply your table schema and insert policy. Test a signup after deployment and verify that the row appears in the table.

## Before launch

- [ ] Confirm the award name, official deadline, eligibility, entry fees, and award rules.
- [ ] Replace placeholder contact and privacy-policy details.
- [ ] Verify the Supabase table columns and RLS insert policy.
- [ ] Submit a real test signup and confirm it is stored.
- [ ] Add spam protection/rate limiting before running paid ads.
- [ ] Add analytics and advertising pixels only after configuring consent requirements.

## Notes

This is a static website. No npm install or build command is required. Google Fonts are loaded from an external stylesheet, so the site uses fallback fonts if that service is unavailable.
