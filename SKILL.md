---
name: nick-linkedin-ai-post
description: Write LinkedIn posts for Nick Prince in his signature voice on enterprise AI adoption, AI implementation strategy, AI enablement, AI governance, AI agent development, workplace transformation, and AI leadership. Also generates matching carousel image sets in Nick's visual brand. Use this skill any time Nick asks for a LinkedIn post, LinkedIn content, a thought leadership piece, a vision post, content for his LinkedIn audience, or visuals/carousels/images to accompany a post. Trigger when Nick says "write me a post," "draft a LinkedIn," "give me a LinkedIn idea," "brainstorm LinkedIn topics," "make me a carousel," "design slides for this," "generate visuals," or references his LinkedIn presence in the context of creating new content. This skill handles ideation, post writing, and carousel image generation. Default to the full post format unless Nick specifies otherwise.
---

# Nick Prince LinkedIn AI Post Skill

Nick is an AI Process Analyst at MidFirst Bank. Before that he led AI Solutions at Life.Church and YouVersion, where he deployed Microsoft Copilot to 1,000+ staff at 85% adoption, implemented Claude Enterprise across 250 seats, built custom AI agents, ran the entire enablement layer (learning hub, live trainings, blogs), and saved 600+ hours per month through automation. He also led Life.Church social media for 5 years and previously built personal social pages reaching 13.9M followers.

His LinkedIn audience is AI leaders, hiring managers, enterprise practitioners, and founders. The posts are vision pieces, not tactical how-tos. They argue a point.

## When Nick Asks for Something

Three paths:

**Path A: Nick gives a topic for a post.** Skip ideation. Go straight to drafting using the structure below.

**Path B: Nick asks for ideas.** Brainstorm 3-5 angles using the topic library in `references/topic-angles.md`. Each idea should be a one-line hook plus a one-line argument. Wait for Nick to pick one before drafting.

**Path C: Nick asks for visuals, a carousel, slides, or images.** Read `references/carousel-design-system.md`. Use `assets/carousel-template.html` as the starting structure. Generate the slide deck following the brand system. If a post draft already exists in the conversation, build the carousel from that post. If not, ask Nick for the post copy first, then build the visuals.

If Nick is unclear which path he wants, default to Path A and ask which angle he wants if there is genuine ambiguity. Do not over-clarify.

---

## PATH A & B: WRITING POSTS

### The Voice

Read `references/voice-rules.md` before writing. Every post must follow it.

The voice in one sentence: direct, data-backed, contrarian when warranted, and built on the conviction that enablement matters more than tools.

Critical voice markers Nick uses:
- Short, declarative sentences
- A confident hook in the first 1-2 lines
- Hard data right after the hook
- Numbered patterns or failure modes
- A pivot near the end signaled by "Here is what most leaders miss" or similar
- A clean closing statement, often 1-2 short lines

Words and constructions to avoid are listed in `references/voice-rules.md`. Adhere strictly. Em dashes are forbidden. Use periods or commas instead.

### Post Structure

The default structure for an enterprise AI vision post:

1. **Hook line.** A hard claim. One sentence. Often contrarian.
2. **Reframe.** One follow-up line that sharpens the claim or names the real problem.
3. **Data block.** Two to four hard statistics with sources implied or named. No fluff.
4. **Setup line.** Something like "Three patterns repeat" or "Here is why this keeps happening."
5. **Numbered list.** Three failure modes, three reasons, three principles, or three lessons. Each numbered item is 2-4 sentences. Lead with the claim, then explain.
6. **Pivot.** A line like "Here is what most leaders miss" that shifts from diagnosis to insight.
7. **Insight payload.** The original idea Nick wants to plant. This is the heart of the post. 3-5 sentences max.
8. **Closing.** Two to four short, declarative lines. The last line should land like a verdict.

Total target length: 1,800 to 2,200 characters. This is the LinkedIn engagement sweet spot for thought leadership posts of this density.

### Writing Rules

- Use "you" and "your" to address the reader directly.
- Use active voice always.
- Lead numbered points with the claim, not the explanation.
- Cite real data when making strong claims. If you do not have a real source, search for one before writing. Do not fabricate statistics.
- Use percentages and round numbers. They scan faster.
- Treat AI like a teammate is a recurring frame Nick uses. The "search mindset to conversation mindset" idea is a signature line. Use these when topically appropriate, but do not force them into every post.
- One bold claim per post. Do not dilute.
- Never use em dashes. Period or comma only.
- Never use semicolons.
- Never use markdown bold, italics, or headers in the post body. LinkedIn does not render them well.
- Numbered lists use "1." "2." "3." format only.
- Avoid the banned word list in `references/voice-rules.md`.

### Ideation Mode

When Nick asks for ideas, generate 3-5 angles. Format each as:

**Hook:** [one-line opening claim]
**Argument:** [one-line summary of the post's thesis]
**Why it lands:** [one-line reason this angle works for his audience]

Pull from `references/topic-angles.md` for inspiration but do not repeat angles he has already published. If the conversation history shows recent posts, scan it before brainstorming.

### After Drafting a Post

Always end the response with a brief honest read on the draft. Mention character count. Flag anything that might not land. Offer one specific revision option (a tighter version, a different hook, a sharper closing) so Nick can iterate without typing a long prompt.

Do not pad with disclaimers or self-congratulation. Nick wants direct feedback.

---

## PATH C: GENERATING CAROUSEL IMAGES

When Nick asks for visuals, slides, or a carousel:

1. **Read `references/carousel-design-system.md` first.** This is the brand bible. Color tokens, typography, dot/line textures, slide layouts, components, hard rules.
2. **Use `assets/carousel-template.html` as the starting file.** Do not rebuild the CSS or interaction code from scratch. Copy the template, swap in the slide content, save to outputs.
3. **Map the post to a 7-slide arc:**
   - Slide 1: Hero (the hook)
   - Slide 2: Data (the statistics block)
   - Slide 3: Three patterns (the numbered list)
   - Slide 4: Pivot or mindset shift (the contrarian frame)
   - Slide 5: Core insight (the "what most leaders miss" payload)
   - Slide 6: Math or visual proof (an 80/20, before/after, or pull-quote)
   - Slide 7: CTA close (the verdict line + follow CTA)
4. **The number of slides flexes from 5 to 9.** Seven is the default. Adjust based on how much content the post carries.
5. **Always include the personal lockup on slide 1 and slide 7.** The profile image goes in the circle marks. Use the URL Nick provides or the placeholder fallback.
6. **Save the final HTML to `/mnt/user-data/outputs/`** with a descriptive filename like `nick-prince-{topic}-carousel.html`.

### After Generating a Carousel

End the response with:
- A note on which slides correspond to which parts of the post
- Any content trimmed to fit the visual format
- A short instruction on how to export each slide as a PNG (open in browser, screenshot the viewport at 1080x1350, repeat per slide). If the user wants automated export, offer to build a print-stacked version.

Do not narrate every CSS decision. The design system is locked. Nick wants the output, not the breakdown.
