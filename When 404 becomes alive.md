<!--
title: "MarkdownsPeek: When 404 Becomes Alive"
date: 2025-10-22
author: Piotr Porzuczek
description: "A lightweight way to turn a GitHub repository into a live, navigable website where Markdown files act as routes and the 404 page becomes a dynamic content gateway."
tags: [javascript, github, markdown, headless-cms, web-development]
-->

## MarkdownsPeek: when 404 becomes alive

I’ve been exploring a simple idea: what if a GitHub repo could be your website? No static build, no backend, no CMS. Just Markdown files that render themselves the moment you visit their URL. That’s what the new version of **markdowns-peek** does.

### From viewer to router

It used to be a simple viewer where you could browse a list of `.md` files and open them inline. Now it listens to the URL. Every route is a potential Markdown file. If it exists in your repo, it loads and renders instantly. If not, it gracefully falls back to a real 404.

You can even mount the viewer directly on your 404 page. That means your “page not found” becomes a dynamic entry point into your repo. Navigate anywhere, and if there’s a matching `.md`, it comes alive. No builds, no redeploys, just GitHub as your live content layer.

### The repo as a living CMS

It’s liberating. Your repo becomes your content management system: versioned, reviewable, transparent, and every commit is a publish event. Push, refresh, done. MarkdownsPeek turns the URL bar into a file explorer for your repo. It blurs the line between docs and web app, between page and file, between not found and found elsewhere. It’s minimal, fast, and purely client-side.

### Beyond CMS: the idea of headless for developers

It doesn’t feel like cheating. It feels like the way things should have always worked. We don’t need heavy CMSs or backend frameworks to publish thoughts. Most of the time, what we call content is just text: notes, documentation, small ideas that grow over time. Developers already have a perfect environment for that which is __GitHub__. Version control, history, collaboration, it’s all there. Why add WordPress or databases on top of something that already understands text better than anything else?

MarkdownsPeek takes that logic and turns it into a headless content model for developers. No dashboard, no visual editors. Your Markdown files are the backend. The browser is the renderer. There’s no middleman between what you write and what people see. This isn’t static site generation; it’s direct content delivery. No builds, no pipelines, no preview servers. Just a repo and a viewer that knows how to listen.

It’s the same idea that made headless CMS popular, but stripped of everything that bloated it. No API tokens, no hosting tiers, no admin panels. Just Markdown served straight from the source. A living documentation layer that updates the moment you push.

### A thin layer with no agenda

MarkdownsPeek isn’t trying to be a platform. It doesn’t lock you in or reshape your structure. It’s a thin layer of logic that exposes what’s already there! Your words, your files, your links and lets them exist on the web without permission or ceremony.

### Why it matters

Publishing doesn’t need to be a system. It can be a gesture. A repo can be a place of thought, not just code. Sometimes the simplest tools give ideas the most direct path to daylight.

👉 [**markdowns-peek on npm**](https://www.npmjs.com/package/markdowns-peek)
