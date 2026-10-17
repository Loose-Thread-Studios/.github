# GitHub project setup for LonelyAstronaut

A draft for a team of four or five, made before the GitHub organization exists. Nothing here has been created on GitHub yet.

| File | What it is |
| --- | --- |
| `.github/ISSUE_TEMPLATE/` | Issue forms: bug report, feature or task, art or audio asset. Copy the folder into the repo root. |
| `labels.yml` | The label set, with colors and descriptions. |
| This README | The board's fields, views, workflow and example issues. |

## Board

One GitHub Projects board (a project in the organization) linked to the LonelyAstronaut repository.

### Fields

| Field | Type | Values | Why |
| --- | --- | --- | --- |
| Status | Single select | Backlog, Ready, In progress, In review, Playtest, Done | The board columns. Playtest holds work that is merged but not yet tried in Play Mode by someone other than its author. |
| Area | Single select | Code, Art, Audio, Design, Level, UI | Who picks it up. Group the board by it to see each discipline's load. |
| Milestone | Repository milestone | 1 Readable encounter, 2 Complete expedition, 3 Tune decisions, 4 Campaign | Mirrors the GDD's Milestones list, so "what's left for milestone 1" is one filter. |
| Priority | Single select | P0 now, P1 next, P2 later | Order inside a column. Keep P0 to a handful. |
| Decision | Text | D12, D22 | The GDD decisions the issue serves. Lets you filter the board by decision. |
| Size | Single select | S (under a day), M (a few days), L (a week or more) | Rough effort. Split anything L before it reaches Ready. |
| Iteration | Iteration | Two weeks | Optional. Add it when the team starts planning in sprints. |

Issue forms can't fill board fields. The form asks for the area so the reporter's answer is in the issue body, and whoever triages sets the Area field and removes `status: needs-triage`.

### Views

| View | Layout | Setup |
| --- | --- | --- |
| Board | Board | Columns by Status, sorted by Priority. The default view. |
| By area | Board | Columns by Status, grouped by Area. |
| Milestone | Table | Filter `milestone:"1 Readable encounter"`, grouped by Status, showing Area, Size and assignee. |
| Triage | Table | Filter `label:"status: needs-triage"`. Empty at the end of each week. |
| Roadmap | Roadmap | Milestones as date markers, items by Iteration. Add when iterations are on. |

### Built-in workflows

Turn on: item added to project sets Status to Backlog; item closed sets Status to Done; pull request merged sets Status to Playtest; auto-add to project for every new issue in LonelyAstronaut.

### Working rules

- A card moves to Ready only when it has an Area, a Milestone, a Priority and acceptance checks.
- Each person has at most two cards in progress.
- A pull request links its issue with `Closes #n`, so merging moves the card.
- Playtest to Done needs a second person to try it. Record what they saw in the GDD Results log when it is evidence about the design.

## Example issues

Seeded from the repo and this project's work, to show how the board fills in. Numbers are placeholders.

| # | Title | Labels | Area | Milestone | Priority | Status |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Show suit health and gun charge pips on the HUD | type: asset | UI | 1 | P0 | In progress |
| 2 | Recolor suit health and beacon sprites to AAP-64 | type: asset | Art | 1 | P1 | Ready |
| 3 | Skitter brace, rush and recovery states read clearly | type: feature | Code | 1 | P0 | In review |
| 4 | Run the combat comparison with two testers | type: playtest | Design | 1 | P1 | Backlog |
| 5 | Choose the gun recharge model (D12) | type: design, status: needs-decision | Design | 1 | P1 | Backlog |
| 6 | Enemy knockback on hit (D22) | type: feature | Code | 1 | P2 | Playtest |
| 7 | Bullet hit passes through enemies at the wrap seam | type: bug, world-wrap | Code | 1 | P0 | Ready |
| 8 | Block out the Wreck Basin route | type: feature | Level | 2 | P1 | Backlog |
| 9 | Title screen with studio logo | type: asset | UI | 2 | P2 | Backlog |
| 10 | Ship ambience and return-to-shelter sting | type: asset | Audio | 2 | P2 | Backlog |
| 11 | Beacon assembly and rescue feedback | type: feature | Code | 2 | P1 | Backlog |
| 12 | Set up Unity Smart Merge on every teammate's machine | type: chore, good first issue | Code | 1 | P2 | Ready |
| 13 | Healthpack in the top-left of the HUD (D19) | type: feature | UI | 1 | P1 | Done |
| 14 | Healthpack fully restores health (D21) | type: feature | Code | 1 | P1 | Done |

Issue 7 is an invented example of the kind of bug the world-wrap label is for, not a known bug.
