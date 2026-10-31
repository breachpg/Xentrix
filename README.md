# Xentrix website

The marketing site for **Xentrix**, a London-based technology studio helping small, medium and enterprise businesses around the world put AI and modern tech to work.

- Live domain: [xentrixltd.co.uk](https://xentrixltd.co.uk)
- Contact: [contact@xentrixltd.co.uk](mailto:contact@xentrixltd.co.uk)

The whole site is one file, `index.html`, with all styles and scripts inside it. There is no build step, framework or dependency to install. The only external resources are Google Fonts.

## What's on the page

| Section | What it does |
|---|---|
| Hero | Rotating headline ("We make digital (and magical) Experiences / Products / Software…"), an interactive 3D neural globe, calls to action, service chips and key facts |
| 01 · Lab | Six concept projects drawn with live canvas animations. Clicking a card opens a detail sheet: the problem, what it does, how it works, tech stack and who it suits |
| 02 · Capabilities | Twelve services. Clicking a row expands it with deliverables and typical tools |
| 03 · Everyday AI | Tabs for Homes, Small teams and Enterprise, each with an example agent activity log |
| 04 · How we work | The four delivery stages: Map, Prototype, Ship, Run |
| 05 · Contact | Email (click to copy), website and location |

### Interactive details

- **Neural globe:** follows the mouse, bends away from the cursor, spins when dragged, and sends a shockwave through the network on click or tap. Its colour changes with the rotating word.
- **Scroll feedback:** progress line at the top, always-visible scrollbar, section dots on the right, and the current section is highlighted in the menu (shown next to the logo on mobile).
- **Reveal animations:** sections fade and slide in as you scroll.
- **Accessibility:** works with the keyboard (Enter or Space opens cards and rows, Esc closes the sheet), respects "reduce motion" settings, and supports light and dark mode automatically.

## Editing the content

Open `index.html` in VS Code and use Cmd+F (Mac) or Ctrl+F (Windows) to find these:

| To change… | Search for |
|---|---|
| Rotating hero words | `const words` |
| Colour for each word | `const hues` |
| Hero intro text | `London-based technology studio` |
| Lab card titles and short descriptions | `class="tile` |
| Lab card popup details | `const projects` |
| Capability rows | `class="cap` |
| Capability expanded details | `const capInfo` |
| Everyday AI example logs | `const data=` |
| Email address | `@xentrixltd.co.uk` |
| Colours and fonts | the `:root{` block at the top of `<style>` |

**Fonts:** Bricolage Grotesque (headings), Instrument Sans (body text) and JetBrains Mono (small labels).

**Preview while editing:** install the "Live Server" extension in VS Code, right-click `index.html` and choose "Open with Live Server". The page reloads every time you save.

## Hosting it for free

Any static host works because the site is a single HTML file. Pick one of the options below. All of them are free, include HTTPS, and redeploy automatically every time you push to GitHub.

### Option A: Cloudflare Pages (recommended if your domain's DNS is on Cloudflare)

1. Sign up or log in at [dash.cloudflare.com](https://dash.cloudflare.com).
2. Go to **Workers & Pages → Create → Pages → Connect to Git**.
3. Authorise GitHub and choose the `breachpg/Xentrix` repository.
4. Build settings: **Framework preset** None, **Build command** leave empty, **Build output directory** `/`.
5. Click **Save and Deploy**. You'll get a free address like `xentrix.pages.dev`.
6. Custom domain: open the project → **Custom domains → Set up a custom domain** → enter `xentrixltd.co.uk`, then repeat for `www.xentrixltd.co.uk`.
   - If the domain already uses Cloudflare DNS, the records are added for you.
   - If not, Cloudflare shows the records to add at your domain registrar. The simplest route is to move the domain's nameservers to Cloudflare (**Add a site** in the dashboard).

### Option B: Netlify

1. Sign up or log in at [app.netlify.com](https://app.netlify.com).
2. Click **Add new site → Import an existing project → GitHub** and choose `breachpg/Xentrix`.
3. Leave **Build command** empty and set **Publish directory** to `.` (a full stop).
4. Click **Deploy**. You'll get an address like `xentrix.netlify.app`.
5. Custom domain: **Domain management → Add a domain** → `xentrixltd.co.uk`. Netlify then shows the DNS records to add at your registrar, usually:
   - `A` record for `@` pointing to `75.2.60.5`
   - `CNAME` record for `www` pointing to `your-site-name.netlify.app`

   Always use the exact values Netlify shows you.
6. HTTPS is switched on automatically once DNS is working, which can take from a few minutes up to 24 hours.

Quick test without GitHub: drag the project folder onto [app.netlify.com/drop](https://app.netlify.com/drop).

### Option C: GitHub Pages

1. In the repository, go to **Settings → Pages**.
2. Under **Source**, choose **Deploy from a branch**, then branch `main`, folder `/ (root)`, and **Save**.
3. Under **Custom domain**, enter `xentrixltd.co.uk` and tick **Enforce HTTPS** when it becomes available.
4. At your registrar, add `A` records for `@` pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153` and `185.199.111.153`, plus a `CNAME` for `www` pointing to `breachpg.github.io`.

## Updating the live site

After connecting a host, publishing a change is just:

```bash
git add -A
git commit -m "Describe what changed"
git push
```

The host picks up the push and the live site updates within a minute or two.
