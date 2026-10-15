# AI Tells: what makes a page look generated

These are the patterns people have learned to associate with AI-built sites. None of them is banned outright, a specific brief can call for any one of them, but each is a default rather than a decision. If one shows up in your design, it should be because the brief demanded it, not because it fell out of your fingers.

## Visual tells

**The three stock looks.** Current AI design clusters around: (1) warm cream background near `#F4F1EA`, high-contrast serif display, terracotta or warm-clay accent near `#D97757`; (2) near-black background with a single acid-green or vermilion accent; (3) broadsheet newspaper style with hairline rules, zero border-radius, dense columns. If your plan matches one of these and the brief didn't ask for it, start over on that axis.

**Purple-to-blue gradients.** Especially on hero backgrounds, buttons, and gradient text. The single loudest tell there is.

**The three-card feature grid.** Three equal cards, each with a rounded icon in a tinted circle, a bold short title, and two lines of gray text. If the content genuinely has three parallel features, present them, but find a shape that isn't this exact component.

**Glassmorphism.** Frosted translucent cards floating over blurry colorful blobs. The named Glass docs theme uses restrained translucency on navigation surfaces only; its article and content components remain opaque.

**Uniform 12 to 16px border-radius on everything.** Radius should be a considered token, and can be zero.

**Emoji as icons or in headings.** A rocket next to "Launch fast" reads as generated instantly.

**Hero = big number + tiny label + gradient accent.** Or hero = centered H1, one gray subtitle sentence, two side-by-side buttons (one filled, one outlined). Both are the template answer.

**Inter/Poppins for everything.** Or any single font doing display, body, and UI duty at once.

**Scattered scroll animations on every element.** Fade-up on each card as it enters the viewport. One orchestrated moment beats twelve twitchy ones, and often no animation is the strongest choice.

**Fake trust signals.** Rows of grayed-out logos of companies that don't exist, "Trusted by 10,000+ teams" on a bakery site, five-star testimonial cards from "Sarah J., Marketing Manager".

**Perfect symmetry everywhere.** Every section the same height, every list exactly three items, every card the same size. Real layouts have hierarchy: some things matter more and look it.

## Copy tells

- Em-dashes. The long dash used as a dramatic pause is now the single most recognized AI writing tell. Zero of them in the final output; restructure the sentence instead.
- Zombie words: seamless, elevate, unlock, empower, robust, comprehensive, cutting-edge, leverage, streamline, synergy, holistic, game-changer, "delve into", "in today's fast-paced world".
- Headline formula "Verb your noun": "Elevate your workflow", "Transform your business", "Supercharge your growth".
- Every section header is a benefit statement of identical length.
- Vague claims with no nouns in them: "powerful features", "beautiful design", "amazing results".
- CTAs that could belong to any product: "Get started", "Learn more", "Join now" with no object.
- Copy that never commits to anything: no prices, no place names, no dates, no proper nouns.

## What real sites have instead

- A point of view. Something is emphasized at the expense of something else.
- Specific nouns: dish names, city names, model numbers, dates, prices.
- Asymmetry that encodes hierarchy.
- One memorable signature element, surrounded by restraint.
- Typography doing personality work, not just delivery work.
- Copy a human could have said out loud without wincing.

## Final self-check (run before delivering, every time)

- [ ] No purple/blue gradient or icon-circle three-card grid; no glassmorphism except restrained navigation surfaces when the named Glass docs theme was chosen
- [ ] Palette is either the chosen named preset (values verbatim) or the user's own brand colors
- [ ] If a custom palette was used, it was stated in one line first and justified by the subject
- [ ] No accidental green or navy cast: those are the usual drift landing spots when avoiding banned looks
- [ ] Backgrounds are warm or deliberately neutral, not cool-tinted by accident
- [ ] Exactly one signature element; everything else is disciplined
- [ ] Zero em-dashes anywhere in the page (search the file for "—" and "&mdash;" to be sure)
- [ ] A humanization pass ran over all copy; nothing left reads like a committee wrote it
- [ ] Zero zombie words; every CTA names a real action
- [ ] At least three specific nouns/numbers in the copy (a price, a place, a date, a name)
- [ ] Both themes designed on purpose; body text contrast passes 4.5:1 in each
- [ ] Theme toggle present and it overrides the system preference
- [ ] No horizontal scroll at 360px; headings use clamp(); touch targets are 44px+
- [ ] No external image URLs; every visual is inline SVG/CSS or an intentional labeled placeholder
- [ ] Any form either works via mailto/tel or is clearly flagged as needing a backend hookup
- [ ] Theme script is inline in the head so there's no flash of the wrong theme on load
- [ ] Semantic landmarks, one h1, visible focus styles, reduced motion respected
- [ ] Looking at it cold, would you guess "small studio" or "prompt"? Be honest.
