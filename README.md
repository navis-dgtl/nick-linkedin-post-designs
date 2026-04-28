# Nick LinkedIn AI Post Skill — Installation Guide

This folder contains the updated skill for writing LinkedIn posts and generating matching carousel images in your visual brand.

## What's in here

```
nick-linkedin-ai-post/
├── SKILL.md                              # Skill entry point. Routes to writing or visuals
├── README.md                             # This file
├── references/
│   ├── voice-rules.md                    # Writing voice (already in your skill)
│   ├── topic-angles.md                   # Topic library (already in your skill)
│   ├── example-post.md                   # Reference post (already in your skill)
│   └── carousel-design-system.md         # NEW — full visual brand system
└── assets/
    └── carousel-template.html            # NEW — working HTML starter for carousels
```

The three reference files marked "already in your skill" are not duplicated here. Keep your existing copies. Only `SKILL.md`, `references/carousel-design-system.md`, and `assets/carousel-template.html` are new or updated.

## How to install

### Claude Projects / Claude Skills
1. Replace your existing `SKILL.md` with the new one in this folder.
2. Add `references/carousel-design-system.md` to your skill's `references/` folder.
3. Create an `assets/` folder inside your skill if it doesn't exist, and add `carousel-template.html`.
4. Done. The skill will trigger on writing requests and visual requests.

### ChatGPT Custom GPT or Project
1. Upload all four files (SKILL.md, voice-rules.md, topic-angles.md, carousel-design-system.md, carousel-template.html) to the project's knowledge base or as system instructions.
2. In the GPT instructions, paste the contents of `SKILL.md` directly.
3. Reference the other files by name in your prompts ("use the carousel design system to...").

### Cursor / Windsurf / other code-aware AI tools
1. Drop the entire `nick-linkedin-ai-post/` folder into your project's `.cursor/` or `.windsurf/` directory.
2. Or paste `SKILL.md` into your global rules and keep the other files accessible in your workspace.

### Generic AI tools (Gemini, Grok, etc.)
1. Save all files locally.
2. When you want to use the skill, paste `SKILL.md` as the system prompt.
3. When asked for a carousel, paste `carousel-design-system.md` and `carousel-template.html` as additional context.

## How to use

**Write a post:**
> "Write me a LinkedIn post about why most AI rollouts fail at the enablement stage."

The skill follows Path A and drafts a post using your voice rules.

**Generate a carousel from an existing post:**
> "Make me a carousel for that post."

The skill follows Path C, reads the design system, copies the template, and produces a finished HTML carousel.

**Both at once:**
> "Write a LinkedIn post on AI governance and create a carousel for it."

The skill drafts the post first, then generates the carousel.

## A note on the profile image

The carousel template uses `{PROFILE_IMAGE_URL}` as a placeholder on slides 1 and 7. LinkedIn CDN URLs expire every few months. For long-term reliability:

1. Download your LinkedIn profile photo
2. Host it somewhere stable (your own site, GitHub, Imgur, or Cloudinary)
3. Replace the placeholder with that permanent URL

Or, when generating a carousel, paste the profile image URL into the conversation and the AI will swap it in.
