# Carnations — setup guide

Everything here is free except the domain (about £8–10 a year).

## 1. Put the files on GitHub
1. Create a **private** repository called `carnations` on github.com/casidiswags.
2. Upload `index.html`, `notes.json` and the `.github` folder (keep the `.github/workflows/notify.yml` path).
   If you use a different repo name or username, change `CONFIG` near the top of the script in `index.html`.

## 2. Host it on Cloudflare Pages
1. Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git → pick `carnations`.
2. Framework preset: None. Build command: leave empty. Build output directory: `/`.
3. Deploy. You get a link like `carnations.pages.dev`. Every change to the repo redeploys automatically.

## 3. Add your custom domain
1. Buy a domain (Cloudflare Registrar is the simplest since DNS is set up for you).
2. Pages project → Custom domains → Set up a custom domain → enter it (e.g. `foryou.example.com`).

## 4. Turn on the email notification
1. On the Gmail account you'll send from: turn on 2-Step Verification, then create an **App password** (Google Account → Security → App passwords).
2. GitHub repo → Settings → Secrets and variables → Actions:
   - Secrets: `MAIL_USERNAME` (your Gmail address), `MAIL_PASSWORD` (the app password), `HER_EMAIL`.
   - Variables: `SITE_URL` (your custom domain, e.g. `https://foryou.example.com`).
3. Each time you add a note, she gets an email with a button to open the bouquet about 90 seconds later.

## 5. Connect the admin panel
1. GitHub → Settings → Developer settings → Fine-grained tokens → Generate:
   repository access: only `carnations`; permissions: **Contents: Read and write**.
2. Open `https://your-domain/#admin` on your phone or laptop, paste the token and press Connect.
   The token stays in that browser only. She never sees the Admin button.

## Good to know
- New notes show on her side once Cloudflare redeploys (under a minute).
- Read/unread is remembered per browser, so a note she's read stays bloomed on that device.
- `notes.json` is reachable by anyone who knows the site address, so keep the domain between the two of you.
