# Five a Day English Academy — Website

---

## 1. Introduction

This is the official website of **Five a Day English Academy**, an innovative English academy in Albacete (Spain) founded by two bilingual teachers. The site presents the academy's methodology, team, philosophy, and provides a contact form for families and students.

The website is live at **[fiveaday.netlify.app](https://fiveaday.netlify.app)** and also accessible via a custom domain purchased through Wix. It is built with modern web technology (React + Vite + Tailwind CSS) and deployed automatically through Netlify whenever changes are pushed to the `main` branch on GitHub.

The project has two files designed to be the only ones you ever need to touch for day-to-day maintenance:

- **`src/data.js`** — all the content (texts, phone numbers, images, Q&As, etc.)
- **`src/styles.css`** — all the visual styles (colors, fonts, shadows, animations)

---

## 2. Infrastructure & Services

The Five a Day website and supporting services are hosted across several platforms. Here's the ecosystem:

### Code Repository

- **[GitHub](https://github.com)** — Hosts all the source code for this website. Every change you push here triggers an automatic deployment to the live site via Netlify. This is where developers work and where you manage git version control.

### Frontend Hosting

- **[Netlify](https://netlify.com)** — Hosts the static website (HTML, CSS, JavaScript files). It's free, fast, and automatically rebuilds and deploys whenever you push code to GitHub. The site is served from `fiveaday.netlify.app` and your custom domain points here.

### Domain Management

- **[Squarespace Domains](https://www.squarespace.com)** — Where the custom domains are registered and managed (fiveaday.com and others). These domains are pointed to Netlify using DNS records. When you visit `fiveaday.com`, your browser's DNS lookup routes you to Netlify's servers, which serve the actual website.

### Google Cloud Platform (Infrastructure)

- **[Google Cloud Platform (GCP)](https://cloud.google.com)** — Hosts more complex backend services and infrastructure. Currently being set up for future needs beyond the static website. Will run Docker containers with four services in Django for advanced functionality like form processing, authentication, and data storage. For now, the simple static website doesn't use GCP, but it's the foundation for scaling the project.

### Email & Authentication

- **[Gmail & Google Account](https://mail.google.com)** — The centerpiece of all login and authentication systems. The Google account associated with `jhernandez@allot.com` is the main administrative account for:
  - Google Cloud Platform access
  - Netlify account management
  - GitHub organization (if team-based)
  - Email for service notifications and password resets
  - OAuth provider for future user login systems

### Live Domains

- **[fiveaday.com](https://fiveaday.com)** — The production domain. This is the public-facing URL where students and families visit the website. It's fully deployed and live.
- **example.com** — A second custom domain registered (currently a placeholder). This will be replaced with the actual domain name soon. It will point to the same Netlify hosting as fiveaday.com, allowing traffic from both domains to reach the same website.

### **How It All Connects**

```
You push code → GitHub → Netlify detects change → Netlify builds & deploys
                                                    ↓
                          fiveaday.com (DNS points here)
                                    ↓
                          Netlify servers serve the site
```

When someone visits `fiveaday.com`:
1. Their browser asks: "Where is fiveaday.com?"
2. DNS (Squarespace) answers: "Go to Netlify's servers"
3. Netlify serves the website from the latest code on GitHub

For future backend features (forms that save to a database, user accounts, etc.), GCP's Docker services will handle the logic, and the frontend (this React app) will communicate with those services via API calls.

---

## 3. Index

1. [Introduction](#1-introduction)
2. [Infrastructure & Services](#2-infrastructure--services)
3. [Index](#3-index)
4. [How to Change Things](#4-how-to-change-things)
   - [Editing content on GitHub (data.js)](#editing-content-on-github-datajs)
   - [Editing styles on GitHub (styles.css)](#editing-styles-on-github-stylescss)
   - [Worked example](#worked-example)
   - [How data.js works](#how-datajs-works)
   - [How styles.css works](#how-stylescss-works)
5. [Development](#5-development)
   - [Prerequisites](#prerequisites)
   - [Running the site locally](#running-the-site-locally)
   - [How Netlify works](#how-netlify-works)
   - [Understanding Git and GitHub](#understanding-git-and-github--versioning-and-change-history)
   - [How to update the live site with Git](#how-to-update-the-live-site-with-git)
6. [Project Structure](#6-project-structure)
   - [File tree](#file-tree)
   - [What each file does](#what-each-file-does)
   - [npm commands](#npm-commands)
7. [Images & Media](#7-images--media)
8. [SEO — being found on Google](#8-seo--being-found-on-google)
   - [Changing a page title or description](#changing-a-page-title-or-description)
   - [If the domain ever changes](#if-the-domain-ever-changes)
   - [The sharing image](#the-sharing-image)
   - [Things only you can do (not in the code)](#things-only-you-can-do-not-in-the-code)
9. [Quick Reference](#9-quick-reference)
10. [Troubleshooting](#10-troubleshooting)
11. [Tech Stack](#11-tech-stack)

---

## 4. How to Change Things

This section is for **non-technical people** who want to make small updates — changing a phone number, editing a text, updating a color — directly in GitHub without running anything on a computer.

> **Important:** Any change you save in GitHub is automatically published to the live website within 1–2 minutes via Netlify. There is no separate "publish" step.

---

### Editing content on GitHub (data.js)

Follow these steps to change any text, link, phone number, address, or similar content:

1. **Go to the repository on GitHub** (the page you're reading this from, or ask the developer for the link).

2. **Navigate to the file** `src/data.js`. You can click through the folders: `src` → `data.js`.

3. **Click the pencil icon** (Edit this file) in the top-right corner of the file view. It looks like ✏️.

4. **Find the text you want to change.** Use `Ctrl+F` (Windows) or `Cmd+F` (Mac) in your browser to search for the word you're looking for. For example, search for `613 48 11 41` to find the phone number.

5. **Make your change.** Click on the line, delete the old text, and type the new text. Be careful to keep the surrounding quote marks (`"`) in place — only change what's between them.

6. **Save your change.** Scroll down to the bottom of the page. You'll see a section called "Commit changes". Write a short description of what you changed (e.g. `Update phone number`) and click the green **"Commit changes"** button.

7. **Wait 1–2 minutes.** Netlify will automatically detect the change and rebuild the website. Your update will appear on [fiveaday.netlify.app](https://fiveaday.netlify.app).

---

### Editing styles on GitHub (styles.css)

Follow the same steps as above, but navigate to `src/styles.css` instead of `src/data.js`.

This file controls colors, fonts, and visual effects. The most common changes are colors:

1. Find the color you want to change. For example, search for `primary` to find the main purple color (`#8b5cd4`).
2. Change the hex color code (the `#xxxxxx` value) to a new one. You can use any color picker online to get hex codes — for example [coolors.co](https://coolors.co) or [htmlcolorcodes.com](https://htmlcolorcodes.com).
3. Commit the change as described above.

---

### Worked example

**Scenario:** The phone number has changed from `613 48 11 41` to `699 00 11 22`.

1. Open `src/data.js` in GitHub.
2. Search for `613 48 11 41`.
3. Find this line:

   ```js
   phone: "613 48 11 41",
   ```

4. Change it to:

   ```js
   phone: "699 00 11 22",
   ```

5. Also update the WhatsApp link right above it:

   ```js
   whatsapp: "https://wa.me/34699001122",
   ```

   (The WhatsApp URL uses the number without spaces, with `34` at the front for Spain's country code.)
6. Scroll down, write a note like `Update phone number`, and click **Commit changes**.
7. In 1–2 minutes the new number appears everywhere on the site automatically.

---

### How data.js works

Think of `data.js` as a **big contact book / content notebook** for the website. Everything the website needs to display is written down here once, and all the pages read from this file.

The file is organized into sections (called "exports"), each covering a different part of the site:

| Section | What it controls |
|---|---|
| `siteConfig` | Academy name, email, phone, WhatsApp link, address, opening hours, social media links, map links |
| `navigation` | The menu items in the navigation bar |
| `heroContent` | The main heading, description, and button on the home page |
| `metodologiaHome` | The four content blocks on the home page methodology preview |
| `foundersPage` | Section heading labels on the "Quiénes somos" page |
| `founders` | The two founders' names, quotes, biographies, and experience timelines |
| `metodologiaPage` | The full methodology page: class descriptions, the 5 routines, Fun Fridays |
| `odsPage` | The ODS / Sustainable Development page content |
| `sobreAcademiaPage` | The "Sobre la academia" page: intro, differences, gallery images, testimonials, section titles |
| `faqPage` | The FAQ page questions and answers |
| `contactForm` | The contact form field labels, success message, and submit button text |
| `whatsappPopup` | The text inside the WhatsApp popup that appears at the bottom-right |
| `legalPage` | The full "Aviso Legal" (legal notice) text |

**The rule is simple:** if you see text on the website that you want to change, search for it in `data.js` and change it there.

Image paths look like `"/images/home_1.jpg"`. These refer to files inside the `public/images/` folder. To change an image, upload a new file there and update the path in `data.js`.

---

### How styles.css works

Think of `styles.css` as a **palette and design manual** for the website. It defines the colors, fonts, and visual effects used everywhere.

The file is organized into numbered sections with plain-language comments explaining each one.

**Colors** are defined as variables with a name and a hex code:
```css
--color-primary: #8b5cd4;   /* main bright purple */
```
Change the hex code and that color updates across the whole site.

**Fonts** are defined similarly:
```css
--font-title: 'Imprima', sans-serif;
```
Change `'Imprima'` to any Google Font name and update the font link in `index.html` accordingly.

**Animations** (the floating blobs on the hero section) and other visual effects are defined further down in the file with descriptive names like `.animate-blob` and `.popup-visible`.

The key point: **you do not need to touch any component file (`.jsx`) to change colors, fonts, or shadows.** All visual customization lives in `styles.css`.

---

## 5. Development

This section is for **developers** who want to work on the project locally. It assumes you're comfortable with a terminal but may be new to this specific project's stack (React, Vite, Tailwind) and to Git.

---

### Prerequisites

Install the following tools once on your machine:

1. **Node.js** (version 18 or higher) — [nodejs.org](https://nodejs.org). This is the runtime that powers the development server and build tools. Download the LTS version and run the installer.

2. **Git** — [git-scm.com](https://git-scm.com). Version control tool used to sync changes with GitHub. Download and install with default settings.

3. A **code editor** — [Visual Studio Code](https://code.visualstudio.com) is recommended. It has great support for React and Tailwind.

---

### Running the site locally

Open a terminal (Command Prompt, PowerShell, or the VS Code terminal) and run these commands one by one:

```bash
# 1. Download the project from GitHub (only needed the first time)
git clone https://github.com/YOUR_USERNAME/five-a-day-frontend.git

# 2. Enter the project folder
cd five-a-day-frontend

# 3. Install all dependencies (only needed the first time, or after package.json changes)
npm install

# 4. Start the development server
npm run dev
```

After step 4 you'll see a message like:

```
  ➜  Local:   http://localhost:6001/
```

Open that URL in your browser. The site is now running locally. **Any file you save will instantly update in the browser** — no refresh needed.

To stop the server, press `Ctrl+C` in the terminal.

---

### How Netlify works

[Netlify](https://netlify.com) is the hosting platform that serves the live website. Here's how it fits into the workflow:

- The code lives on **GitHub** (a code storage and version control platform).
- Netlify is connected to the GitHub repository and **watches the `main` branch** for changes.
- Every time new code is pushed to `main`, Netlify automatically:
  1. Pulls the latest code.
  2. Runs `npm run build` to compile the React app into plain HTML/CSS/JS files.
  3. Deploys those files to its global server network.
  4. The live site at **[fiveaday.netlify.app](https://fiveaday.netlify.app)** updates within 1–2 minutes.

The **custom domain** (purchased via Wix) is pointed at Netlify's servers using DNS records — this is already configured and you don't need to touch it. Both the Netlify subdomain and the custom Wix domain point to the same site.

The `netlify.toml` file in the project root contains Netlify's build configuration. You should not need to edit it.

---

### Understanding Git and GitHub — Versioning and change history

Git and GitHub sound technical, but the idea is simple: they work like **"Version History" on Google Docs**, but for code files. Instead of typing in a document and saving over the old version, Git lets you save a complete snapshot of your entire project at each moment, with a note about what changed.

#### The core concepts

**Git** (on your computer) keeps track of every change you make. **GitHub** (on the internet) is where you store and share those changes.

Think of it like this:

- **Your local copy** = the code on your computer that you're editing right now
- **GitHub** = a backup of your code on the internet that the whole team can see
- **Commits** = snapshots of your code with a note explaining what changed
- **Pull** = download the latest version from GitHub to your computer
- **Push** = upload your changes from your computer back to GitHub

#### How changes are preserved: The commit history

Every time you make a change and commit it, Git saves:

- **What changed** — the exact lines you added, deleted, or modified
- **When it changed** — the timestamp
- **Who changed it** — your name
- **Why it changed** — the message you wrote (e.g. "Update phone number")

This creates a **full history** of the project. You can go back and see:

- What the site looked like a month ago
- Who made a specific change
- Why a change was made (from the commit message)
- Undo mistakes by reverting to an earlier version

**Example:** Imagine you changed the phone number and broke something. You can look at the commit history, see exactly what changed, and revert that one change without losing all the other work done since then.

#### Branches: Working on multiple things at once

Sometimes you might want to work on something without affecting the live website. Git lets you create a **branch** — a parallel version of the code where you can make changes safely.

Think of it like this:

- The `main` branch is the official, live version (what users see)
- You create a test branch and make experimental changes
- If it works, you merge it back into `main`
- If it doesn't work, you delete the test branch and `main` is unaffected

For this project, you'll mostly work directly on `main` because it's small and simple, but branches are there if you need them later.

#### The workflow: Pull → Edit → Commit → Push

Here's what happens each time you make a change:

1. **Pull** — Download the latest version from GitHub to make sure you have everyone else's changes

   ```bash
   git pull
   ```

2. **Edit** — Make your changes using your code editor

   ```txt
   Edit src/data.js, save it normally
   ```

3. **Check what changed** — See which files you modified

   ```bash
   git status
   ```

4. **Stage your changes** — Tell Git "I want to save these files"

   ```bash
   git add src/data.js
   ```

5. **Commit** — Take a snapshot with a message explaining what you did

   ```bash
   git commit -m "Update phone number from 613 to 699"
   ```

6. **Push** — Upload your snapshot to GitHub so the team can see it

   ```bash
   git push
   ```

Once you push, Netlify sees the change and redeploys the website automatically.

#### Common scenarios explained

##### Scenario: You change the phone number

1. You edit `src/data.js` — change `"613 48 11 41"` to `"699 00 11 22"`
2. You run `git add src/data.js` — "I want to save this change"
3. You run `git commit -m "Update phone number"` — "Take a snapshot and note what I did"
4. You run `git push` — "Upload to GitHub"
5. Netlify sees the commit, rebuilds, and the live site updates

Now the full history shows: who changed it, when, and why. If someone asks "when did we change the number?", you can look at the commit history and see exactly.

##### Scenario: You break something and want to undo it

1. You pushed a bad change, and the site broke
2. You look at the commit history on GitHub
3. You find the bad commit and click "Revert" (or run `git revert COMMIT_ID`)
4. The change is undone, the site works again
5. Everyone can see in the history: "This change broke the site, so we reverted it"

##### Scenario: Two people edit the same file

1. You pull the latest code: phone number is `"613 48 11 41"`
2. Your teammate also pulls the latest code
3. You change it to `"699 00 11 22"` and push
4. Your teammate changes it to `"555 12 34 56"` and tries to push
5. Git says "Wait, the file changed since you last pulled. Pull first and merge."
6. Your teammate pulls, Git shows both changes, they pick one (or combine both)
7. Both changes are now recorded in history

This happens automatically — Git is smart enough to merge changes in most cases.

#### What gets saved and what doesn't

Git saves:

- Text files (`data.js`, CSS files, components, images)
- The history of every change
- Commit messages and metadata

Git **does not** save:

- `node_modules/` folder (too big; everyone regenerates it with `npm install`)
- Temporary files or editor settings
- Secrets or passwords (you'd store those separately)

This is controlled by a file called `.gitignore` which lists what to skip.

---

### How to update the live site with Git

This is the standard workflow for making any code change:

**Step 1 — Make sure your local copy is up to date**

```bash
git pull
```

This downloads any changes others have made since your last sync.

**Step 2 — Make your changes**
Edit files using your code editor. Save them normally.

**Step 3 — Check what you changed**

```bash
git status
```

This lists every file you've modified. Green = staged (ready to commit). Red = modified but not yet staged.

**Step 4 — Stage your changes**

```bash
git add src/data.js
```

Replace `src/data.js` with whatever files you changed. To stage everything at once:

```bash
git add .
```

Use `git add .` only when you're confident you haven't accidentally changed unrelated files.

**Step 5 — Commit with a message**

```bash
git commit -m "Update phone number and opening hours"
```

The message in quotes should describe what you changed, for your own records and for the team.

**Step 6 — Push to GitHub**

```bash
git push
```

This uploads your commit to GitHub. Netlify will see it and start rebuilding the live site.

> **Tip:** Always pull before you push (`git pull` first). If someone else has pushed changes since your last pull, Git will warn you and you'll need to merge first.

---

## 6. Project Structure

### File tree

```
five-a-day-frontend/
│
├── public/
│   └── images/              ← All images used on the site
│
├── scripts/
│   └── generate-seo.mjs     ← Builds a separate HTML page per address for Google
│
├── src/
│   ├── main.jsx             ← Entry point — mounts the React app
│   ├── App.jsx              ← Router setup + image preloading
│   ├── seo.js               ← All page titles, descriptions & Google data
│   ├── index.css            ← Technical entry for Tailwind (don't edit)
│   ├── styles.css           ← ✏️  All custom styles — EDIT THIS
│   ├── data.js              ← ✏️  All content & config — EDIT THIS
│   │
│   ├── components/
│   │   ├── Layout.jsx       ← Wraps every page: Navbar + Footer + Popup
│   │   ├── Navbar.jsx       ← Top contact bar + main navigation
│   │   ├── Logo.jsx         ← SVG logo (the five coloured leaves)
│   │   ├── Footer.jsx       ← Bottom bar with copyright and legal link
│   │   ├── Reveal.jsx       ← Scroll-triggered fade-in animation wrapper
│   │   ├── ScrollToTop.jsx  ← Resets scroll position on page navigation
│   │   ├── WhatsAppPopup.jsx← Timed popup in the bottom-right corner
│   │   ├── ImageGallery.jsx ← Carousel + lightbox for the photo gallery
│   │   └── ContactSection.jsx ← Purple contact form used on all pages
│   │
│   ├── pages/
│   │   ├── Home.jsx                ← Home page
│   │   ├── QuienesSomos.jsx        ← "Quiénes somos" — founder profiles
│   │   ├── NuestraMetodologia.jsx  ← "Nuestra metodología" — the 5 routines
│   │   ├── LosODS.jsx              ← "Los ODS" — sustainability education
│   │   ├── SobreLaAcademia.jsx     ← "Sobre la academia" — gallery, testimonials, map
│   │   ├── PreguntasFrecuentes.jsx ← FAQ page
│   │   └── AvisoLegal.jsx          ← Legal notice page
│   │
│   └── hooks/
│       └── usePreloadImages.js     ← Preloads images in the background on startup
│
├── index.html               ← HTML shell — also contains the Google Fonts link
├── vite.config.js           ← Vite build tool configuration
├── netlify.toml             ← Netlify deployment configuration
├── package.json             ← Project dependencies and npm scripts
└── eslint.config.js         ← Code quality rules for the editor
```

---

### What each file does

**`src/data.js`** — The single source of truth for all website content. Every text, image path, link, and configurable value lives here. Components import from this file and render whatever they find. Nothing else needs to change when content changes.

**`src/styles.css`** — All custom CSS: the color palette, font definitions, animations, drop shadows, gradient effects, and the WhatsApp popup transition. Tailwind's utility classes handle layout and spacing; this file handles brand-specific visual identity.

**`src/index.css`** — Only two lines: it imports Tailwind (the utility CSS framework) and then imports `styles.css`. You never need to edit this file.

**`src/main.jsx`** — The JavaScript entry point. It mounts the React application onto the HTML page. You never need to edit this file.

**`src/App.jsx`** — Sets up page routing (which URL shows which page) and starts the image preloading process in the background.

**`src/components/Layout.jsx`** — The frame around every page. It renders the Navbar at the top, the Footer at the bottom, and passes the current page content through in the middle. The WhatsApp popup is also mounted here so it appears on every page.

**`src/components/Reveal.jsx`** — A reusable wrapper that makes its children fade in and slide up when they scroll into view. Used throughout the site to create the animated reveal effects.

**`src/components/ImageGallery.jsx`** — The photo carousel on the "Sobre la academia" page. Supports clicking the center image to open a full-screen lightbox, and keyboard navigation (arrow keys, Escape).

**`src/components/ContactSection.jsx`** — The purple contact form that appears at the bottom of every page. Reads all its labels, fields, and messages from `data.js`.

**`src/seo.js`** — The single source of truth for everything Google sees: the title and description of each page, the web address of the site, and the structured business information (address, phone, opening hours, map position) that makes the academy eligible to appear in Google's local map results. See [section 8](#8-seo--being-found-on-google).

**`scripts/generate-seo.mjs`** — Runs automatically after every build. It creates a real, separate HTML file for each page of the site so that Google sees seven distinct pages instead of seven copies of the same one, and writes `sitemap.xml` and `robots.txt`. You never need to edit this file.

**`src/hooks/useSeo.js`** — Keeps the browser tab title and the official page address correct while a visitor clicks around inside the site, since the page never fully reloads.

**`src/hooks/usePreloadImages.js`** — Silently preloads all images in the background so there's no delay when users navigate between pages. The download deliberately waits until the browser is idle, so it never slows down the first screen a visitor sees (Google measures that speed and uses it for ranking).

---

### npm commands

Run these from the project root directory in your terminal:

| Command | What it does |
|---|---|
| `npm install` | Downloads and installs all project dependencies into `node_modules/`. Run this once after cloning, and again whenever `package.json` changes (e.g. after someone adds a library). |
| `npm run dev` | Starts the local development server at `http://localhost:6001`. Changes to any file are instantly reflected in the browser without a page refresh (Hot Module Replacement). Use this while working. |
| `npm run build` | Compiles the entire React app into optimized static files (HTML, CSS, JS) in the `dist/` folder. This is what Netlify runs automatically before deploying. You rarely need to run this manually. |
| `npm run preview` | Serves the compiled `dist/` folder locally, so you can test exactly what Netlify will deploy. Run `npm run build` first. |
| `npm run lint` | Checks the code for style errors and potential bugs using ESLint. Run this before pushing if you want to catch obvious issues early. |

---

## 7. Images & Media

All images are stored in the **`public/images/`** folder. They are referenced in `data.js` with paths like `"/images/home_1.jpg"`.

### How to add or replace an image

1. **Prepare your image file.** Use JPG for photos, PNG for logos and images with transparency. Resize large photos to a maximum of 1400–1600px wide before uploading to keep the site fast.

2. **Upload the file** to `public/images/` in the GitHub repository:
   - Navigate to `public/images/` in GitHub.
   - Click **"Add file"** → **"Upload files"**.
   - Drag your file in and commit.

3. **Update the reference in `data.js`** if you're replacing an existing image with a new filename. Find the old filename (e.g. `"/images/home_1.jpg"`) and change it to the new one.

If you're replacing an image with the **same filename**, just upload the new file with the same name — no changes to `data.js` needed. GitHub will overwrite the old file.

### Image naming convention

Use lowercase letters, numbers, and underscores. Examples:
- `home_1.jpg`, `home_2.jpg` — hero and methodology block images
- `metodologia_1.jpg` through `metodologia_6.jpg` — routine and Fun Fridays images
- `about_galery_1.jpg` through `about_galery_11.jpg` — gallery images
- `penelope.webp`, `silvia.webp` — founder portrait photos
- `logo_transparent.png` — main logo with transparent background
- `logo_contact.png` — logo variant used in the contact section

---

## 8. SEO — being found on Google

Everything that controls how the website appears in Google lives in one
file: **`src/seo.js`**. You do not need to touch anything else.

### How it works

A website like ours normally has a problem: every address on the site
(`/faq`, `/quienes-somos`, and so on) is really the *same* HTML file, so
Google saw seven pages that all had the identical title and could not
tell them apart.

To fix this, the build now runs an extra step (`scripts/generate-seo.mjs`)
that creates a genuine, separate HTML file for each page, each with its
own title and description. This happens automatically every time the site
is published — there is nothing to remember.

The same step also generates:

| File | What it does |
| --- | --- |
| `sitemap.xml` | The list of pages we ask Google to index. Submit it once in Google Search Console. |
| `robots.txt` | Tells search engines they are welcome and where the sitemap is. |

### Changing a page title or description

Open `src/seo.js` and edit the `pagesSeo` list. Each page looks like this:

```js
{
  path: "/faq",
  title: "Preguntas frecuentes | Academia de inglés en Albacete",
  description:
    "Horarios, instalaciones, cómo son las clases y cómo inscribirse...",
  priority: "0.7",
},
```

- **`title`** — what people see as the blue clickable line in Google.
  Keep it **under about 60 characters** or Google cuts it off.
- **`description`** — the grey text underneath. Keep it **under about 155
  characters**. It does not affect ranking directly, but a good one makes
  more people click.
- **`path`** — must exactly match the address in `src/App.jsx`.

Save, commit, and the change is live in 1–2 minutes like any other edit.

### If the domain ever changes

Change the single line near the top of `src/seo.js`:

```js
export const SITE_URL = "https://fiveadayenglish.com";
```

Everything else — sitemap, canonical addresses, sharing links — updates
itself from that one value.

### The sharing image

`public/images/og-image.jpg` is the picture that appears when someone
shares a link on WhatsApp, Facebook or Instagram. It must stay
**1200 x 630 pixels**. To change it, replace the file with the same name.

### Things only you can do (not in the code)

The single biggest factor for showing up in the Google map results for
"academia de inglés Albacete" is **not** on this website:

1. **Claim and complete the Google Business Profile** at
   [business.google.com](https://business.google.com). Name, address,
   phone and opening hours must match this site *exactly*.
2. **Ask happy families for Google reviews.** Review count and rating are
   among the strongest local ranking signals that exist.
3. **Submit the sitemap** once at
   [search.google.com/search-console](https://search.google.com/search-console)
   → add `fiveadayenglish.com` → Sitemaps → enter `sitemap.xml`.

---

## 9. Quick Reference

The most common changes and where to make them:

| I want to change... | Edit this |
|---|---|
| Phone number | `siteConfig.phone` and `siteConfig.whatsapp` in `data.js` |
| Email address | `siteConfig.email` in `data.js` |
| Opening hours | `siteConfig.hours.phone` and `siteConfig.hours.inPerson` in `data.js` |
| Physical address | `siteConfig.address` in `data.js` |
| Instagram or Facebook link | `siteConfig.social.instagram` / `.facebook` in `data.js` |
| Main purple color | `--color-primary` in `styles.css` |
| Background yellow color | `--color-accent-yellow` in `styles.css` |
| Body font | `--font-sans` in `styles.css` (+ update Google Fonts link in `index.html`) |
| Home page hero text | `heroContent` in `data.js` |
| Navigation menu items | `navigation` array in `data.js` |
| FAQ questions/answers | `faqPage.questions` in `data.js` |
| Testimonials | `sobreAcademiaPage.testimonials` in `data.js` |
| Contact form fields | `contactForm.fields` in `data.js` |
| Legal notice text | `legalPage.sections` in `data.js` |
| WhatsApp popup text | `whatsappPopup` in `data.js` |
| Gallery photos | `sobreAcademiaPage.gallery` in `data.js` + upload image to `public/images/` |
| Founder biographies | `founders` array in `data.js` |

---

## 10. Troubleshooting

**The site isn't updating after I committed on GitHub**
- Wait 2–3 minutes — Netlify build times vary.
- Go to the [Netlify dashboard](https://app.netlify.com) and check the "Deploys" tab for the project. If the latest deploy shows an error, click on it to read the build log.

**I broke something and the site went blank / shows an error**
- The most common cause is a formatting error in `data.js` — a missing comma, an unmatched quote, or a deleted bracket.
- Open `data.js` and look carefully at the line you last edited. Every text value must be surrounded by `"` characters, and each line (except the last in a section) must end with a `,`.
- In GitHub you can click **History** on the file and revert to an earlier version.

**`npm run dev` fails with "Cannot find module"**
- Run `npm install` first. The `node_modules/` folder (which is not stored in Git) needs to be created on your machine.

**Images are not showing locally**
- Make sure the image file is in `public/images/` (not in `src/`).
- Check the filename matches exactly — file names are case-sensitive on Linux/Mac.

**The Google Maps embed is not showing**
- This sometimes happens when viewing the site over HTTP (not HTTPS) locally. It will work correctly on the live Netlify site.

**`git push` is rejected**
- Someone else pushed changes since your last `git pull`. Run `git pull` to merge their changes, then `git push` again.

---

## 11. Tech Stack

| Technology | Version | Purpose |
|---|---|---|
| [React](https://react.dev) | 19 | UI component library — builds the interactive pages |
| [Vite](https://vite.dev) | 8 | Development server and build tool — extremely fast |
| [Tailwind CSS](https://tailwindcss.com) | 4 | Utility-first CSS framework — handles layout and spacing |
| [React Router](https://reactrouter.com) | 7 | Client-side routing — switching between pages without full reloads |
| [Netlify](https://netlify.com) | — | Hosting and continuous deployment |

The project does **not** use a backend or database. All content is static and lives in `data.js`. The contact form currently has no server integration — form submissions are captured in the browser state only (marked as TODO in the code). Integrating a form backend (e.g. Netlify Forms, Formspree, or a custom API) is a future task.
