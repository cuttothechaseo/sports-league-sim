# Progress & Notes — Football League Simulator

This file tracks decisions made, open questions, and where things left off between sessions. It is not a prescribed roadmap — the decisions here were made by working through DESIGN_QUESTIONS.md, not planned in advance.

## Status

Last updated: 2026-09-17 — end of Day 1 (design/thinking phase, no code written yet)

## Decisions Made

### Classes

- **Team** — owns name, rating, and W-L record. Multiple instances (8 teams). Rating is state that persists and changes incrementally after each game (not recalculated from scratch each time).
- **Game** — owns the two teams involved and the score. Has its own identity, stored rather than calculated.
- **Schedule** — owns the season's games, organized by week. Has its own behavior (e.g. "what games are this week," "is the season over"). Owned by League.
- **League** — owns teams, the schedule, and settings (e.g. league name). Has behavior of its own (e.g. get settings, get standings).

### Not Classes (deliberately)

- **Rating** — an attribute on Team, not its own thing. No independent identity.
- **Score** — an attribute on Game (e.g. home score / away score). No independent identity.
- **Standings** — calculated on demand from Team records, not stored anywhere as its own object.

### Config vs. State

- League name: leaning toward being an attribute on the League object (`league.name`), not a standalone global constant — decided after re-examining the initial instinct to make it a global constant.

### Scope Cuts

- No Player class. Intentional simplification to keep focus on Team/Game/League/Schedule state management rather than spreading into roster-level detail.

## Open / Undecided

- Is League the same concept as "Season," or are these two separate things? Not yet decided.
- Config vs. object state vs. local variable has only been worked through for league name — other values (home-field advantage, scoring randomness, etc. per DESIGN_QUESTIONS.md Q26-30) haven't been examined yet.
- Module/file breakdown not started.

## Next Step

Write the **Team** class first — most concrete concept so far (name, rating, record).

## Log

### 2026-09-17

- Worked through "what things exist in the league" using DESIGN_QUESTIONS.md's Start-With-The-World and Class Questions sections.
- Sorted the six initial candidates (Teams, Ratings, Games, Standings, Scores, Schedule) into classes vs. attributes vs. calculated values.
- Introduced League as a class mid-discussion (needed to own Schedule) and ran it through the same class test.
- Resolved the league-name config-vs-state question raised at the very start of the session.
- Decided to stop for the day and resume tomorrow by writing the Team class.
