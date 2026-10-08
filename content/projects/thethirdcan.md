+++
template = "project.html"
title = "The Third Can"
description = "A browser extension that provides a suite of utilities to improve the UX of the Two Cans & String website."
date = 2022-01-01

[extra]
old = true
+++

Built with:
- JavaScript
- HTML/CSS
- Preact
- Rust + Rocket

Project source: [link](http://github.com/aprzn123/thethirdcan)

# Background
Two Cans & String is a website where users semi-anonymously ask and answer questions. It's been run by one man named Blake for nearly two decades. The way it works is that as an asker, you can post questions to the board and you'll see answers roll in over time, without visibly attached names. As an answerer, you are fed a randomized feed of questions that others have asked and you can either answer them or skip. I was, for a time, heavily involved in its community, and wanted to give back during a period when the developer was ons a bit of a hiatus.

# Development
So I developed The Third Can, a collection of utilities meant to address UX issues that people experienced. It was my first time writing a browser extension, and I learned a lot of interesting things about how they work, especially with regards to the specific security boundaries that are put in place.

In particular, I faced a lot of engineering challenges with regards to the ability to access values within the page's JavaScript environment. The way this is done is by having a separate JavaScript file that, instead of running as part of the extension, is treated as an asset and injected into the DOM *by* the extension. Since each individual extension feature can be separately enabled/disabled by the user, the overall pipeline goes:
- User loads a page relevant to the extension.
- A script specific to the type of page is launched.
- That script reads the config to determine which features are enabled.
- It injects JavaScript code into \<script\> tags in the page only for enabled features that are also applicable to that type of page.

# Ending
Unfortunately, my timing quite possibly could not have been worse. Mere months after publishing The Third Can, Blake came back with a big update that not only overhauled the look of the site, but was built around a homemade React-like framework and made the entire website client-side rendered. I never had the time to reverse-engineer the framework to find a way to hook into it, but it's still a pipe dream of mine to bring back the extension one day.

# Reflection
Every so often I go back and look at the project's codebase. I get the classic feeling of "why did I do all this? Clearly younger Nova was foolish and overcomplicated everything for no good reason," but when I look deeper and remind myself of all the specific limitations I had to overcome, the need for this structure falls out so clearly. In retrospect I probably could have actually *organized* the project better (especially if I had added a build step) but that's neither here nor there. I'm proud of my work, and it was useful to the community while it was around.
