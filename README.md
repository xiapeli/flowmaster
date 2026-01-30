# FlowMaster

```
███████╗██╗      ██████╗ ██╗    ██╗███╗   ███╗ █████╗ ███████╗████████╗███████╗██████╗
██╔════╝██║     ██╔═══██╗██║    ██║████╗ ████║██╔══██╗██╔════╝╚══██╔══╝██╔════╝██╔══██╗
█████╗  ██║     ██║   ██║██║ █╗ ██║██╔████╔██║███████║███████╗   ██║   █████╗  ██████╔╝
██╔══╝  ██║     ██║   ██║██║███╗██║██║╚██╔╝██║██╔══██║╚════██║   ██║   ██╔══╝  ██╔══██╗
██║     ███████╗╚██████╔╝╚███╔███╔╝██║ ╚═╝ ██║██║  ██║███████║   ██║   ███████╗██║  ██║
╚═╝     ╚══════╝ ╚═════╝  ╚══╝╚══╝ ╚═╝     ╚═╝╚═╝  ╚═╝╚══════╝   ╚═╝   ╚══════╝╚═╝  ╚═╝
```

> "Every screen tells a story. FlowMaster shows the whole narrative."

**AI Agent for App Flow Visualization & UX Analysis** - Generates interactive xyflow diagrams, analyzes adoption hooks, identifies UX gaps, and provides framework-backed recommendations.

## Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        FLOWMASTER PIPELINE                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   SCAN ──► ANALYZE ──► GENERATE ──► AUDIT ──► RECOMMEND            │
│     │         │           │           │           │                │
│     ▼         ▼           ▼           ▼           ▼                │
│   Views    UX Gaps    flow-viewer  Hooks    Action Items           │
│   + Nav    + Flows    + React     Analysis  + Priority             │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

## Agents

| Agent | Model | Specialty |
|-------|-------|-----------|
| **Scanner** | Haiku | Find Views/Screens, parse navigation patterns |
| **Analyzer** | Sonnet | UX gaps, dead ends, orphan screens, broken flows |
| **Generator** | Sonnet | Create React + xyflow visualization |
| **Auditor** | Sonnet | Adoption hooks analysis (onboarding, engagement, retention) |

## Features

### Automatic Flow Generation
- Scans Swift, Kotlin, React, Flutter code
- Detects navigation patterns automatically
- Generates React + xyflow visualization
- Auto-layout with manual override

### Adoption Hooks Analysis
Based on world-class product frameworks:
- **Onboarding**: Time to value, permission timing, aha moment
- **Engagement**: Streaks, progress, gamification, social proof
- **Retention**: Triggers, variable rewards, investment loops

### UX Gap Detection
- Dead ends (screens without clear exit)
- Orphan screens (unreachable code)
- Navigation depth issues (>3 taps)
- Missing feedback (no confirmation on actions)
- Broken flows (error states without recovery)

## Installation

Copy `flowmaster.md` to your Claude Code commands folder:

```bash
cp flowmaster.md ~/.claude/commands/
```

## Usage

```bash
# Analyze your project
/flowmaster analyze

# Generate interactive visualization
/flowmaster generate
# Opens http://localhost:3000

# Deep UX audit with recommendations
/flowmaster audit

# Update after code changes
/flowmaster update
```

## Supported Platforms

| Platform | Detection | Navigation Patterns |
|----------|-----------|---------------------|
| iOS (SwiftUI) | ✅ | NavigationLink, sheet, fullScreenCover, TabView |
| iOS (UIKit) | ✅ | Storyboard segues, programmatic navigation |
| Android (Compose) | ✅ | NavHost, navigation-compose |
| React/Next.js | ✅ | useRouter, Link, pages/ |
| Flutter | ✅ | Navigator, go_router |

## Output

### Interactive Flow Viewer
```
http://localhost:3000

Features:
- Drag to reposition
- Zoom with scroll
- Click for details
- MiniMap navigation
- Color-coded by type
```

### Analysis Report
```
FLOW_ANALYSIS.md
├── Adoption Hooks Analysis
│   ├── Onboarding (7 metrics)
│   ├── Engagement (5 hook types)
│   └── Retention (Hooked Model)
├── UX Gaps (5 categories)
└── Recommendations (prioritized)
```

## Frameworks Integrated

FlowMaster's analysis is backed by:

- **Teresa Torres** - Continuous Discovery
- **Nir Eyal** - Hooked Model
- **Jakob Nielsen** - 10 Usability Heuristics
- **Steve Krug** - Don't Make Me Think
- **BJ Fogg** - Behavior Model
- **Sean Ellis** - Growth Hacking
- **Apple HIG** - Human Interface Guidelines

## Principles

1. **Code is truth** - Scans real code, not assumptions
2. **Frameworks over opinions** - Every recommendation cites a source
3. **Visual first** - See the whole narrative before details
4. **Actionable output** - Prioritized recommendations with file locations

## File Structure

```
~/.claude/commands/
└── flowmaster.md      # Main skill (24KB)

Project output:
├── .flowmaster/
│   └── state.json     # Scan state and analysis
├── flow-viewer/       # React + xyflow project
│   ├── src/
│   │   ├── App.jsx    # Nodes and edges
│   │   └── ...
│   └── package.json
└── FLOW_ANALYSIS.md   # Full analysis report
```

## References

- [xyflow](https://github.com/xyflow/xyflow) - React Flow library
- [Hooked](https://www.nirandfar.com/hooked/) - Nir Eyal
- [Continuous Discovery](https://www.producttalk.org/) - Teresa Torres
- [Nielsen Norman Group](https://www.nngroup.com/) - Usability heuristics

---

**v1.0.0** | Created with [LIBERDADE](https://github.com/pheeliipe91/liberdade) meta-agent

*"You can't improve what you can't see."*
