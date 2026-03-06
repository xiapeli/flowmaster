<div align="center">

# FlowMaster

**Product evolution studio for Claude Code. Visualize, plan, and evolve products with AI.**

[![MIT License](https://img.shields.io/badge/License-MIT-gold.svg?style=for-the-badge)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-5A45FF?style=for-the-badge)](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview)
[![Version](https://img.shields.io/badge/Version-4.0-22c55e?style=for-the-badge)]()

*Two modes. One tool. From first scan to shipped product.*

[Quick Start](#quick-start) &#8226; [Features](#features) &#8226; [How It Works](#how-it-works) &#8226; [Examples](#examples)

</div>

---

## What It Does

FlowMaster turns Claude Code into a product development studio. Point it at any codebase and it scans every screen, maps every navigation path, and generates interactive flow visualizations you can drag, zoom, and share.

It works in two modes:

| | Analyze (v3.1) | Studio (v4.0) |
|---|---|---|
| **Purpose** | Quick architecture snapshot | Full product evolution |
| **Output** | Static HTML or JSON | Interactive studio with persistence |
| **Input** | Codebase scan | Codebase + voice + screenshots + git |
| **Best for** | Documentation, onboarding | Product planning, team collaboration |

## Features

### Code Intelligence

- Scans Swift, Kotlin, React, Flutter, and Next.js codebases
- Detects navigation patterns automatically (NavigationLink, sheet, fullScreenCover, TabView, useRouter, NavHost, Navigator)
- Extracts features, integrations, and status from every screen
- Identifies UX gaps: dead ends, orphan screens, broken flows, missing feedback

### Interactive Visualization

- Node-based flow diagrams powered by [@xyflow/react](https://github.com/xyflow/xyflow)
- Draggable cards with rich detail (features, integrations, status badges)
- SmoothStep edges with descriptive labels
- Color-coded nodes by type (entry, router, tab, flow, modal, sheet, detail, settings)
- Auto-layout algorithm with guaranteed zero overlap

### Studio Mode (v4.0)

- Interactive canvas with terminal integration (`Cmd+/`)
- Voice comments via Web Speech API
- Screenshot upload and preview
- Git push/pull with auto-save and auto-commit
- Multi-select cards with shared context
- Undo/Redo (`Cmd+Z` / `Cmd+Shift+Z`)
- Local-first persistence (`~/.flowmaster/flows/`)

### Product Analysis

- **Onboarding audit**: time to value, permission timing, aha moment detection
- **Engagement hooks**: streaks, progress tracking, gamification, social proof
- **Retention analysis**: triggers, variable rewards, investment loops (Hooked Model)
- Prioritized recommendations backed by product frameworks (Teresa Torres, Nir Eyal, Nielsen, BJ Fogg)

## Quick Start

### 1. Install

```bash
# Copy the skill file to your Claude Code commands folder
curl -sL https://raw.githubusercontent.com/xiapeli/flowmaster/main/flowmaster.md \
  -o ~/.claude/commands/flowmaster.md
```

Or clone and copy:

```bash
git clone https://github.com/xiapeli/flowmaster.git
cp flowmaster/flowmaster.md ~/.claude/commands/
```

### 2. Analyze a codebase

Open Claude Code in any project directory and run:

```
/flowmaster analyze
```

FlowMaster scans every view, maps navigation paths, and generates an interactive flow diagram at `http://localhost:3000`.

### 3. Launch the full studio

```
/flowmaster studio
```

This creates a persistent project with canvas, terminal, voice, screenshots, and git sync.

## How It Works

```
                    FLOWMASTER PIPELINE

  SCAN ────> ANALYZE ────> GENERATE ────> AUDIT ────> RECOMMEND
    |           |             |             |             |
    v           v             v             v             v
  Views      UX Gaps      flow-viewer    Hooks       Action Items
  + Nav      + Flows      + React       Analysis     + Priority
  + Types    + Dead Ends  + xyflow      + Hooked     + File Locations
```

**Scan.** Finds all views/screens in your project. Extracts struct names, file paths, view types, features, and integrations.

**Analyze.** Maps navigation between screens. Detects UX gaps: dead ends, orphan screens, navigation depth > 3 taps, missing error recovery.

**Generate.** Creates a React + @xyflow/react visualization with rich cards, color-coded by screen type, with guaranteed non-overlapping layout.

**Audit.** Evaluates adoption hooks (onboarding, engagement, retention) using established product frameworks.

**Recommend.** Produces prioritized action items with specific file locations and framework citations.

## Commands

| Command | Description |
|---------|-------------|
| `/flowmaster` | Show help and current status |
| `/flowmaster analyze` | Scan codebase and generate detailed analysis |
| `/flowmaster generate` | Create interactive flow visualization (opens in browser) |
| `/flowmaster studio` | Launch full v4.0 studio with persistence and git sync |
| `/flowmaster audit` | Deep UX audit with adoption hook analysis |

## Node Types

Each screen in the flow is color-coded by its role in the architecture:

| Type | Color | Role |
|------|-------|------|
| Entry | `#22c55e` green | App launch, entry points |
| Router | `#10b981` teal | ContentView, route decisions |
| Main | `#f59e0b` amber | MainTabView, primary containers |
| Tab | `#f59e0b` amber | Tab content views |
| Flow | `#8b5cf6` violet | Onboarding, wizards, multi-step |
| Modal | `#ec4899` pink | fullScreenCover, modal presentations |
| Sheet | `#14b8a6` teal | .sheet, side panels |
| Detail | `#6b7280` gray | Detail views, push navigation |
| Settings | `#64748b` slate | Settings, preferences |
| Component | `#71717a` zinc | Internal reusable components |

## Supported Platforms

| Platform | Navigation Patterns Detected |
|----------|------------------------------|
| iOS (SwiftUI) | NavigationLink, sheet, fullScreenCover, TabView |
| iOS (UIKit) | Storyboard segues, programmatic navigation |
| Android (Compose) | NavHost, navigation-compose |
| React / Next.js | useRouter, Link, pages directory |
| Flutter | Navigator, go_router |

## Output Structure

```
project/
  flow-viewer/              # Interactive React app
    src/
      App.jsx               # Nodes, edges, and layout
      ScreenNode.jsx         # Custom node component with Handles
      styles.css             # Flow styling
    package.json
    vite.config.js
    index.html
  FLOW_ANALYSIS.md           # Full analysis report with recommendations
```

Studio mode (v4.0) adds persistent project storage:

```
~/.flowmaster/flows/<project>/
  flow.json                 # Nodes and edges (auto-saved)
  comments.json             # Voice and text comments
  assets/                   # Screenshots and attachments
```

## Examples

### Analyze an iOS app

```
> /flowmaster analyze

Scanning project...
Found 42 views across 5 modules.
Generating flow visualization...

Flow viewer running at http://localhost:3000
  42 screens mapped
  67 navigation edges
  3 dead ends detected
  2 orphan screens found
```

### Launch studio for product planning

```
> /flowmaster studio

FlowMaster Studio v4.0
Project: my-app
Server: http://localhost:3141

Shortcuts:
  Cmd+/          Toggle terminal
  Shift+Click    Multi-select cards
  Cmd+Z          Undo
  Delete          Remove selected
```

### Export architecture documentation

```
> /flowmaster analyze --format=json --output=docs/architecture.json
> /flowmaster analyze --output=docs/flow.html
```

## Design Principles

1. **Code is truth.** Scans real source files, not assumptions or stale documentation.
2. **Frameworks over opinions.** Every recommendation cites a published framework or heuristic.
3. **Visual first.** See the whole product narrative before diving into code.
4. **Zero overlap.** Layout algorithm guarantees cards never stack or clip (min 420px horizontal, 380px vertical spacing).
5. **Close the loop.** Generate, execute, verify, fix. Repeat until zero errors.

## Frameworks Behind the Analysis

FlowMaster's product audit draws on:

- [Teresa Torres](https://www.producttalk.org/) -- Continuous Discovery Habits
- [Nir Eyal](https://www.nirandfar.com/hooked/) -- Hooked Model (trigger, action, variable reward, investment)
- [Jakob Nielsen](https://www.nngroup.com/) -- 10 Usability Heuristics
- [Steve Krug](https://sensible.com/) -- Don't Make Me Think
- [BJ Fogg](https://behaviormodel.org/) -- Behavior Model (motivation, ability, prompt)
- [Sean Ellis](https://growthengineers.com/) -- Growth Hacking / Product-Market Fit
- [Apple HIG](https://developer.apple.com/design/human-interface-guidelines/) -- Human Interface Guidelines

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview) CLI
- Node.js >= 18 (for the flow viewer React app)

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

[MIT](LICENSE)

---

<div align="center">

*"Every screen tells a story. FlowMaster shows the whole narrative."*

**[Phelipe Xavier](https://github.com/xiapeli)**

</div>
