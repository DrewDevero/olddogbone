# olddogbone

Public website for the Old Dog Bone brand. This is a static HTML site with no build step or package dependencies.

## What's on the site

- Old Dog Teacher: Ronald "Old Dog Bone" Dougherty and Young Pup
- Rufus Reviews
- Old Dougherty Dog, Ol' Boy, and Boy Ol' Boy
- Featured YouTube Shorts, social links, a coming-soon merch section, and a direct ASPCA donation link

Page content, layout, and styles are in `index.html`. Images, audio, and video are in `assets/`. The featured video IDs and social links are set directly in `index.html`.

## Run locally

From this directory, start a local static server:

```sh
python3 -m http.server 4173
```

Open <http://localhost:4173>. Stop the server with `Ctrl+C`. YouTube embeds and Google Fonts require an internet connection.

## Deploy to Vercel

Import the repository into Vercel. Set the project root to this directory (`olddogbone_website`) if the repository contains the parent workspace; if this directory is the repository root, keep the project root as `.`.

Use the **Other** framework preset, leave the build command empty, and set the output directory to `.`. No install command is needed. Vercel will serve `index.html` and the `assets/` files as-is.

After deployment, add `olddogbone.com` in the Vercel project's Domains settings and apply the DNS records Vercel provides at the domain registrar.
