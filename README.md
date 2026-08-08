# KAVE — Website Source

A from-scratch HTML/CSS recreation of the KAVE site, built so you can edit it
in VS Code and host it for free (no GoDaddy Website Builder subscription).

## Files

- `index.html` — home page
- `sewing.html`, `graphic-design.html`, `embroidery.html`, `writing.html`, `other.html` — one page per category, each with a placeholder photo gallery
- `privacy-policy.html` — stub, edit to match what you actually collect
- `style.css` — all styling (colors, fonts, layout) in one place

## Editing in VS Code

1. Install [VS Code](https://code.visualstudio.com/) and the **Live Server** extension (by Ritwick Dey) — lets you preview changes in the browser instantly as you save.
2. Open this folder in VS Code (`File > Open Folder`).
3. Right-click `index.html` → **Open with Live Server** to preview.
4. To add real photos: drop image files into an `images/` folder, then in the relevant page replace a block like

   ```html
   <div class="placeholder-img">Photo 1</div>
   ```

   with

   ```html
   <img src="images/your-photo.jpg" alt="Describe the piece">
   ```

5. Colors and fonts all live at the top of `style.css` under `:root`, so you can retheme the whole site by changing a few hex values.

## The contact form

Right now the form doesn't send anywhere — it's just HTML. Since this will be a static site (no server), the easiest free way to make it work is **Formspree**:

1. Sign up free at [formspree.io](https://formspree.io) and create a form to get an endpoint URL.
2. In `index.html`, change:
   ```html
   <form>
   ```
   to:
   ```html
   <form action="https://formspree.io/f/YOUR_ID" method="POST">
   ```
   and add `name="name"`, `name="email"`, `name="message"` (already present) so Formspree captures the fields.

## Hosting for free with your own domain

You already own `kave.lv` — you don't need to buy a new domain, you can just stop paying for GoDaddy's Website Builder and point the domain somewhere free instead. Two solid free options:

### Option A: GitHub Pages (simplest, free forever)
1. Create a free GitHub account and a new repository (e.g. `kave-site`).
2. Push this folder to it (VS Code has built-in Git support: `Source Control` panel → publish to GitHub, or use the terminal: `git init`, `git add .`, `git commit -m "first version"`, then follow GitHub's push instructions).
3. In the repo, go to **Settings → Pages**, set source to the `main` branch, root folder.
4. Your site will be live at `https://yourusername.github.io/kave-site/`.
5. To use `kave.lv` instead: in the repo's Pages settings, add `kave.lv` as a **custom domain**, then in your domain's DNS settings (you can manage DNS at GoDaddy even without their Website Builder, or transfer DNS elsewhere free) add the A records GitHub provides — GitHub's docs walk through this: https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site

### Option B: Netlify or Cloudflare Pages (also free, drag-and-drop)
1. Sign up at [netlify.com](https://netlify.com) or [pages.cloudflare.com](https://pages.cloudflare.com).
2. Drag this folder onto their dashboard (Netlify supports plain drag-and-drop deploys) or connect it to a GitHub repo for automatic redeploys when you push changes.
3. Add `kave.lv` as a custom domain in their dashboard, then update your domain's DNS records as instructed.

Either way, once DNS points at the new host, you can cancel the GoDaddy Website Builder plan — just keep the domain registration itself (that's usually a separate, much cheaper yearly fee, not the monthly builder charge).

## Notes

- This is an original design (fonts, colors, layout, code) inspired by the structure of your existing site, not a copy of GoDaddy's template code.
- All copy is placeholder based on what's on your live site — swap in your real photos and any updated text.
