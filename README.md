# Hi, I'm Vatsal 👋

I'm a full-stack developer in Jaipur, India. I build products end to end: the Postgres schema, the API, the interface, and lately the AI layer on top (agents, tool calling and MCP servers).

[![Portfolio][badge-portfolio]][portfolio] [![LinkedIn][badge-linkedin]][linkedin] [![Email][badge-email]][email] [![Hugging Face][badge-hf]][hf]

> **Open to full-stack and AI engineering roles.** Email is the fastest way to reach me: [vatsalgoyal9999@gmail.com][email].

## What I'm building: AxeSuite

[AxeSuite][axesuite] is a productivity suite for computer-science students and engineers: seven web apps and a desktop app that share one sign-in, one Postgres database, one AI assistant and one design language. It's a solo project; I design, build and run all of it.

| App | What it does |
| --- | --- |
| [**AxeTasker**](https://tasker.axesuite.tech) | A week-by-week planner: dated task cards with timers and streaks, rich-text notes, templates, and links to items in the other apps |
| [**AxeDSA**](https://dsa.axesuite.tech) | A coding-practice tracker for LeetCode, Codeforces and HackerRank problems, with a store of ready-made problem packs |
| [**Axe Design**](https://design.axesuite.tech) | System-design practice: draw an architecture on a canvas, then a simulator load-tests it against latency, availability and budget targets |
| [**AxeFeed**](https://feed.axesuite.tech) | One calm daily feed of blogs, newsletters and papers. Paste any link and it finds the feed, or watches sites that don't publish one |
| [**AxeAI**](https://ai.axesuite.tech) | AxeBot, the assistant inside the apps, and an MCP server so Claude, ChatGPT or Cursor can work with your AxeSuite data |
| [**Axe Home**](https://home.axesuite.tech) and [**AxeTips**](https://tips.axesuite.tech) | The front door (sign-in for every app, a dashboard, the blog, payments) and the user guides |
| **AxeSuite Desktop** | An Electron app for macOS, Windows and Linux that holds AxeAI, AxeDSA and AxeTasker in one window, works offline, and brings local coding agents (Claude Code, Codex, Antigravity) into AxeAI's chat |

**How it's built**

- **One sign-in for every app.** Google sign-in, handled by Axe Home, starts one session that every `*.axesuite.tech` app shares, and signing out anywhere signs you out everywhere. The desktop app signs in through the system browser (OAuth for native apps, RFC 8252, with PKCE).
- **The AI follows each app's own rules.** Every app publishes what can be done to its data as named actions typed with JSON Schema. The app's pages and the AI call the same actions; AxeAI calls them on a user's behalf with short-lived, Ed25519-signed service tokens, so no business logic is copied into the AI service.
- **A remote MCP server with OAuth 2.1** (dynamic client registration, PKCE, rotating refresh tokens, per-app scopes) serves 40 tools. AxeBot runs on LangChain and LangGraph, on whichever model and API key the user picks: Anthropic, OpenAI, Google or xAI.
- **Offline, like Google Docs.** AxeTasker, AxeDSA and AxeAI open with no network (a service worker plus a per-user copy on the device). Changes made offline survive restarts and sync on their own when the connection is back.
- **A load-test engine for system design.** 26 problems, each in three stages of growth, built from 16 component types. The engine routes every request type through your design and computes each component's load, p99 latency with queueing delay, availability and monthly cost. Any design that holds up passes.
- **Feeds for sites that don't have one.** AxeFeed reads RSS, Atom and JSON Feed, and falls back to sitemaps or to watching a listing page. Sources are shared between readers, polled with `FOR UPDATE SKIP LOCKED` on intervals set by how often each one publishes, and fetched from public addresses only.

Next.js · React · TypeScript · Tailwind CSS · PostgreSQL (Neon) · LangChain · LangGraph · MCP · Electron · Vitest + PGlite · Playwright · Vercel

<sub>The source is private (500+ commits so far), but every web app above is live. Most of my commits land there, which is why my contribution graph is busier than my list of public repos.</sub>

## Other projects

- **[PocketLM][pocketlm]**: an experiment in how much of a language model's worldview comes from its data. I trained eight models on a MacBook, on posts from politically opposed Reddit communities: LiquidAI LFM2-1.2B fine-tuned with LoRA (on MLX and PEFT), and 124M-parameter GPT-2s trained from scratch with nanoGPT. For the from-scratch models, a FAISS semantic-deduplication pass built equal 200 MB corpora for each side. A React and Node front end talks to the Python model server over JSON-RPC to compare answers side by side. Weights are on [Hugging Face][pocketlm-hf].
- **[GlobalFreight AI][globalfreight]**, built for the Intellithon challenge at AI-Fortnight 2026: a logistics platform in four levels, from a RAG policy assistant that cites its sources to an autonomous command centre where Planner, Executor and Auditor agents coordinate through an MCP server under hard safety rules (no more than three cancellations in any ten minutes). Flask, LangGraph, ChromaDB and Next.js 16, on Azure OpenAI with automatic fallback to Gemini.
- **[vatsalgoyal.com][portfolio]**: my portfolio. Glass hexagons over a single WebGL shader, with no animation or 3D libraries. Next.js 16, React 19 and Tailwind CSS 4, with every page's content in Markdown files that are checked at build time. [Source][portfolio-src].
- **[JobNest][jobnest]**: a job portal for job seekers, employers and admins, built during my internship at Xebia. MERN, JWT auth, Stripe and Razorpay payments, Socket.io notifications.
- **[450 House of Sourdough][450]**: client work for an artisanal bakery in Jaipur. A storefront with WhatsApp checkout and a subscription program, plus a local-first Flask and SQLite system for orders, recurring deliveries and B2B accounts ([source][450-backend]).
- **[Gleck][gleck]** *(in development)*: my personal AI agent. It runs locally and is meant to keep my resumes and portfolio up to date, hunt for jobs, send mail and help with research. LangGraph, LangChain and MCP. It's developed on GitLab for now; releases will land in the GitHub repo.
- **AxeServer**: a salvaged PC turned into a 24/7 Ubuntu server on Tailscale, where I test agents like Gleck.
- **AshaKiran**: a website for an NGO, in React, Node and Postgres.

Smaller things: [movie.fy][moviefy] (Flutter), [Flapper][flapper] (a Flappy Bird-style canvas game, packaged for iOS with Capacitor) and a [VS Code setup][vscode-dsa] that runs DSA solutions in seven languages with one shortcut.

## Experience

- **Full-stack development intern**, [Pratham Software (PSI)][psi] · Jan – Jul 2026
- **IT consultant**, 450 House of Sourdough · Jun – Nov 2025. Built and deployed the bakery's web platform: online orders, payments and inventory.
- **Full-stack intern**, Xebia · Jun – Jul 2025. Built JobNest.
- **Part-time web developer**, Digispheres · Jul 2023 – Jul 2024. Built and deployed websites for clients.
- **Core team member**, JECRC Incubation Centre · 2022 – 2023. Represented the centre's NEC-winning team at IIT Bombay's E-Summit 2023 and helped run SISFS startup evaluation rounds.

**Education:** B.Tech in Computer Science and Engineering (full-stack development specialization), JECRC University, Jaipur · 2022 – 2026

## Achievements and certifications

- **Oracle Cloud certifications (2025):** Generative AI Professional, AI Vector Search, AI Foundations, Data Platform Foundations and OCI Foundations
- **Smart India Hackathon:** 7th place in the inter-college competition
- **College coding contests:** 1st place in Code-O-Mania and Algo vs Logic

## Tools I use

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://skillicons.dev/icons?i=ts%2Cjs%2Cpy%2Ccpp%2Cswift%2Creact%2Cnextjs%2Ctailwind%2Cnodejs%2Cexpress%2Cflask%2Cpostgres%2Cmongodb%2Csqlite%2Cpytorch%2Celectron%2Cflutter%2Cdocker%2Cvercel%2Cgithubactions%2Clinux&theme=dark&perline=11">
  <img alt="TypeScript, JavaScript, Python, C++, Swift, React, Next.js, Tailwind CSS, Node.js, Express, Flask, PostgreSQL, MongoDB, SQLite, PyTorch, Electron, Flutter, Docker, Vercel, GitHub Actions and Linux" src="https://skillicons.dev/icons?i=ts%2Cjs%2Cpy%2Ccpp%2Cswift%2Creact%2Cnextjs%2Ctailwind%2Cnodejs%2Cexpress%2Cflask%2Cpostgres%2Cmongodb%2Csqlite%2Cpytorch%2Celectron%2Cflutter%2Cdocker%2Cvercel%2Cgithubactions%2Clinux&theme=light&perline=11">
</picture>

Also: LangChain, LangGraph, MCP, RAG, MLX, LoRA and PEFT, FAISS, ChromaDB · Radix UI, Tiptap, React Flow, WebGL · Vitest, Playwright · Tailscale, Ubuntu Server

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://streak-stats.demolab.com?user=masterunix&theme=tokyonight&hide_border=true">
    <img alt="GitHub contribution streak for masterunix" src="https://streak-stats.demolab.com?user=masterunix&hide_border=true">
  </picture>
</p>

---

Thanks for stopping by. If you're hiring, or want to build something together, [email me][email] or find me on [LinkedIn][linkedin].

> "Just do it."

[portfolio]: https://www.vatsalgoyal.com
[linkedin]: https://www.linkedin.com/in/vatsalgoyal93
[email]: mailto:vatsalgoyal9999@gmail.com
[hf]: https://huggingface.co/axe-net
[axesuite]: https://home.axesuite.tech
[pocketlm]: https://github.com/masterunix/PocketLM
[pocketlm-hf]: https://huggingface.co/axe-net/PocketLM
[globalfreight]: https://github.com/masterunix/FOURTH-AGENT
[portfolio-src]: https://github.com/masterunix/portfolio-frontend
[jobnest]: https://github.com/masterunix/JobNest-v1
[450]: https://450-hos-static.vercel.app
[450-backend]: https://github.com/masterunix/450Backend
[gleck]: https://github.com/masterunix/gleck
[moviefy]: https://github.com/masterunix/Fluttter-Movie-App
[flapper]: https://github.com/masterunix/flapper
[vscode-dsa]: https://github.com/masterunix/VS-Code-DSA-Setup
[psi]: https://www.thepsi.com

[badge-portfolio]: https://img.shields.io/badge/vatsalgoyal.com-7C3AED?style=flat-square&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjZmZmIiBzdHJva2Utd2lkdGg9IjIiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCI+PGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iMTAiLz48cGF0aCBkPSJNMTIgMmExNC41IDE0LjUgMCAwIDAgMCAyMCAxNC41IDE0LjUgMCAwIDAgMC0yMCIvPjxwYXRoIGQ9Ik0yIDEyaDIwIi8+PC9zdmc+
[badge-linkedin]: https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iI2ZmZiIgZD0iTTIwLjQ0NyAyMC40NTJoLTMuNTU0di01LjU2OWMwLTEuMzI4LS4wMjctMy4wMzctMS44NTItMy4wMzctMS44NTMgMC0yLjEzNiAxLjQ0NS0yLjEzNiAyLjkzOXY1LjY2N0g5LjM1MVY5aDMuNDE0djEuNTYxaC4wNDZjLjQ3Ny0uOSAxLjYzNy0xLjg1IDMuMzctMS44NSAzLjYwMSAwIDQuMjY3IDIuMzcgNC4yNjcgNS40NTV2Ni4yODZ6TTUuMzM3IDcuNDMzYTIuMDYyIDIuMDYyIDAgMSAxIDAtNC4xMjUgMi4wNjIgMi4wNjIgMCAwIDEgMCA0LjEyNXpNNy4xMTkgMjAuNDUySDMuNTU1VjloMy41NjR2MTEuNDUyek0yMi4yMjUgMEgxLjc3MUMuNzkyIDAgMCAuNzc0IDAgMS43Mjl2MjAuNTQyQzAgMjMuMjI3Ljc5MiAyNCAxLjc3MSAyNGgyMC40NTFDMjMuMiAyNCAyNCAyMy4yMjcgMjQgMjIuMjcxVjEuNzI5QzI0IC43NzQgMjMuMiAwIDIyLjIyMiAwaC4wMDN6Ii8+PC9zdmc+
[badge-email]: https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white
[badge-hf]: https://img.shields.io/badge/Hugging_Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black
