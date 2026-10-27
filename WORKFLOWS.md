# Project workflows

These diagrams show what a visitor should understand quickly: the inputs, decisions, human involvement, and result. **Delivered work, pilots, public code, and concept designs are labeled separately.** The diagrams summarize the linked case studies or repositories; they are not exports of private production systems.

## GenAI campaign workflow — delivered implementation

The public case study contains a separate, more detailed *proposed creative route*. This diagram covers only the implementation steps described for the n8n proof of concept, pilot, and rollout.

```mermaid
flowchart LR
    A[Find a repeatable campaign task] --> B[Build n8n proof of concept]
    B --> C[Run controlled pilot]
    C --> D1[2 AI-assisted locations]
    C --> D2[2 comparison locations]
    D1 --> E[Compare production time and audience response]
    D2 --> E
    E --> F[Human approval and data minimization]
    F --> G[Adoption workshop]
    G --> H[Roll out to 4 DACH locations]
```

The reported standard campaign cycle moved from about two weeks to one in the pilot. The exact internal automation steps are not public, so the diagram does not present a node-by-node n8n export. [Read the case study](https://sittanbon.github.io/genai-workflow-case-study.html).

## AI Expense Intelligence — internal pilot decision flow

The pilot tested receipt OCR and confidence-based routing. The broader finance dashboard shown in the case study is a product concept.

```mermaid
flowchart TD
    A[Capture receipt evidence] --> B[Extract fields with OCR]
    B --> C[Propose transaction match]
    C --> D{Confidence score}
    D -->|Below 75 percent| E[Reject or recapture evidence]
    D -->|75 to 95 percent| F[Finance specialist reviews]
    D -->|Above 95 percent| G{Bill above THB 20,000?}
    G -->|Yes| F
    G -->|No| H[Green route, notify human, keep audit log]
    F --> I[Confirm or correct decision]
```

The thresholds describe Bon's stated pilot policy, including human review at exactly 75%. The case-study confidence factors and interface wireframes illustrate a possible product design; their precise weights are not claimed as pilot settings. [Read the case study](https://sittanbon.github.io/finance-ai-case-study.html).

## Prompt Smash! — public application flow

The four learning journeys share one React and TypeScript interaction engine. A pure assembler turns the learner's answers into the live prompt; required Goal and Task fields must be present before copy or download.

```mermaid
flowchart LR
    A[Choose one of 4 journeys] --> B[Build 7 prompt layers]
    B --> C[Assemble live prompt]
    C --> D[Techniques, testing and exercises]
    D --> E[BITE review]
    E --> F[Responsible-AI review]
    F --> G[Copy or download prompt]
    B -. save locally .-> H[Browser storage]
    H -. restore .-> B
```

The responsible-AI review asks the learner to check risk, injection, hallucination, bias, and data protection; it does not declare a prompt safe. The browser stores drafts locally. [Try Prompt Smash!](https://sittanbon.github.io/prompt-smash/) · [Read the code](https://github.com/SittanBon/prompt-smash).

## Mochi Pop — public game loop


Mochi Pop is a playable Expo and React Native project with a browser preview. The core loop connects tactile play to pet care and progression; state is saved locally. The leaderboard is optional and requires Firebase configuration.


```mermaid
flowchart LR
    A[Pop mochi or care for pet] --> B[Game rules update taps, needs and activity]
    B --> C[Earn candy and XP]
    C --> D[Grow, reach milestones and unlock looks]
    D --> E[Save progress on device]
    E --> F[Return to play]
    F --> A
    E -. if Firebase is configured .-> G[Optional live leaderboard]
```


The browser preview uses a short stroll instead of the phone step counter, and vibration depends on browser support. Future quests, teams and app-store release are not presented as shipped features. [Play the browser preview](https://sittanbon.github.io/mochi-pop/) · [Read the code](https://github.com/SittanBon/mochi-pop).


## Bierpreis — public price-reporting flow

This is the flow implemented in the public React front end and Express API. Submitted information stays pending until an administrator reviews it.

```mermaid
flowchart LR
    A[Visitor explores Munich venue map] --> B[Report price or venue information]
    B --> C[Validate form and API input]
    C --> D[Normalize serving size and flag unusual price]
    D --> E[(SQLite pending submission)]
    E --> F{Admin review}
    F -->|Reject| G[Record reason and log action]
    F -->|Approve| H[Apply relevant change and record provenance]
    H --> I[Refresh public venue, price history and stats]
```

The app also supports search, filters, price freshness, trends, bilingual content, and data-quality review. A flag is a review signal, not an automatic rejection. [Read the code](https://github.com/SittanBon/muenchner-bierpreis).

## QR Event Management — pilot and learning loop

The QR product was piloted internally and licensed to five market competitors. CRM, live streaming, gamification, rewards, and the dashboard on the case-study page are a separate design exploration.

```mermaid
flowchart LR
    A[Internal QR event pilot] --> B[License product to 5 market competitors]
    B --> C[Gather usage data and feedback]
    C --> D[Improve QR product]
    D --> C
```

[Read the case study](https://sittanbon.github.io/event-engagement-case-study.html).

## Portfolio website — public build flow

The portfolio itself is a static GitHub Pages project. Editable page fragments are assembled into visitor-facing pages with shared navigation, metadata, styles, and scripts.

```mermaid
flowchart LR
    A[Page fragments in src] --> B[Node build script]
    C[Shared CSS and JavaScript] --> B
    B --> D[Static HTML pages and case studies]
    D --> E[Structure and link checks]
    E --> F[GitHub Pages]
```

[Explore the portfolio](https://sittanbon.github.io/) · [Read the repository](https://github.com/SittanBon/sittanbon.github.io).
