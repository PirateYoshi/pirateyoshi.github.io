# Home Calendar: OAuth consent-screen pages

A static site (plain HTML and CSS, no JavaScript, no external requests) that
gives the Google OAuth consent screen the homepage, privacy policy and terms
URLs it needs before the app can be switched to production.

## Contents

| File | Purpose |
| --- | --- |
| `index.html` | Homepage |
| `privacy.html` | Privacy policy |
| `terms.html` | Terms of use |
| `assets/simple.css` | [Simple.css](https://simplecss.org) v2.3.3, unmodified |
| `assets/LICENSE-simple.css.txt` | Simple.css MIT licence (keep it) |
| `assets/site.css` | Small overrides: always-dark palette, footer spacing |

`README.md` itself does not need to be uploaded.

## 1. Replace the placeholders

| Placeholder | Where | Replace with |
| --- | --- | --- |
| `USERNAME` | This README only | Your GitHub username |

Check that none are left:

```bash
grep -rn 'USERNAME' --include='*.html' .   # should print nothing
```

The pages contain no names, email addresses, IP addresses, serial numbers,
device or network details, the project's real name, calendar addresses or tokens. Keep it that way:
these pages are public. Contact goes through the repository's Issues tab
(leave Issues enabled), so no email address appears on the site. The support
email on the consent screen is shown by Google, not by these pages.

The site calls the app **Home Calendar**. Set the consent screen's
**App name** (Branding page) to the same name so the two match.

## 2. Upload to GitHub Pages

1. On GitHub, create a new **public** repository named exactly
   `USERNAME.github.io` (your username, lower case).
2. Upload the contents of this folder (`index.html`, `privacy.html`,
   `terms.html` and the `assets/` folder) to the **root** of the repository,
   on the `main` branch. Use **Add file › Upload files**, or `git push`.
3. In the repository, open **Settings › Pages**. Under **Build and
   deployment**, set **Source** to **Deploy from a branch**, branch `main`,
   folder `/ (root)`, and save.
4. Wait a minute or two, then open `https://USERNAME.github.io/` and check
   the three pages load.

## 3. Fill in Google Cloud

Google Cloud console › **Google Auth Platform › Branding**:

| Field | Value |
| --- | --- |
| Application home page | `https://USERNAME.github.io/` |
| Application privacy policy link | `https://USERNAME.github.io/privacy.html` |
| Application terms of service link | `https://USERNAME.github.io/terms.html` |
| Authorized domains | `USERNAME.github.io` |

Save, then go to **Google Auth Platform › Audience** and choose
**Publish app** to move it from Testing to In production. The app stays
unverified, which is fine for a handful of users: Google shows an
"unverified app" warning on sign-in that you click through once.

## Updating the policy

If the app starts using more Google data, update `privacy.html` (and the
"Last updated" date) before you change the scopes on the consent screen.
