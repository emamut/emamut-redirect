# emamut-redirect

A lightweight, static HTML redirect page designed to seamlessly forward visitors to [emamut.com.co](https://emamut.com.co).

## Features

- **Fast Client-Side Redirection:** Uses `window.location.replace()` to immediately forward users without polluting browser back-button history.
- **SEO & No-JS Fallback:** Includes a `<meta http-equiv="refresh">` tag and `<link rel="canonical">` to support search engine crawlers and browsers with JavaScript disabled.
- **Clean UI Fallback:** If redirection takes a moment, users see a responsive centered card with an animated loading spinner and a direct clickable link.
- **Zero Dependencies:** Pure HTML/CSS/JS in a single file with no external frameworks or libraries.

## Redirection Flow

1. **Meta Refresh:** `<meta http-equiv="refresh" content="0; url=https://emamut.com.co" />` triggers fallback redirection.
2. **JavaScript Navigation:** `window.location.replace('https://emamut.com.co')` triggers immediate client redirection.
3. **Manual Link:** Fallback clickable anchor in case browser security settings block automated redirects.

## Customization

To redirect to a different destination URL, update the target URL in [index.html](file:///Users/emamut/workspace/TEMP/emamut-redirect/index.html):

1. **Meta Refresh & Canonical URL (Lines 10–11):**
   ```html
   <meta http-equiv="refresh" content="0; url=https://your-domain.com" />
   <link rel="canonical" href="https://your-domain.com" />
   ```

2. **JavaScript Redirect (Line 16):**
   ```javascript
   window.location.replace('https://your-domain.com');
   ```

3. **Fallback Link (Line 88):**
   ```html
   <a href="https://your-domain.com" id="target-link">https://your-domain.com</a>
   ```

## Local Preview

You can test the redirect page locally using any static web server:

```bash
# Using Python 3
python3 -m http.server 8000

# Using Node.js
npx serve
```

Then visit `http://localhost:8000` in your web browser.

## Deployment

Deployable directly to any static hosting provider:

- **GitHub Pages:** Enable GitHub Pages in repository settings pointing to the root directory or `gh-pages` branch.
- **Cloudflare Pages / Vercel / Netlify:** Connect the repository and set the publish directory to `/` (no build command needed).
- **Web Servers (Nginx / Apache / Caddy):** Place `index.html` in your web root directory.
