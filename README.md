# Perruzza Time To Go

Campaign website built with [Astro](https://astro.build), deployed on Netlify. Marketing publishes blog posts through [Decap CMS](https://decapcms.org) at `/admin` (no Git or markdown required).

## Local development

```bash
npm install
npm run dev
```

Open [http://localhost:4321](http://localhost:4321). Blog list: `/blog`. CMS UI: `/admin` (login only works after Netlify Identity is enabled on the deployed site).

```bash
npm run build   # output in dist/
npm run preview # preview production build
```

## One-time Netlify setup (required for the editor)

Do this in the [Netlify dashboard](https://app.netlify.com) for this site after the Astro deploy is live:

1. Confirm the site is connected to the GitHub repo `TakuTahran/perruzzamustgo` and builds with `npm run build` → publish `dist` (see `netlify.toml`).
2. **Identity** → enable Identity → **Registration** = Invite only.
3. **Identity** → **Services** → enable **Git Gateway** (lets the CMS commit posts to GitHub).
4. **Identity** → **Invite users** → send invites to marketing emails.
5. Writers open `https://<your-domain>/admin`, accept the invite email, set a password, then publish.

### Writer workflow

1. Go to `/admin` and log in.
2. **Blog Posts** → **New Blog Posts** → fill title, date, body (optional cover image).
3. Click **Publish**.
4. Wait for the Netlify deploy (~1–2 minutes).
5. Post appears at `/blog/<slug>`.

## Project layout

| Path | Purpose |
|------|---------|
| `src/pages/index.astro` | Homepage |
| `src/pages/issues.astro` | Issues detail page |
| `src/pages/blog/` | Blog index + post pages |
| `src/content/blog/` | Blog markdown (CMS writes here) |
| `public/admin/` | Decap CMS UI + config |
| `public/images/` | Static images |
