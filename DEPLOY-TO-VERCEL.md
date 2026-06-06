# Deploy to Vercel

## Files in this build
- `index.html` — page shell with form interceptor
- `vercel.json` — SPA routing config (replaces Netlify's `_redirects`)
- `assets/` — JS/CSS bundle and images
- `ppt-logo1.svg` — logo
- `DEPLOY-TO-VERCEL.md` — this file

## Deploy steps

### Option 1: Drag-and-drop (no command line)
1. Go to https://vercel.com/new
2. Click "Browse all templates" → scroll down to "Other"
3. Or use: https://vercel.com/new/upload
4. Drag this entire folder onto the page
5. Click Deploy

### Option 2: Vercel CLI
```
npm install -g vercel
cd /path/to/this/folder
vercel
```
Follow prompts. Site goes live in ~30 seconds.

## After deploy

### 1. Verify routing works
Click around the site: `/services`, `/about`, `/contact`. If any return 404, the `vercel.json` didn't take effect. Re-deploy.

### 2. Hook up the contact form
The form will look correct but won't actually email you until you do this:

1. Sign up at https://formspree.io  (free)
2. Create a new form
3. Copy your form ID (looks like `abcdwxyz` — the part after `/f/`)
4. Open `index.html` in a text editor
5. Find: `var FORMSPREE_ID = 'YOUR_FORMSPREE_ID';`
6. Replace `YOUR_FORMSPREE_ID` with your actual ID
7. Re-deploy

### 3. Connect your custom domain
Vercel dashboard → your project → Settings → Domains → Add `absoluteptsb.com`

If Vercel rejects the domain because the old Vercel account still claims it:
- Email Vercel support — request domain release
- Or use external DNS: point Squarespace DNS at Vercel's IP/CNAME

## Differences from the Netlify build
- `vercel.json` replaces `_redirects`
- Form submissions go to Formspree instead of Netlify Forms
- No Netlify-specific code anywhere
