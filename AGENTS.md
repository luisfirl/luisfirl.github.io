# AGENTS.md

This file provides persistent project context and working instructions for AI coding agents contributing to `luisfirl.com`.

Read this file before making changes. The goal is that a new agent can continue the project without needing the full history of previous chats.

---

# 1. Project overview

## Website

- Personal academic website and research portfolio of **Luis Firl**.
- Production domain: `https://luisfirl.com`
- GitHub repository: `luisfirl/luisfirl.github.io`
- Hosting: GitHub Pages
- DNS/domain registrar: Cloudflare
- Deployment: GitHub Actions
- Primary language of the public website: **English**
- Conversation with Luis may be in German.

This is not intended to be a generic personal homepage or a startup-style portfolio. It is an academic research portfolio designed primarily for researchers, principal investigators, PhD selection committees, and collaborators in computational biology, systems biology, theoretical biophysics, and scientific machine learning.

The website should communicate scientific depth, quantitative thinking, research independence, and strong computational ability without turning into a software-engineering portfolio.

---

# 2. Main purpose and audience

The primary purpose of the site is to support Luis's academic profile and future PhD applications in areas such as:

- Systems Biology
- Theoretical Biophysics
- Computational Biology
- Scientific Machine Learning
- AI/ML for the Life Sciences
- Mechanistic Modeling
- Dynamical Systems in Biology

The target reader may be a PI who spends only 30–90 seconds on the first visit. The site must therefore make the following clear quickly:

1. What scientific questions Luis is interested in.
2. Which mathematical and computational methods he works with.
3. What research he has actually carried out.
4. What he is currently working on.
5. Where to find deeper evidence such as project pages, code, thesis, and eventually publications.

The website should establish a coherent research identity rather than simply listing credentials.

A useful high-level positioning is:

> Computational scientist interested in combining mechanistic models and machine learning to understand complex biological systems.

Do not treat this exact sentence as immutable copy. It is a positioning guideline.

---

# 3. Luis's academic background

Relevant background for public-facing copy:

- Luis studied **Life Science Engineering at HTW Berlin**.
- He completed his Master's thesis in the **Theoretical Biophysics** research environment at **Humboldt-Universität zu Berlin**.
- The thesis was supervised in the research context of **Prof. Edda Klipp**.
- His work sits at the interface of biology, mathematical modeling, scientific computing, and machine learning.
- He is interested in pursuing a PhD in Systems Biology / Theoretical Biophysics / Scientific ML / AI for life sciences.

Do not make the website read like a conventional chronological CV. Background information should support the research narrative.

---

# 4. Research identity and content priorities

When deciding what to emphasize, use this priority order:

1. Scientific question and biological motivation.
2. Mathematical / mechanistic formulation.
3. Inference and optimization strategy at a conceptual level.
4. Dynamic simulation and scientific interpretation.
5. Current research development and future direction.
6. Code and implementation details as supporting evidence.

Avoid presenting Luis primarily as someone who "implemented packages" or "built scripts". The code matters, but the scientific and mathematical thinking should remain central.

For example, on the signaling-network project, prefer language such as:

- constrained parameter inference
- dependency estimation
- identifiability
- mechanistic ODE modeling
- mass-action kinetics
- dynamic signaling networks
- perturbation analysis
- scalable network simulation

rather than centering the story on individual Julia libraries.

Software/package names may appear in a compact technical note, repository README, or implementation section when useful, but they should not dominate the main research narrative.

---

# 5. Main ongoing research project

## Working title

**Data-driven Dynamic Modeling of Signaling Networks in Triple-Negative Breast Cancer**

Current project page:

`/projects/signaling-networks`

This is an **ongoing research project**, not merely a completed Master's thesis project.

The project originated from Luis's Master's thesis in the Theoretical Biophysics group / research environment of Prof. Edda Klipp at Humboldt-Universität zu Berlin, but research on the topic is continuing.

## Important framing rule

Do **not** frame this project primarily as:

> Master's Thesis

Instead frame it as:

> Ongoing Research

The Master's thesis should be described as an important origin or milestone within the continuing project.

The conceptual timeline is approximately:

`Master's thesis → continued model development → ongoing research collaboration → future scientific publication`

Do not imply that a paper has already been submitted, accepted, or published unless Luis explicitly confirms that status later.

Do not use strong formal claims such as "manuscript in preparation" unless the actual project status warrants that wording.

At the current stage, safer language includes:

- developing the scientific framework for a future publication
- ongoing research collaboration
- preparing a publication blueprint / scientific framework

---

# 6. Scientific context of the signaling project

The project uses time-resolved phosphoproteomic measurements from triple-negative breast cancer cells to construct and analyze dynamic kinase signaling models.

The scientific goal is broader than reconstructing one fixed small network. The modeling framework is intended to support increasingly large and interconnected signaling networks.

## Critical content rule

**Do not emphasize or advertise the specific network size used in the Master's thesis.**

In particular, avoid using the counts of kinases, phosphorylation sites, or edges as headline statistics or key project metrics.

These values belong to one implementation state of the Master's thesis and are not central to the long-term research aim.

The scientific story should instead focus on the general modeling framework and its scalability.

---

# 7. Core mathematical idea: dependency inference

The signaling model introduces parameters representing dependencies between kinases, their phosphorylation states, and downstream phosphorylation sites.

The project uses two central classes of dependency parameters:

- **α parameters**: describe the relative influence of an upstream kinase on phosphorylation of a target site.
- **β parameters**: describe the contribution of phosphorylation states of a kinase to its effective activity.

A representative nested dependency formulation used in the project is conceptually of the form:

`P_i(t) = α_i^0 + Σ_j α_j^i ( β_j^0 + Σ_k β_j^k P_j^k(t) )`

The exact notation may be typeset more carefully later.

Public-facing explanations should focus on what these terms mean biologically and mathematically, rather than on implementation-specific code.

Important themes:

- constrained parameter estimation
- relative interaction strengths
- coupling between kinase state and downstream signaling
- inference from experimental time-series data
- parameter identifiability
- integration of additional biophysical information

---

# 8. Optimization framing

The Master's-thesis work compared two complementary numerical optimization strategies for estimating network dependencies:

- a gradient-based formulation
- an interior-point formulation

The website should discuss these approaches at the **mathematical / numerical level**, not as a package comparison.

Useful concepts to highlight include:

## Gradient-based approach

- first-order derivative information
- iterative parameter updates
- transformed / constrained parameter representations
- potential scalability advantages as problem size grows

## Interior-point approach

- constrained nonlinear optimization
- direct treatment of constraints
- use of curvature / higher-order numerical information
- strong convergence performance for the investigated problem

Avoid making the main story:

> Flux vs JuMP

or:

> Package A vs Package B

A scientifically important result is that different optimization formulations can generate very similar fits while identifying different underlying parameter configurations.

This supports a central research insight:

> Good agreement with experimental observations does not necessarily imply unique identification of the underlying biological parameters.

This parameter-identifiability problem is scientifically more important than benchmark-style software performance comparisons.

---

# 9. Core mechanistic idea: dynamic ODE network

The inferred dependencies are embedded into a mechanistic system of ordinary differential equations.

The dynamic model includes biological processes such as:

- transcription
- translation
- protein degradation
- phosphorylation
- dephosphorylation

The model is based on mass-action-style kinetic descriptions and follows dynamic states such as:

- mRNA
- unphosphorylated proteins
- phosphorylated protein states

The key conceptual transition to communicate is:

`experimental data → inferred dependencies → signaling activity → phosphorylation kinetics → coupled ODE dynamics`

This is one of the most important scientific ideas on the website.

Whenever possible, explain that the inferred dependency structure is not treated as a separate static result: it is incorporated into the phosphorylation terms of the dynamic ODE system.

The website should make this relationship visually and conceptually clear.

---

# 10. Current research beyond the Master's thesis

Luis is actively continuing research on this project.

Current work includes two major directions.

## A. Improving kinetic parameter estimation

Luis is currently improving the kinetic parameter-estimation strategy at the implementation and numerical-method level.

Relevant goals include:

- improved numerical stability
- better optimization behavior
- computational efficiency
- improved simulation quality
- robustness of inferred kinetic parameters
- scalability to larger signaling networks

When describing this work publicly, focus on the numerical and modeling challenge rather than low-level implementation details unless specifically requested.

## B. Developing a publication framework

Luis is also developing a blueprint / scientific framework for a future paper on the broader research topic together with collaborators and professors involved in the research environment associated with the experimental dataset used in the Master's work.

Do not invent:

- publication authors
- publication title
- journal
- submission status
- publication timeline

Do not claim publication status beyond what is explicitly known.

---

# 11. Longer-term scientific direction

The project should naturally connect to Luis's broader interest in scientific machine learning.

Potential future directions include:

- improved constrained parameter inference
- incorporation of additional biophysical constraints
- integration of additional experimental measurements
- larger signaling-network reconstruction
- experimental perturbation validation
- coupling signaling dynamics to phenotypic observations
- mechanistic + machine-learning hybrid models
- physics-informed or biology-informed learning approaches where scientifically justified

Do not present methods such as Physics-Informed Neural Networks as if they are already implemented unless that becomes true later.

They may be described as possible future methodological directions.

---

# 12. Research data and confidentiality

This project involves experimental phosphoproteomic data that was described in the Master's thesis as unpublished at the time of writing.

Be conservative about research-data exposure.

## Never do the following without explicit approval from Luis

- publish raw unpublished datasets
- commit confidential experimental files
- expose unpublished collaborator material
- publish newly generated results that may belong in a future manuscript
- infer or invent unpublished experimental details
- expose credentials, tokens, private URLs, or local configuration

## Safe default

Publicly discuss:

- scientific motivation
- mathematical model structure
- general methodology
- concepts already intentionally made public
- high-level results already intentionally made public
- Luis's own research role
- ongoing methodological work at a high level

If a proposed website change would reveal specific new scientific results from ongoing work, ask Luis before publishing them.

---

# 13. Master's thesis

The Master's thesis is an important research milestone and the origin of the current signaling project.

Title:

**Data-driven Dynamic Simulation of Signaling Networks in Triple Negative Breast Cancer Cells**

The thesis was completed in 2026 in the context of Life Science Engineering at HTW Berlin and Theoretical Biophysics at Humboldt-Universität zu Berlin.

The public website currently provides the thesis PDF as a supporting research document.

Current public path:

`/files/luis-firl-master-thesis.pdf`

The project page should present the PDF as documentation of an important stage of the research, not as the entire identity of the ongoing project.

A suitable link label is:

`Read Master's Thesis (PDF) ↗`

Do not automatically duplicate large portions of the thesis on the website.

Distill the research story into concise, web-native scientific communication.

---

# 14. Research links

Research-group website:

`https://klipp-linding.science/index.php/`

Luis's research-group profile:

`https://klipp-linding.science/index.php/en/?view=article&id=356:luis-firl&catid=56:92-students`

The group website may occasionally be unavailable because of maintenance / rebuilding.

Do not delete these links merely because a temporary availability check fails.

Recommended placement:

- Research-group link on the signaling-project page.
- Research-group link and Luis's group profile on the About page / research-affiliation area.
- Do not clutter the main navigation with these links.

GitHub profile:

`https://github.com/luisfirl`

Signaling-project repository:

`https://github.com/luisfirl/SignalingProject`

Before making the SignalingProject repository more prominent or exposing additional files from it, remain mindful of unpublished research-data concerns.

---

# 15. Website information architecture

Current core pages:

- `/` — Home
- `/research` — Research interests
- `/projects` — Project overview
- `/projects/signaling-networks` — Ongoing signaling-network research project
- `/about` — Background and links

The website may later include:

- additional research-project pages
- publications
- CV
- software/repositories
- selected scientific visualizations
- ORCID
- Google Scholar
- other academic profiles

Do not create many empty navigation items prematurely.

Add sections when meaningful content exists.

---

# 16. Current content status / known next steps

At the time this `AGENTS.md` was written:

- The main site structure exists.
- The signaling-network project page exists.
- The Master's thesis PDF has been linked from the project page.
- The home page still contains older wording that frames the signaling work too strongly as a Master's-thesis project.
- The `/projects` page still contains older wording that frames the signaling work too strongly as a Master's-thesis project.
- The `/about` page does not yet fully reflect the ongoing research affiliation.
- The `/about` page does not yet include both research-group links.
- The signaling-project page is a good first version but will likely receive later visual and scientific refinements.

A logical next content task is therefore:

1. Update the home-page featured project from "Master's Thesis" to ongoing signaling-network research.
2. Link it directly to `/projects/signaling-networks`.
3. Update `/projects` so the project is presented as ongoing research rather than merely "Theoretical Biophysics / Master's Thesis".
4. Update `/about` to mention the Master's thesis as the origin of continuing research.
5. Add research-affiliation links to `/about`.
6. Re-check site-wide wording for consistency.
7. Later improve the signaling-project page with scientific visualizations and possibly selected figures.

These are recommendations, not immutable requirements.

Follow Luis's newest explicit request if priorities change.

---

# 17. Visual direction

The desired visual language is a mixture of:

- academic
- modern
- technical / computational
- restrained
- research-focused

A useful shorthand is:

**academic + techy**

The site should feel credible to a scientist first and visually distinctive second.

## Desired characteristics

- generous whitespace
- strong typography
- clean grid structure
- restrained borders and separators
- subtle technical details
- mathematical notation used where meaningful
- scientific diagrams / network motifs where useful
- clear information hierarchy
- responsive design
- visually calm pages
- strong but restrained accent color
- long-form scientific storytelling where appropriate

## Avoid

- generic startup landing-page aesthetics
- flashy SaaS cards everywhere
- excessive gradients
- neon cyberpunk styling
- meaningless decorative dashboards
- stock-photo-heavy academic design
- overly rounded UI everywhere
- excessive pills / badges
- visual clutter
- animations that distract from reading
- corporate consulting-style case studies
- rigid numbered structures such as `01 Problem / 02 Approach / 03 Results` as the dominant research-page layout

Luis specifically did not like a rigid numbered portfolio/case-study structure for the signaling project.

Prefer a scientific long-form narrative where text, equations, diagrams, and results flow naturally through the page.

---

# 18. Animation direction

The website is intentionally built with Astro so that richer visual elements can be added later.

Animations are welcome when they support scientific meaning, especially ideas such as:

- signaling-network activity
- dynamic trajectories
- propagation through biological networks
- particles / nodes / edges
- model states changing over time
- temporal processes
- dependency propagation

However, animations should be subtle and optional rather than defining the basic usability of the site.

When adding animation:

- keep important content available without JavaScript where practical
- respect `prefers-reduced-motion`
- avoid large dependencies for trivial effects
- prioritize performance
- avoid distracting continuous motion behind long text
- prefer scientifically meaningful motion over decorative motion
- keep mobile performance in mind

Do not introduce React, Vue, Svelte, or another frontend framework only for simple animations unless there is a strong technical reason.

Astro + CSS + vanilla JavaScript is preferred for lightweight interactions.

---

# 19. Scientific visualizations

Visuals should help explain research rather than simply decorate pages.

Good candidates include:

- simplified kinase-network diagrams
- dependency-flow diagrams
- ODE / kinetic-state diagrams
- experimental vs simulated trajectories
- conceptual data → inference → dynamics pipelines
- perturbation diagrams
- parameter-identifiability visualizations
- temporal signaling diagrams

When reusing material from the Master's thesis or collaborators, verify that it is appropriate to publish.

Prefer recreating simplified explanatory diagrams for the website when copyright, confidentiality, readability, or visual consistency is uncertain.

Do not publish unpublished collaborator figures or raw experimental plots without explicit approval.

---

# 20. Public writing style

Website copy should normally be written in **English**.

Desired tone:

- scientifically precise
- concise
- confident but not inflated
- readable by adjacent-field scientists
- technically sophisticated without unnecessary jargon
- clear about uncertainty and limitations

Avoid exaggerated language such as:

- revolutionary
- groundbreaking
- cutting-edge
- world-class
- state-of-the-art

unless objectively supported and genuinely necessary.

Do not oversell results.

Prefer explaining what was:

- modeled
- inferred
- tested
- compared
- simulated
- observed
- learned

## Scientific accuracy rule

Never invent:

- experimental results
- publication status
- collaborators
- numerical performance
- biological conclusions
- methods that have not actually been implemented
- affiliations
- employment relationships
- future publication details

If something is uncertain, either use cautious wording or ask Luis.

---

# 21. Master's thesis vs ongoing project wording

This distinction is important across the entire website.

## Good

> The project originated from my Master's thesis in the Theoretical Biophysics group of Prof. Edda Klipp at Humboldt-Universität zu Berlin and is currently being developed further as part of an ongoing research collaboration.

## Avoid

> My Master's thesis project investigates ...

when referring to the current project as a whole.

## Good labels

- Ongoing Research
- Current Research
- Systems Biology
- Theoretical Biophysics
- Dynamic Signaling Models

## Avoid using as the primary current-project label

- Master's Thesis

The thesis can and should still be clearly mentioned and linked.

---

# 22. Technical stack

Current stack:

- Astro `^7.2.10`
- Node.js `>=22.12.0`
- standard Astro components
- CSS
- minimal client-side JavaScript
- GitHub Pages
- GitHub Actions

Do not add frameworks or dependencies without a clear benefit.

Before adding a package, consider whether the feature can be implemented cleanly with:

- Astro
- HTML
- CSS
- a small amount of vanilla JavaScript

Keep the dependency footprint small.

---

# 23. Current repository structure

Approximate relevant structure:

```text
.
├── .github/
│   └── workflows/
│       └── deploy.yml
├── public/
│   ├── files/
│   │   └── luis-firl-master-thesis.pdf
│   └── ...
├── src/
│   ├── components/
│   │   ├── Header.astro
│   │   └── Footer.astro
│   ├── layouts/
│   │   └── Layout.astro
│   ├── pages/
│   │   ├── index.astro
│   │   ├── research.astro
│   │   ├── projects.astro
│   │   ├── projects/
│   │   │   └── signaling-networks.astro
│   │   └── about.astro
│   └── styles/
│       └── global.css
├── AGENTS.md
├── astro.config.mjs
├── package.json
└── README.md
```

Inspect the repository rather than assuming this structure is unchanged in the future.

The repository state is the source of truth for the actual file layout.

---

# 24. Astro architecture guidance

Use Astro's strengths:

- static content by default
- components for repeated UI
- minimal JavaScript
- simple file-based routing
- reusable layouts
- strong static-site performance

Avoid duplicating large CSS or markup blocks across many pages when a reusable component would clearly improve maintainability.

However, do not over-componentize tiny one-off pieces simply for abstraction's sake.

If a pattern appears repeatedly across pages, consider extracting it into a component.

Potential future components may include:

- `ProjectCard.astro`
- `ResearchLink.astro`
- `SectionHeading.astro`
- scientific diagram components
- reusable external-link components
- research metadata components

Do not refactor aggressively while implementing an unrelated small request.

Keep changes focused.

---

# 25. Styling conventions

Global visual tokens live in:

`src/styles/global.css`

Prefer using existing CSS variables such as:

- `--background`
- `--surface`
- `--text`
- `--muted`
- `--border`
- `--accent`
- `--accent-soft`
- `--max-width`

Do not scatter hard-coded near-identical colors throughout the codebase if a global token is more appropriate.

Maintain the current restrained palette unless Luis explicitly asks for a redesign.

Use responsive units and `clamp()` where appropriate.

Keep mobile layouts intentional rather than merely allowing desktop layouts to collapse accidentally.

Prefer clear CSS over unnecessary abstraction.

---

# 26. Accessibility

New UI should be accessible by default.

Requirements:

- semantic HTML where possible
- meaningful heading hierarchy
- descriptive link text
- sufficient color contrast
- keyboard-accessible interactive elements
- `alt` text for meaningful images
- decorative graphics should not create unnecessary screen-reader noise
- external links opened with `target="_blank"` should use `rel="noreferrer"` or an appropriate equivalent
- respect `prefers-reduced-motion` for substantial animation

Avoid using visual styling alone to communicate important scientific distinctions.

---

# 27. SEO and metadata

Each public page should have an informative title and description through the shared layout.

Prioritize human-readable scientific titles rather than keyword stuffing.

Production site URL is configured as:

`https://luisfirl.com`

Do not change it back to the GitHub Pages subdomain unless explicitly requested.

Potential future improvements include:

- Open Graph metadata
- canonical URLs
- structured data
- sitemap
- publication metadata
- social preview images

Implement these incrementally rather than prematurely overengineering SEO.

---

# 28. Development workflow

Install dependencies:

```bash
npm install
```

Run local development server:

```bash
npm run dev
```

Production build:

```bash
npm run build
```

Preview production build when useful:

```bash
npm run preview
```

Agents working in environments that support background processes may use a background development server when useful.

Do not assume a globally installed `astro` executable.

Prefer project-local commands such as:

```bash
npm run dev
```

or:

```bash
npm run astro -- ...
```

---

# 29. Validation requirements

After meaningful code changes:

1. Run `npm run build`.
2. Fix build errors before considering the task complete.
3. If browser access is available, inspect the affected page visually.
4. Check both desktop and narrow/mobile layout for substantial UI changes.
5. Confirm important internal links resolve to valid routes.
6. For changes to static files, confirm paths use the correct `/public` URL convention.
7. Check for obvious overflow issues around equations and scientific diagrams.

For example:

```text
public/files/luis-firl-master-thesis.pdf
```

is linked publicly as:

```text
/files/luis-firl-master-thesis.pdf
```

Do not use:

```text
/public/files/...
```

in browser URLs.

---

# 30. Git and change-management guidance

Keep changes focused and understandable.

Before editing:

- inspect the relevant files
- understand existing patterns
- check current repository status when possible
- avoid overwriting unrelated work

After editing:

- inspect the diff
- run the production build
- summarize what changed

Do not perform destructive Git operations unless explicitly requested.

Avoid commands such as:

```bash
git reset --hard
```

destructive force pushes, or deleting branches containing unreviewed work.

If working in a cloud-agent environment that uses branches and pull requests, prefer a focused branch / PR and allow Luis to review before merge.

If Luis explicitly asks for a direct commit or direct push, follow that request.

Use concise commit messages describing the actual change, for example:

- `Refine signaling research project page`
- `Update ongoing research project links`
- `Improve responsive project layout`
- `Add research affiliation to about page`
- `Add scientific project visualization`

Do not mix unrelated large changes into a single commit when avoidable.

---

# 31. Deployment

Deployment is handled by GitHub Actions and GitHub Pages.

The deployment workflow lives under:

`.github/workflows/deploy.yml`

Pushes to `main` trigger the site build and deployment.

The custom production domain is:

`https://luisfirl.com`

Do not reconfigure DNS, GitHub Pages, Cloudflare, or the custom domain during ordinary website-development tasks.

If deployment fails:

1. Check the GitHub Actions workflow run.
2. Distinguish build errors from deployment / Pages errors.
3. Inspect the actual failed step.
4. Do not change DNS settings to fix an Astro build error.

---

# 32. Collaboration behavior for AI agents

Luis wants agents to reduce manual copy/paste and perform repository changes directly when possible.

When given a clear implementation request:

1. inspect the repository
2. inspect relevant existing files
3. make the changes
4. run appropriate validation
5. visually inspect the result when possible
6. report what changed
7. mention any important unresolved issue

Do not unnecessarily respond with large blocks of code for Luis to paste manually if the environment allows direct repository modification.

Ask a clarifying question only when ambiguity materially affects:

- scientific accuracy
- design direction
- research-data confidentiality
- public claims
- destructive operations
- publication status

For small aesthetic decisions, make a reasonable choice consistent with this file and show the result for review.

---

# 33. User experience when explaining terminal commands

Luis is still becoming familiar with Git and terminal workflows.

If instructions must be given manually, explain whether a command:

- runs immediately and returns
- starts a long-running process
- opens an interactive pager/editor
- requires a specific exit command

Prefer commands that do not unexpectedly open pagers or editors.

For diffs, prefer:

```bash
git --no-pager diff
```

rather than a command that may leave the user inside `less` without explanation.

For a long-running development server, explicitly state that it remains active and can be stopped with:

```text
Ctrl+C
```

Whenever direct agent execution is available, prefer doing the work rather than asking Luis to copy and paste terminal commands.

---

# 34. Design review philosophy

The current site is intentionally an early foundation.

Do not assume current layout choices are final.

Luis is happy to iterate later on:

- spacing
- typography
- colors
- scientific diagrams
- animation
- section structure
- equations
- responsive behavior
- project visualizations

However, preserve the overall research-first direction unless explicitly asked to redesign it.

Make improvements incrementally so that changes are easy to evaluate and revert.

A working but simple scientific page is preferable to an overengineered page that is difficult to maintain.

---

# 35. Content hierarchy for the signaling-network page

The project page should broadly communicate the following scientific story, but headings and visual structure may evolve.

## Research context

Why dynamic kinase signaling requires quantitative / systems-level modeling.

## From experimental data to network dynamics

Time-resolved phosphoproteomics provides dynamic observations used to inform the model.

## Dependency inference

Infer relative signaling dependencies using constrained mathematical optimization.

## Mechanistic dynamics

Embed inferred dependencies into a mechanistic ODE system describing biological kinetic processes.

## Parameter inference and identifiability

Emphasize that reproducing observed data does not guarantee unique biologically correct parameters.

## Current model development

Explain that Luis is actively improving kinetic parameter estimation and scalability.

## Toward predictive signaling models

Connect the work to:

- perturbation analysis
- additional biophysical constraints
- experimental validation
- larger networks
- future scientific ML approaches

Do not force these into a numbered `01 / 02 / 03` visual sequence.

---

# 36. Project-page visual hierarchy

For research-project pages, favor a long-form scientific layout using combinations of:

- concise explanatory text
- large scientific statements
- equations
- conceptual diagrams
- selected plots
- whitespace
- subtle separators
- small metadata elements

A possible visual rhythm is:

`context → model concept → mathematics → dynamics → scientific insight → current work → outlook`

This should feel more like an elegant interactive research explanation than a corporate case study.

The scientific argument should determine the page structure.

---

# 37. Mathematical content presentation

Mathematical content is encouraged when it genuinely helps explain the research.

Do not hide all mathematics merely to make the site superficially simpler.

At the same time, avoid reproducing full thesis derivations.

The ideal level is:

- show the core equation or relationship
- explain what the terms mean
- explain why the equation matters scientifically
- connect it to the next modeling stage

For example:

```text
experimental trajectories
        ↓
dependency parameters α, β
        ↓
signaling activity
        ↓
ODE phosphorylation terms
        ↓
dynamic network trajectories
```

Mathematics should reinforce the scientific narrative rather than function as decoration.

---

# 38. Results presentation

Do not turn the website into a compressed Results chapter of the Master's thesis.

Prefer a few important scientific insights.

Examples of appropriate themes include:

## Dynamic reconstruction

The coupled dynamic model can reproduce important temporal trends observed in experimental phosphoproteomic measurements.

## Parameter identifiability

Different parameter configurations can explain experimental observations similarly well, motivating additional biological / biophysical constraints.

## Perturbation analysis

The dynamic framework enables in-silico investigation of targeted changes to signaling components and network responses.

Avoid presenting every figure, benchmark, or numerical detail from the thesis.

Use selected evidence.

---

# 39. Current research should be visibly current

The website should make it obvious that the signaling project is still active.

A reader should not leave the page thinking:

> This was a Master's project that ended in 2026.

Instead they should understand:

> This research began during the Master's thesis and is now being developed further.

The "Current work" or equivalent section should therefore remain meaningful and visible.

As the project evolves, update this section.

If a paper is eventually submitted or published, update the project timeline and `AGENTS.md`.

---

# 40. Future portfolio projects

The website is expected to grow beyond the signaling project.

Future projects may demonstrate skills such as:

- neural ODEs
- differentiable modeling
- physics-informed / biology-informed learning
- generative modeling
- molecular machine learning
- graph neural networks
- Bayesian optimization
- active learning
- reproduction / extension of Scientific ML papers

Do not create fictional completed projects.

When a future project is genuinely started, present it with the same principles as the signaling project:

`scientific problem → method → evidence → interpretation → reproducibility`

not merely a technology list.

---

# 41. Repository and research reproducibility philosophy

The website should eventually connect readers to high-quality research repositories.

For scientific repositories, desirable practices include where appropriate:

- clear README
- reproducible environment
- meaningful project structure
- documented data requirements
- scripts or notebooks with defined purpose
- citations / references
- license when appropriate
- `CITATION.cff` when appropriate
- clear distinction between public and non-public data

Do not publish research data simply to make a repository appear complete.

Reproducibility must respect confidentiality and collaborator agreements.

---

# 42. GitHub as evidence

The website is the curated scientific narrative.

GitHub should provide supporting evidence.

A useful conceptual distinction is:

```text
Website
→ What was the scientific question?
→ Why does it matter?
→ What modeling approach was used?
→ What was learned?

GitHub
→ How was it implemented?
→ How is the project structured?
→ Can the work be inspected or reproduced?
```

Do not overload the website with implementation details that are better placed in a repository README.

At the same time, do not let GitHub repositories remain undocumented if they are linked prominently from the website.

---

# 43. About-page direction

The About page should not become an autobiography.

It should provide concise context around Luis's research path.

Relevant themes:

- interdisciplinary Life Science Engineering background
- movement toward mathematical / computational biology
- Master's thesis in Theoretical Biophysics
- continued research on dynamic signaling models
- interest in mechanistic modeling + scientific ML

The About page should eventually include a compact research-affiliation / external-links area containing:

- GitHub
- Research Group
- Research Group Profile
- later possibly ORCID
- later possibly Google Scholar
- later possibly CV

Avoid excessive personal detail unless Luis explicitly asks for it.

---

# 44. Home-page direction

The home page is the highest-priority page for first-time visitors.

It should answer quickly:

- Who is Luis?
- What does he research?
- What methods interest him?
- What is his main current project?
- Where can I learn more?

The main signaling project should eventually be shown as **ongoing research**, not as simply "Master's Thesis".

A homepage visitor should be able to reach:

`/projects/signaling-networks`

directly from the featured project area.

Keep the homepage concise.

Do not duplicate the entire project page.

---

# 45. Research-page direction

The `/research` page is for broad research interests and intellectual positioning.

It should explain areas such as:

- Systems Biology
- Theoretical Biophysics
- Scientific Machine Learning
- Computational / Mechanistic Modeling

It should not simply duplicate `/projects`.

Conceptually:

```text
/research
→ what kinds of scientific questions interest Luis

/projects
→ what Luis has actually worked on

/projects/signaling-networks
→ detailed evidence for one research project
```

Maintain this distinction.

---

# 46. Projects-page direction

The `/projects` page should function as a concise research-project index.

The signaling project should be presented as:

- ongoing research
- active model development
- systems biology / theoretical biophysics
- linked to the detailed project page

Do not describe it primarily as "Master's Thesis".

Future projects can be added when they contain meaningful work.

Avoid filling the page with placeholder projects simply to make it look larger.

One excellent project is better than several vague placeholders.

---

# 47. Scientific machine learning positioning

Scientific ML is an important future direction for Luis's profile.

However, do not artificially relabel classical numerical optimization or ODE modeling as AI merely to make the profile sound more ML-heavy.

Instead build a credible progression:

```text
mechanistic modeling
        +
parameter inference
        +
dynamical systems
        ↓
scientific machine learning
```

As Luis completes genuine ML-based research projects, they can become increasingly prominent.

Credibility is more important than buzzwords.

---

# 48. AI/ML project strategy

Future portfolio work should ideally demonstrate that Luis can connect modern ML methods to scientific questions.

Strong project directions may include:

- Neural ODEs for biological dynamical systems
- differentiable mechanistic modeling
- hybrid mechanistic / neural models
- reproduction and extension of a Scientific ML paper
- graph-based modeling of biological or molecular systems
- physics-informed or biology-informed models
- probabilistic inference for dynamical systems

These are strategic directions, not current accomplishments.

Do not present them as completed unless implemented.

---

# 49. Performance

The site should remain fast.

Prefer:

- static HTML
- optimized images
- lightweight scripts
- lazy-loading where appropriate
- small dependency footprint

Be cautious with:

- large animation libraries
- large JavaScript frameworks
- WebGL
- large client-side datasets
- unnecessary font downloads

If adding a computational visualization, ensure it has a clear scientific benefit.

---

# 50. Responsive design

Every meaningful UI change should work on desktop and mobile.

Pay particular attention to:

- long research titles
- mathematical equations
- navigation
- multi-column research layouts
- diagrams
- external links
- project metadata

Equations may use horizontal scrolling if necessary, but avoid breaking the entire page width.

Scientific diagrams should simplify gracefully on narrow screens.

---

# 51. External-link behavior

External research links should generally:

- use clear labels
- open in a new tab when appropriate
- use `rel="noreferrer"` with `target="_blank"`

Avoid displaying long raw URLs in the public UI unless there is a specific reason.

Preferred labels include:

- `Research Group ↗`
- `Group Profile ↗`
- `GitHub ↗`
- `Read Master's Thesis (PDF) ↗`

---

# 52. Content claims about collaboration

Be precise when describing collaborations.

Safe phrasing may include:

- ongoing research collaboration
- research carried out in the Theoretical Biophysics research environment
- working with collaborators involved in the experimental research
- developing the scientific framework for a future publication

Do not imply:

- formal employment
- formal lab membership beyond known status
- authorship agreements
- publication guarantees
- finalized consortium structure

unless Luis explicitly provides that information.

---

# 53. What not to infer

Do not infer or state without confirmation:

- that Luis is currently enrolled as a PhD student
- that a future paper has been submitted
- that a future paper has a fixed author list
- that a model has been experimentally validated if it has not
- that current model improvements have produced specific new results
- that all code/data in the thesis can be published freely
- that a research-group relationship has a formal employment status unless stated
- that a specific future ML method has already been implemented
- that temporary research-group website downtime means the affiliation or URLs are obsolete

---

# 54. Source-of-truth priority

When information conflicts, follow this order:

1. Luis's newest explicit instruction.
2. Current repository state.
3. This `AGENTS.md` project context.
4. Older website copy or placeholder content.

This file is intended to preserve project direction, not override future decisions.

If Luis changes:

- research status
- publication status
- affiliations
- design preferences
- technical architecture
- project priorities

update `AGENTS.md` accordingly so future agents receive current context.

---

# 55. When to ask Luis before making a change

Ask before proceeding if a proposed change would:

- expose unpublished data
- publish new scientific results
- claim publication status
- change scientific conclusions
- significantly reinterpret the Master's research
- change affiliation wording in a potentially misleading way
- remove major content
- substantially redesign the visual identity
- add a major framework or dependency
- alter deployment / DNS / GitHub Pages configuration
- perform destructive Git operations

For ordinary layout, copy, CSS, accessibility, responsiveness, or component improvements, make a reasonable implementation and present it for review.

---

# 56. Agent autonomy

When an agent has repository access, Luis prefers the agent to **do the work directly**.

Do not default to instructions such as:

> Create a file and paste this code.

Instead:

1. inspect the repository
2. edit the file
3. run the build
4. inspect the result
5. report back

If the platform requires a PR, create or update the working branch / PR.

If the agent cannot write because of permissions, explain the limitation clearly and provide the smallest necessary manual step.

---

# 57. Browser-based visual testing

If the agent environment provides a browser:

- start the Astro development server
- open the affected page
- check desktop layout
- check a narrow/mobile viewport
- look for overflow
- verify links
- inspect alignment and spacing
- inspect equations and diagrams

For visual design tasks, do not rely only on a successful compiler/build.

A technically valid page may still look poor.

---

# 58. Current visual baseline

The current visual system is intentionally simple.

Core ideas currently include:

- light neutral background
- white / light surface sections
- dark graphite/navy-like text
- restrained blue/teal accent
- monospaced labels for technical metadata
- large sans-serif headings
- thin borders
- generous spacing

Future improvements can refine this visual system.

Do not introduce a completely different visual identity without Luis's request.

---

# 59. Long-term website ambition

The website should gradually become a polished academic research identity rather than remain a static CV page.

Possible future features include:

- interactive scientific network visualizations
- selected model trajectories
- animated signaling diagrams
- publications
- CV
- project timelines
- project-specific methodology diagrams
- links to reproducible research repositories
- ORCID / Scholar integrations
- subtle dark mode if desired later

These should be added because they strengthen the scientific presentation, not simply because they are technically possible.

---

# 60. Definition of a good contribution

A good change to this repository should usually satisfy most of the following:

- scientifically accurate
- visually restrained and polished
- clearly connected to Luis's research identity
- responsive
- accessible
- performant
- easy to maintain
- successfully builds with Astro
- does not expose private or unpublished material accidentally
- does not overstate Luis's research status or results
- makes the site more useful to researchers evaluating Luis's work

When in doubt, optimize for:

**scientific credibility, clarity, and depth**

rather than visual spectacle.
