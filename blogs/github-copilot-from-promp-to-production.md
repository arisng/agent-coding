# From prompt to production: Building a landing page with Copilot agent mode

See how I built a developer-focused landing page in under 30 minutes using
GitHub Copilot agent mode and Claude 3.5 Sonnet—with just screenshots and prompts.

[Kedasha Kerr](https://github.blog/author/ladykerr/)·[GitHub profile of ladykerr](https://github.com/ladykerr)April 23, 2025

8 minutes
Share:
[Share on X](https://x.com/share?text=From%20prompt%20to%20production%3A%20Building%20a%20landing%20page%20with%20Copilot%20agent%20mode&url=https%3A%2F%2Fgithub.blog%2Fai-and-ml%2Fgithub-copilot%2Ffrom-prompt-to-production-building-a-landing-page-with-copilot-agent-mode%2F)
[Share on Facebook](https://www.facebook.com/sharer/sharer.php?t=From%20prompt%20to%20production%3A%20Building%20a%20landing%20page%20with%20Copilot%20agent%20mode&u=https%3A%2F%2Fgithub.blog%2Fai-and-ml%2Fgithub-copilot%2Ffrom-prompt-to-production-building-a-landing-page-with-copilot-agent-mode%2F)
[Share on LinkedIn](https://www.linkedin.com/shareArticle?title=From%20prompt%20to%20production%3A%20Building%20a%20landing%20page%20with%20Copilot%20agent%20mode&url=https%3A%2F%2Fgithub.blog%2Fai-and-ml%2Fgithub-copilot%2Ffrom-prompt-to-production-building-a-landing-page-with-copilot-agent-mode%2F)

GitHub Copilot has quickly become an integral part of how I build. Whether I’m
exploring new ideas or scaffolding full pages, using Copilot’s agent mode in my
IDE helps me move faster—and more confidently—through each step of the
development process.

[GitHub Copilot agent mode](https://github.blog/news-insights/product-news/github-copilot-agent-mode-activated/#agent-mode-in-vs-code) is an interactive chat experience built right into your IDE that turns Copilot
into an active participant in your development workflow. After you give it a
prompt, agent mode streamlines complex coding tasks by autonomously iterating on
its own code, identifying and fixing errors, suggesting and executing terminal
commands, and resolving runtime issues with self-healing capabilities.

And here’s the best part: You can attach images, reference files, and give
natural language instructions, and Copilot will generate and modify code directly in
your project!

In this post, I’ll walk you through how I built a developer-focused landing page—from product requirements to code—using GitHub Copilot agent mode and the Claude
3.5 Sonnet model. This kind of build could easily take a few hours if I did it
all by myself. But with Copilot, I had a working prototype in under 30 minutes! You’ll see how I used design artifacts, inline chat, and Copilot’s awareness of
context to go from idea → design → code, with minimal friction.

You can also watch the full build in the video above!

Not sure how to use agent mode in GitHub Copilot?

Don’t sweat it—we have a guide for you on everything you need to know to get
started (plus, details on how to use other GitHub Copilot features, too). [Learn more >](https://github.blog/ai-and-ml/github-copilot/mastering-github-copilot-when-to-use-ai-agent-mode/)

## Designing with AI: From PRD to UI

Before I wrote a single line of code, I needed a basic product vision. I started
by [using GitHub Copilot on GitHub.com](https://github.com/copilot) to generate a lightweight product requirements document (PRD) using GPT-4o.
Here was my prompt:

> “Describe a landing page for developers in simple terms.”

Copilot returned a structured but simple [outline of a PRD](https://github.com/copilot/share/0a631304-4100-80a1-a951-3e0864370837) for a developer-focused landing page. I then passed this PRD into Claude 3.5
Sonnet and asked it to generate a design based on that prompt.

![An image showing the interface for GitHub Copilot responding to the prompt "Describe a landing page for developers in simple terms" with a a structured but simple outline of a PRD for a developer-focused landing page.](https://github.blog/wp-content/uploads/2025/04/copilot-claude-prd-design.png?w=768)

Claude gave me a clean, organized layout with common landing page sections: a
hero, feature list, API examples, a dashboard preview, and more. This was more
than enough for me to get started.

You can explore the full design that Claude [built here](https://gh.io/devflow-design); it’s pretty cool.

## Setting up the project

For the tech stack, I chose [Astro](https://astro.build/) because of its performance and flexibility. I paired it with Tailwind CSS and
React for styling and component architecture. I started in a blank directory and
ran the following commands:

```bash
npm create astro@latest
npx astro add react
npx astro add tailwind
```

I initialized the project, configured Tailwind, and opened it in VS Code with
GitHub Copilot agent mode enabled ([learn how to enable it with our docs](https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode)!). Once the server was running, I was ready to start building.

## Building section by section with Copilot agent mode

Copilot agent mode really shines when translating visual designs into
production-ready code because it understands both image and code context in your project.
By attaching a screenshot and specifying which file to edit, I could prompt it
to scaffold new components, update layout structure, and even apply Tailwind
styles—all without switching tabs or writing boilerplate manually.

For our project here, this meant I could take screenshots of each section from
Claude’s design and drop them directly into Copilot’s context window.

💡 Pro tip: When building from a visual design like this, I recommend working on one
section at a time. This not only keeps the context manageable for the model, but also
makes it easier to debug if something goes off track. You’ll know exactly where
to look!

### Creating the hero and navigation section

I opened `index.astro`, attached the design screenshot, and typed the following prompt:

> “Update index.astro to reflect the attached design. Add a new navbar and hero
section to start the landing page.”

Copilot agent mode then returned the following:

• Created `Navbar.astro` and `Hero.astro`
• Updated `index.astro` to render them
• Applied Tailwind styling based on the visual layout

And here’s what I got:

Now, this is beautiful! Though it doesn’t have the image on the right [per the design](https://gh.io/devflow-design), it did a very good job of getting the initial design down. We’ll go back in
later to update the section to be exactly what we want.

## Commit early and often

💡 Pro tip: When building with AI tools, commit early and often. I’ve seen too many folks lose progress when a prompt goes sideways.
And in case you didn’t know, GitHub Copilot can help here too. After staging
your changes in the Source Control panel, click the ✨ sparkles icon to
automatically generate a commit message. It’s a small step that can save you a lot of time
(and heartache).

## Improve accuracy with Copilot custom instructions

One of the best ways to improve the quality of GitHub Copilot’s
suggestions—especially in multi-file projects—is by providing it with [custom instructions](https://docs.github.com/en/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot). These are short, structured notes that describe your tech stack, project
structure, and any conventions or tools you’re using.

Instead of repeatedly adding this contextual detail to your chat questions, you
can create a file in your repository that automatically adds this information
for you. The additional information won’t be displayed in the chat, but is
available to Copilot—allowing it to generate higher-quality responses.

To give Copilot better context, I created a `CopilotInstructions.md` file describing my tech stack:

• Astro v5
• Tailwind CSS v4
• React
• TypeScript

When Copilot agent mode referenced this file when making suggestions, I noticed
the results became more accurate and aligned with my setup.

Here’s what some of the file looked like:

```markdown
# GitHub Copilot Project Instructions

## Project Overview
This is an Astro project that uses React components and Tailwind CSS for styling. When making suggestions, please consider the following framework-specific details and conventions.

## Tech Stack
- Astro v5.x
- React as UI library
- Tailwind CSS for styling (v4.x)
- TypeScript for type safety

## Project Structure

```text
├── src/
│   ├── components/     # React and Astro components
│   ├── layouts/        # Astro layout components
│   ├── pages/          # Astro pages and routes
│   ├── styles/         # Global styles
│   └── utils/          # Utility functions
├── public/             # Static assets
└── astro.config.mjs    # Astro configuration
```

## Component Conventions

### Astro Components

- Use `.astro` extension
- Follow kebab-case for filenames
- Example structure:

```astro
---
// Imports and props
interface Props {
  title: string;
}

const { title } = Astro.props;
---

<div class="component-wrapper">
  <h1>{title}</h1>
  <slot />
</div>

<style>
  /* Scoped styles if needed */
</style>
```

You can explore the full instructions [file in my repo](https://github.com/LadyKerr/devflow-landing/blob/main/.github/copilot-instructions.md), along with the full code, setup instructions, and a link to the deployed
landing page.

## Iterating on your designs by prompting Copilot

I then repeated the same process to build each new section. Here’s what this
looked like in practice:

### “Built by Developers” section

> “Add a new section to the landing page called ‘By Developers’ and follow the
attached design.”

Copilot generated a reusable component with feature cards structured in a
Tailwind-styled grid.

![An image showing a reusable component with feature cards structured in a Tailwind-styled grid.](https://github.blog/wp-content/uploads/2025/04/by-devs-section.png?w=768)

### “API development” section

> “Add the API development section based on the design.”

This section featured interactive code samples in tabs. Copilot interpreted that
from the screenshot and added UI logic to switch between examples—without me asking.

### “Dashboard preview” section

> “Now add the dashboard management section on the landing page based on the
design.”

I uploaded a screenshot of my editor as a placeholder image, and Copilot added
it seamlessly to the new component.

![A screenshot of the dashboard management section.](https://github.blog/wp-content/uploads/2025/04/dashboard_api.png?w=512)

It’s so amazing how fast we’re building this landing page. Look at the progress
we’ve already made!

## Smart suggestions, fast results

Even with sections like “Trusted by Developers” and “Try it Yourself,” Copilot
created placeholder images, added semantic HTML, and applied Tailwind styling—all
based on a single image and prompt. 🤯

![A screenshot of the "Trusted by developers worldwide" section of the landing page.](https://github.blog/wp-content/uploads/2025/04/trusted-by-devs.png?w=768)

When I updated the final hero section to match the layout more closely, Copilot
flagged and fixed TypeScript issues without being prompted.

That might sound small, but it’s a big deal. It means Copilot agent mode wasn’t just taking instructions—it was actively
understanding my codebase, looking at my terminal, identifying problems, and resolving them in real time. This reduced my need to context switch, so I could focus on shipping!

This wasn’t just a series of generated components. It was a fully structured, landing page built with modern best practices baked in. And I didn’t have to build it alone!

## Wrapping up:

With GitHub Copilot agent mode and Claude working together, I was able to:

• Generate a usable PRD and design mockup with a single prompt
• Build a responsive Astro-based landing page in less than thirty minutes
• Scaffold, test, and iterate on each section with minimal manual coding
• Use natural language to stay in the flow as I developed

## What’s next?

To complete this project, I updated the README with a clear project structure,
added instructions for getting started, and staged it for deployment. From here,
you can:

• Deploy it with GitHub Pages, Netlify, or your host of choice
• Set up GitHub Actions for CI/CD
• Add unit tests or accessibility checks
• Replace placeholder content with real data (like logos, dashboard, and profile
images)
• Add new pages based on the Navbar

Want to explore it yourself?

• [View the repository](https://github.com/LadyKerr/devflow-landing)
• [View the live demo](https://ladykerr.github.io/devflow-landing/)

## Take this with you

AI tools like GitHub Copilot agent mode are transforming how we build, but like
any tool, their power depends on how well we use them. Adding context, being
explicit, and committing often made building this web page smooth and successful.

If you’re thinking about building with GitHub Copilot, give this workflow a try:

1. Start with a PRD using Copilot on GitHub.com
2. Generate a design from your PRD with Claude
3. Use Copilot Agent in your IDE to code it, step by step.

Until next time, happy coding!

## Tags:

[GitHub Copilot](https://github.blog/tag/github-copilot/)

## Written by

![Kedasha Kerr](https://avatars.githubusercontent.com/u/47188731?v=4&s=200)

### [Kedasha Kerr](https://github.blog/author/ladykerr/)

[@ladykerr](https://github.com/ladykerr)

Kedasha is a Developer Advocate at GitHub where she enjoys sharing the lessons
she's learned with the wider developer community. She finds joy in helping others
learn about the tech industry and loves sharing her experience as a software
developer. Find her online @itsthatladydev.

[GitHub Copilot](https://github.blog/tag/github-copilot/)

## More on [GitHub Copilot](https://github.blog/tag/github-copilot/)

### [GitHub for Beginners: Building a React App with GitHub Copilot](https://github.blog/ai-and-ml/github-copilot/github-for-beginners-building-a-react-app-with-github-copilot/)

Follow along and build a frontend client using React and Copilot Chat.

[Kedasha Kerr](https://github.blog/author/ladykerr/)

## Related posts

  [AI & ML](https://github.blog/ai-and-ml/)

### [Vibe coding: Your roadmap to becoming an AI developer](https://github.blog/ai-and-ml/vibe-coding-your-roadmap-to-becoming-an-ai-developer/)

Learn how to go from curious coder to AI wizard—with a little help from GitHub.

[Gwen Davis](https://github.blog/author/purpledragon85/)  [AI & ML](https://github.blog/ai-and-ml/)

### [Real‑world video demo: Using different AI models in GitHub Copilot](https://github.blog/ai-and-ml/real%e2%80%91world-video-demo-using-different-ai-models-in-github-copilot/)

Curious about how AI models perform in real-world scenarios with GitHub Copilot?
Same. We made a live video demo to find out, and wrote up our key takeaways.

[Jon Peck](https://github.blog/author/peckjon/)

## Explore more from GitHub

![Docs](https://github.blog/wp-content/uploads/2024/07/Icon-Circle.svg)

### Docs

Everything you need to master GitHub, all in one place.

 [Go to Docs](https://docs.github.com/)![GitHub](https://github.blog/wp-content/uploads/2024/07/Icon_95220f.svg)

### GitHub

Build what’s next on GitHub, the place for anyone from anywhere to build
anything.

 [Start building](https://github.com/)![Customer stories](https://github.blog/wp-content/uploads/2024/07/Icon_da43dc.svg)

### Customer stories

Meet the companies and engineering teams that build with GitHub.

 [Learn more](https://github.com/customer-stories)![Enterprise content](https://github.blog/wp-content/uploads/2022/05/careers.svg)

### Enterprise content

Executive insights, curated just for you

 [Get started](https://github.com/solutions/executive-insights)

## We do newsletters, too

Discover tips, technical guides, and best practices in our biweekly newsletter
just for devs.

 Your email address Subscribe

 Yes please, I’d like GitHub and affiliates to use my information for
personalized communications, targeted advertising and campaign effectiveness. See the [GitHub Privacy Statement](https://github.com/site/privacy) for more details. [Go to GitHub homepage](https://github.com/)

## Product

[Features](https://github.com/features)
[Security](https://github.com/security)
[Enterprise](https://github.com/enterprise)
[Customer Stories](https://github.com/customer-stories?type=enterprise)
[Pricing](https://github.com/pricing)
[Resources](https://resources.github.com/)

## Platform

[Developer API](https://developer.github.com/)
[Partners](https://partner.github.com/)
[Atom](https://atom.io/)
[Electron](https://www.electronjs.org/)
[GitHub Desktop](https://desktop.github.com/)

## Support

[Docs](https://docs.github.com/)
[Community Forum](https://github.community/)
[Training](https://services.github.com/)
[Status](https://www.githubstatus.com/)
[Contact](https://support.github.com/)

## Company

[About](https://github.com/about)
[Blog](https://github.blog/)
[Careers](https://github.com/about/careers)
[Press](https://github.com/about/press)
[Shop](https://shop.github.com/)

[LinkedIn icon GitHub on LinkedIn](https://www.linkedin.com/company/github)
[Instagram icon GitHub on Instagram](https://www.instagram.com/github/)
[YouTube icon GitHub on YouTube](https://www.youtube.com/github)
[X icon GitHub on X](https://twitter.com/github)
[TikTok icon GitHub on TikTok](https://www.tiktok.com/@github)
[Twitch icon GitHub on Twitch](https://www.twitch.tv/github)
[GitHub’s organization on GitHub](https://github.com/github)

© 2025 GitHub, Inc.
[Terms](https://docs.github.com/en/github/site-policy/github-terms-of-service)
[Privacy](https://docs.github.com/en/github/site-policy/github-privacy-statement)
Manage Cookies
Do not share my personal information

## Additional Links

- [Designing with AI: From PRD to UI](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#designing-with-ai-from-prd-to-ui)
- [Setting up the project](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#setting-up-the-project)
- [Building section by section with Copilot agent mode](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#building-section-by-section-with-copilot-agent-mode)
- [Commit early and often](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#commit-early-and-often)
- [Improve accuracy with Copilot custom instructions](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#improve-accuracy-with-copilot-custom-instructions)
- [Iterating on your designs by prompting Copilot](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#iterating-on-your-designs-by-prompting-copilot)
- [Smart suggestions, fast results](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#smart-suggestions-fast-results)
- [Wrapping up:](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#wrapping-up)
- [What’s next?](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#whats-next)
- [Take this with you](https://github.blog/ai-and-ml/github-copilot/from-prompt-to-production-building-a-landing-page-with-copilot-agent-mode/#take-this-with-you)
