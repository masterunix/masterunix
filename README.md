<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:7C3AED,100:2563EB&height=180&section=header&text=Vatsal%20Goyal&fontSize=52&fontColor=ffffff&animation=fadeIn&fontAlignY=36" width="100%" alt="Vatsal Goyal">

<img src="https://readme-typing-svg.demolab.com/?font=JetBrains+Mono&size=20&duration=3000&pause=900&color=8B5CF6&center=true&vCenter=true&width=640&lines=Full+Stack+and+AI+Developer;Building+axe+Suite+and+RCIS;Open+to+full-stack+and+AI+roles;Computers+are+still+magic." alt="Full Stack and AI Developer, building axe Suite and RCIS">

[![Portfolio][badge-portfolio]][portfolio] [![LinkedIn][badge-linkedin]][linkedin] [![Email][badge-email]][email] [![Hugging Face][badge-hf]][hf]

</div>

Hey, I'm Vatsal 👋 I build full-stack apps, and lately the AI side of them too: agents, tool calling and MCP servers. Most of my time goes into axe Suite and my studio, RCIS.

> **I'm open to full-stack and AI engineering roles.** Email is the quickest way to reach me: [vatsalgoyal9999@gmail.com][email]

## What I'm working on

### axe Suite

A productivity suite for CS students and engineers, and the project I spend most of my time on. It's seven web apps and a desktop app that share one login, one Postgres database and one AI assistant, axe AI. I build and run all of it myself.

| App | What it does |
| --- | --- |
| [**axe Tasker**](https://tasker.axesuite.tech) | A week-by-week planner with task cards, timers and streaks, notes on a board you can drag around, and a budget with limits, forecasts, and subscriptions and EMIs that log themselves |
| [**axe DSA**](https://dsa.axesuite.tech) | Tracks your LeetCode, Codeforces, HackerRank and AtCoder practice, with ready-made problem packs |
| [**axe Design**](https://design.axesuite.tech) | System design practice. You draw an architecture, a simulator load-tests it, and every submission is kept with its result |
| [**axe Feed**](https://feed.axesuite.tech) | A daily briefing of blogs, newsletters and research papers, laid out like a newspaper front page, with AI summaries and a Research Lab for arXiv |
| [**axe AI**](https://ai.axesuite.tech) | The assistant inside every app, plus an MCP server so Claude, ChatGPT or Cursor can use your data |
| [**axe Home**](https://home.axesuite.tech) and [**axe Tips**](https://tips.axesuite.tech) | Sign-in, dashboard, blog and payments, and the user guides |
| **axe Suite Desktop** | An Electron app for macOS, Windows and Linux. It holds axe AI, axe DSA and axe Tasker, works offline, and lets you chat with Claude Code, Codex or Antigravity inside axe AI |

```mermaid
flowchart LR
    you([You]) -->|sign in once| home[axe Home]
    home -->|one session for every app| apps
    subgraph apps [Apps on axesuite.tech]
        direction TB
        tasker[axe Tasker]
        dsa[axe DSA]
        design[axe Design]
        feed[axe Feed]
    end
    llm([Claude, ChatGPT, Cursor]) -->|MCP + OAuth 2.1| ai[axe AI<br/>assistant + MCP server]
    ai -->|app actions| tasker
    ai --> dsa
    ai --> design
    ai --> feed
    desktop[axe Suite Desktop<br/>Electron + local agents] --> apps
    apps --- db[(Postgres)]
```

- **One login for everything.** Sign in once with Google and every app on `*.axesuite.tech` knows it's you. Sign out of one and you're out of all of them. The desktop app signs in through your browser (RFC 8252 with PKCE).
- **The AI follows the apps' rules.** The apps publish what can be done to their data as typed actions. Their own pages use them, and axe AI calls the same ones with short-lived signed tokens, so none of that logic gets copied into the AI.
- **Bring your own AI.** The MCP server (OAuth 2.1, 40 tools) lets Claude, ChatGPT or Cursor work with your stuff. axe AI runs on LangGraph with whatever model you pick, and connecting OpenRouter takes one click.
- **Works offline.** Tasker, DSA and axe AI open without internet, keep your changes on the device and sync them when you're back, a bit like Google Docs.
- **A load-test simulator.** axe Design pushes traffic through your design and works out the load on each part, p99 latency, availability and the monthly bill. Any design that holds up passes.
- **Feeds for sites that don't have one.** axe Feed falls back to sitemaps, or just watches the page for new links.

Next.js, React, TypeScript, Tailwind, Postgres (Neon), LangChain, LangGraph, MCP, Electron, Vitest, Playwright, Vercel

<sub>The code is private, but every app above is live. Most of my commits go there (about 1,100 so far), which is why my contribution graph looks busier than my public repos.</sub>

### RCIS

[RCIS][rcis] is my web development studio, built around one idea: a website delivered in 10 minutes, with no lock-in, and a real developer who can step in and do the work whenever it's needed. We also build the systems behind websites, like order management, dashboards and internal tools.

- The studio site is Next.js with no CSS framework, and the night sky behind it is a shader I wrote in raw GLSL. Switch to the light theme and the same sky looks like it was printed on paper.
- Clients get their own portal to follow their project and message the studio, and partners get one too. There are no sign-ups. The studio issues every account.
- Our internal tooling is a mix of AI-assisted tools, deterministic tools, helpers, authorisation and much more. It's how we run a website delivery service like no other. From Next.js to WordPress with Elementor, we do it all.

Next.js, TypeScript, WordPress, Elementor, GLSL, Supabase, Python

### PocketLM

How much of a model's worldview comes from its data? I trained eight small models on my MacBook, on posts from politically opposite Reddit communities, and compared what they said. Six are LiquidAI's LFM2-1.2B fine-tuned with LoRA (on MLX and PEFT), and two are 124M GPT-2s trained from scratch with nanoGPT. For those two, a FAISS dedup pass kept both datasets clean and the same size. A small React and Node app runs the models side by side.

[Code][pocketlm] and [weights][pocketlm-hf] are open. PyTorch, MLX, LoRA, FAISS, TypeScript

### FT7

A calm trading desk for [Flattrade](https://flattrade.in), on Mac and Windows: your account, live markets, OpenBB research and an AI assistant in one window. It's free, and you can [download it here](https://www.vatsalgoyal.com/ft7).

- **Markets:** live prices and depth, charts from a day to all time, an option chain with OI and IV, movers, sectors, IPOs and price alerts
- **Ask FT7:** an assistant (Claude, or Google's Antigravity, over the Agent Client Protocol) that reads your account, the news and OpenBB, and explains them. It can prepare an order card, but never send one
- **Pipelines:** AI agents and data steps wired together on a canvas. A pipeline can watch a price or the news and run by itself when something happens
- **Your own screens:** dashboards of cards you arrange, extensions, tabs, profiles and a vim mode
- **Safe by design:** every order is a card with the exact request and the money at risk, and only a click on Place sends it. Read-only mode turns all of that off at once

Python, OpenBB and the assistant's tools ship inside the app, and it updates itself from [its releases](https://github.com/masterunix/ft7/releases). Electron, Python, OpenBB, Agent Client Protocol

### Gleck (in development)

My personal AI agent, still in the works. The idea is that it keeps my resumes and portfolio up to date, hunts for jobs, sends mail and helps with research, all running locally. LangGraph, LangChain and MCP. I'm building it on GitLab for now and releases will land in [the GitHub repo][gleck].

### SkyKeys

[SkyKeys][skykeys] turns the iPhone you already have into a keypad for your Mac: keys, wheels, sliders and a trackpad, with profiles that switch with the app you're using. It's three apps that talk to each other:

- **SkyKeys Console**, the Mac app: you build pages of keys there, and it runs them. It's notarized and free to download
- **SkyKeys for iPhone** (iOS 15 and later): what you press. It's coming to the App Store, free with an optional one-time upgrade
- **SkyKeys Legacy**, for older iPhones on iOS 7 to 14, all the way back to the iPhone 4, written in Objective-C

The phone and the Mac connect over a cable, Wi-Fi and Bluetooth at once and fail over between them. Pairing uses a code confirmed on both screens, and the link is encrypted. There are ready-made profiles for Photoshop, Premiere, Final Cut, Figma, Ableton, OBS and Xcode, haptics that feel like a real device, and Live Activities on the Lock Screen. No account, no analytics and no tracking. Swift, SwiftUI, UIKit, Objective-C

<details>
<summary><b>Other stuff I've built</b></summary>

- **[GlobalFreight AI][globalfreight]**: built solo for a company-wide AI hackathon at Pratham Software (Intellithon, AI-Fortnight 2026), where it cleared all four rounds. A logistics platform that goes from a RAG policy assistant up to Planner, Executor and Auditor agents running the network through an MCP server, under hard safety rules. Flask, LangGraph, ChromaDB, Next.js 16.
- **[vatsalgoyal.com][portfolio]**: my portfolio. Glass hexagons over a single WebGL shader, no animation libraries. [Source][portfolio-src]
- **[JobNest][jobnest]**: a job portal I built during my internship at Xebia. MERN, JWT auth, Stripe and Razorpay, Socket.io.
- **[450 House of Sourdough][450]**: client work for a bakery. The storefront, plus a Flask and SQLite system for orders, subscriptions and B2B accounts ([source][450-backend]).
- **AxeServer**: an old PC I turned into a 24/7 Ubuntu server on Tailscale. It's where I test agents like Gleck.
- **[AshaKiran][ashakiran]**: the website for Asha Kiran Sanstha, an NGO that supports cancer patients and their families. Next.js and plain CSS, prerendered, with a contact form that emails the NGO through Resend.
- Smaller things: [movie.fy][moviefy] (Flutter), [Flapper][flapper] (a Flappy Bird-style game I packaged for iOS with Capacitor) and a [VS Code setup][vscode-dsa] that runs DSA code in seven languages with one shortcut.

</details>

## Experience

- **Full-stack development intern**, [Pratham Software (PSI)][psi] · Jan to Aug 2026. Worked on an internal application using the PERN stack (PostgreSQL, Express, React and Node).
- **IT consultant**, 450 House of Sourdough · Jun to Nov 2025. Built and deployed the bakery's web platform: online orders, payments and inventory.
- **Full-stack intern**, Xebia · Jun to Jul 2025. Built JobNest.
- **Part-time web developer**, Digispheres · Jul 2023 to Jul 2024. Built and deployed websites for clients.

**Education:** B.Tech in Computer Science and Engineering (full-stack development specialization) · 2022 to 2026

## Achievements and certifications

- **Oracle Cloud certifications (2025):** Generative AI Professional, AI Vector Search, AI Foundations, Data Platform Foundations and OCI Foundations
- **Smart India Hackathon:** 7th place in the inter-college competition
- **College coding contests:** 1st place in Code-O-Mania and Algo vs Logic

## Tools I use

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://skillicons.dev/icons?i=ts%2Cjs%2Cpy%2Ccpp%2Cswift%2Creact%2Cnextjs%2Ctailwind%2Cnodejs%2Cexpress%2Cflask%2Cvite%2Cpostgres%2Csupabase%2Cmongodb%2Csqlite%2Cpytorch%2Celectron%2Cflutter%2Caws%2Cvercel%2Cdocker%2Cgithubactions%2Clinux%2Cbash%2Cgit%2Clatex&theme=dark&perline=14">
  <img alt="TypeScript, JavaScript, Python, C++, Swift, React, Next.js, Tailwind CSS, Node.js, Express, Flask, Vite, PostgreSQL, Supabase, MongoDB, SQLite, PyTorch, Electron, Flutter, AWS, Vercel, Docker, GitHub Actions, Linux, Bash, Git and LaTeX" src="https://skillicons.dev/icons?i=ts%2Cjs%2Cpy%2Ccpp%2Cswift%2Creact%2Cnextjs%2Ctailwind%2Cnodejs%2Cexpress%2Cflask%2Cvite%2Cpostgres%2Csupabase%2Cmongodb%2Csqlite%2Cpytorch%2Celectron%2Cflutter%2Caws%2Cvercel%2Cdocker%2Cgithubactions%2Clinux%2Cbash%2Cgit%2Clatex&theme=light&perline=14">
</picture>

Also: LangChain, LangGraph, MCP, RAG, MLX, LoRA, FAISS, ChromaDB, OpenBB, WebGL and GLSL, Radix UI, Tiptap, React Flow, SwiftUI, UIKit, Objective-C, Vitest, Playwright, Tailscale and the Agent Client Protocol

## GitHub activity

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://streak-stats.demolab.com?user=masterunix&theme=tokyonight&hide_border=true">
    <img alt="GitHub contribution streak for masterunix" src="https://streak-stats.demolab.com?user=masterunix&hide_border=true">
  </picture>
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/masterunix/masterunix/output/github-snake-dark.svg">
    <img alt="A snake eating my contribution graph" src="https://raw.githubusercontent.com/masterunix/masterunix/output/github-snake.svg">
  </picture>
</p>

---

Thanks for stopping by! If you're hiring, or want to build something together, [email me][email] or find me on [LinkedIn][linkedin].

> "Just do it."

<div align="center">

<img src="https://komarev.com/ghpvc/?username=masterunix&label=profile+views&color=8b5cf6&style=flat-square" alt="Profile views">

<sub>Last updated 15 Nov 2026 · v3.3</sub>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:7C3AED,100:2563EB&height=110&section=footer" width="100%" alt="">

</div>

[portfolio]: https://www.vatsalgoyal.com
[linkedin]: https://www.linkedin.com/in/vatsalgoyal93
[email]: mailto:vatsalgoyal9999@gmail.com
[hf]: https://huggingface.co/axe-net
[rcis]: https://rcis-systems.vercel.app
[pocketlm]: https://github.com/masterunix/PocketLM
[pocketlm-hf]: https://huggingface.co/axe-net/PocketLM
[gleck]: https://github.com/masterunix/gleck
[skykeys]: https://www.projectskykeys.com
[ashakiran]: https://www.ashakiransanstha.org
[globalfreight]: https://github.com/masterunix/FOURTH-AGENT
[portfolio-src]: https://github.com/masterunix/portfolio-v2
[jobnest]: https://github.com/masterunix/JobNest-v1
[450]: https://450-hos-static.vercel.app
[450-backend]: https://github.com/masterunix/450Backend
[moviefy]: https://github.com/masterunix/Fluttter-Movie-App
[flapper]: https://github.com/masterunix/flapper
[vscode-dsa]: https://github.com/masterunix/VS-Code-DSA-Setup
[psi]: https://www.thepsi.com

[badge-portfolio]: https://img.shields.io/badge/vatsalgoyal.com-7C3AED?style=flat-square&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjZmZmIiBzdHJva2Utd2lkdGg9IjIiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCI+PGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iMTAiLz48cGF0aCBkPSJNMTIgMmExNC41IDE0LjUgMCAwIDAgMCAyMCAxNC41IDE0LjUgMCAwIDAgMC0yMCIvPjxwYXRoIGQ9Ik0yIDEyaDIwIi8+PC9zdmc+
[badge-linkedin]: https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iI2ZmZiIgZD0iTTIwLjQ0NyAyMC40NTJoLTMuNTU0di01LjU2OWMwLTEuMzI4LS4wMjctMy4wMzctMS44NTItMy4wMzctMS44NTMgMC0yLjEzNiAxLjQ0NS0yLjEzNiAyLjkzOXY1LjY2N0g5LjM1MVY5aDMuNDE0djEuNTYxaC4wNDZjLjQ3Ny0uOSAxLjYzNy0xLjg1IDMuMzctMS44NSAzLjYwMSAwIDQuMjY3IDIuMzcgNC4yNjcgNS40NTV2Ni4yODZ6TTUuMzM3IDcuNDMzYTIuMDYyIDIuMDYyIDAgMSAxIDAtNC4xMjUgMi4wNjIgMi4wNjIgMCAwIDEgMCA0LjEyNXpNNy4xMTkgMjAuNDUySDMuNTU1VjloMy41NjR2MTEuNDUyek0yMi4yMjUgMEgxLjc3MUMuNzkyIDAgMCAuNzc0IDAgMS43Mjl2MjAuNTQyQzAgMjMuMjI3Ljc5MiAyNCAxLjc3MSAyNGgyMC40NTFDMjMuMiAyNCAyNCAyMy4yMjcgMjQgMjIuMjcxVjEuNzI5QzI0IC43NzQgMjMuMiAwIDIyLjIyMiAwaC4wMDN6Ii8+PC9zdmc+
[badge-email]: https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white
[badge-hf]: https://img.shields.io/badge/Hugging_Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black
