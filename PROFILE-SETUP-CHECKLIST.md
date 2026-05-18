# GitHub Profile — Manual Setup Checklist

These are the steps **you** must do in the GitHub web UI (Cascade can't click them for you). Do them in order. Estimated time: ~10 minutes.

---

## ✅ Step 1 — Create the special profile repo

The README at the top of your profile page is rendered from a repo whose name **exactly matches your username**.

1. Go to https://github.com/new
2. Repository name: **`Tanbin-CS`** *(yes, exactly the same as your username — GitHub will show a 💡 hint "You found a secret!")*
3. Description: `My GitHub profile`
4. Visibility: **Public** *(must be public for the README to render)*
5. **Do NOT** tick *Add a README*, *Add .gitignore*, or *Choose a license* (we already have the README locally).
6. Click **Create repository**.

---

## ✅ Step 2 — Push the README

Open PowerShell, then run:

```powershell
cd C:\Users\onoy2\CascadeProjects\github-profile-tanbin
git init
git add README.md
git commit -m "Initial profile README"
git branch -M main
git remote add origin https://github.com/Tanbin-CS/Tanbin-CS.git
git push -u origin main
```

If git asks for credentials, sign in with your GitHub account in the browser popup (or use a Personal Access Token as the password).

After push, open https://github.com/Tanbin-CS — your new profile README should render at the top with the typing banner, badges, stats card, pie chart, streak, activity graph, and trophies.

---

## ✅ Step 3 — Update profile settings

Go to https://github.com/settings/profile and set:

| Field | Value |
| --- | --- |
| **Name** | `MD Tanbin Islam` |
| **Public email** | `contact@tanbinislam.xyz` *(make sure this email is verified at https://github.com/settings/emails — add it there first if needed)* |
| **Bio** | `Software Developer & FinTech Consultant \| React/Next.js · Payment Gateways · AIUB CSE '26` |
| **URL** | `https://tanbinislam.xyz` |
| **Company** | *(optional — leave blank or add your business name)* |
| **Location** | `Dhaka, Bangladesh` |
| **Profile picture** | Upload a clean professional headshot (square, 400×400+, plain background) |

Click **Update profile**.

### Also enable "Show private contributions":

Same Profile Settings page → **Contributions** section → tick:

- ✅ **Include private contributions on my profile**

This makes your **528 private commits** show up as green squares on your contribution graph (commits stay anonymized — repo names are not exposed).

---

## ✅ Step 4 — Clean up pinned repositories

Go to https://github.com/Tanbin-CS (your profile) → click **Customize your pins**.

1. **Untick** the forked `jaimjoy/Web-Technology-M-` repo (forked classwork weakens your profile).
2. Pin your **best original repos** instead.
3. If you don't have strong public repos yet, you can leave pins empty — the README hero will dominate the profile anyway.

For each repo you keep public:

- Add a clear **description**
- Add **topics** (e.g. `nextjs`, `stripe`, `fintech`, `payment-gateway`, `react`)
- Add a short **README.md** with screenshots / demo link

---

## ✅ Step 5 — (Optional) Add LinkedIn / X / other links

Open `README.md` in this folder and uncomment the LinkedIn and X badges near the bottom (in the "Let's Connect" section). Replace `YOUR-HANDLE` with your real handles, then:

```powershell
cd C:\Users\onoy2\CascadeProjects\github-profile-tanbin
git add README.md
git commit -m "Add LinkedIn and X links"
git push
```

---

## ✅ Step 6 — (Optional) Self-host stats card for full private-repo numbers

The free `github-readme-stats.vercel.app` API only sees **public** repos, so the stats card under-reports your activity. To make it count private repo stars/commits/languages too, deploy a personal fork to Vercel (5–10 min):

1. Fork https://github.com/anuraghazra/github-readme-stats to your account.
2. Create a Personal Access Token: https://github.com/settings/tokens/new
   - Note: `readme-stats`
   - Expiration: `No expiration` (or 1 year)
   - Scopes: ✅ `repo` ✅ `read:user`
   - Click **Generate token** and copy it.
3. Go to https://vercel.com → Sign in with GitHub → **Add New Project** → import your fork of `github-readme-stats`.
4. Under **Environment Variables**, add `PAT_1` = *(paste the token)*.
5. Click **Deploy**. After deploy you'll get a URL like `https://github-readme-stats-tanbin-cs.vercel.app`.
6. In `README.md`, replace every `https://github-readme-stats.vercel.app/api` with your new Vercel URL. Commit & push.

Now the stats card will pull data from **all** your repos including private ones.

---

## ✅ Step 7 — Verify

Open https://github.com/Tanbin-CS in an **incognito** window (so you see what visitors see) and confirm:

- [ ] Profile picture, name, bio, location, website, email all show under your avatar.
- [ ] Profile README renders with typing banner, About, What I Do, Tech Stack.
- [ ] Stats card, top-languages pie chart, streak, activity graph, and trophies all load (give it ~30s on first visit, the services cache the SVGs).
- [ ] Contribution graph shows green squares (private commits visible).
- [ ] Pinned section shows your real work, not the forked classwork repo.

You're done! 🎉

---

## Troubleshooting

- **Stats card shows "Could not fetch user"** → repo name must be exactly `Tanbin-CS` (case-sensitive on the URL).
- **Widgets don't load / show error icons** → free third-party services occasionally rate-limit; refresh after a minute or two. If `streak-stats` is down, replace its URL with `https://streak-stats.demolab.com/?user=Tanbin-CS&theme=tokyonight&hide_border=true`.
- **Email field rejects `contact@tanbinislam.xyz`** → first add & verify it at https://github.com/settings/emails, then it becomes selectable as a public email.
- **`git push` asks for password** → GitHub no longer accepts account passwords. Use a Personal Access Token: https://github.com/settings/tokens/new (scope: `repo`) and paste it as the password. Or install **GitHub CLI** (`winget install GitHub.cli` then `gh auth login`).
