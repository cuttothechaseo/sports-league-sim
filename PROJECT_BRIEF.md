# Football League Simulator — Project Brief

## Goal

Build a multi-file Python application that simulates a fictional football league over the course of a season.

The point is not statistical realism. The point is to practice building a larger software system where:

- multiple Python files have clear responsibilities
- classes own related data and behavior
- functions pass values between modules
- state changes over time
- imports connect the codebase together
- results are easy to print, inspect, and test
- architecture decisions are made intentionally

## Primary Learning Goals

### Classes and objects

Learn when a class is useful because several pieces of state belong to the same conceptual thing.

Potential concepts include Player, Team, Game, League, and Season. These are possibilities, not requirements.

### State ownership

For every value, be able to answer:

- Where does this value live?
- Which object owns it?
- Which function is allowed to change it?
- Is it permanent state or temporary calculation?
- Does another module need access to it?

### Function contracts

For important functions, understand:

input → parameter → local work → mutation/calculation → return value → receiving variable

Before writing a function, ask:

- What exact type goes in?
- What exact type comes out?
- Does it mutate an existing object?
- Does it return a new value?
- Does it do both?
- Who uses the return value?

### Modules and imports

Use separate `.py` files when responsibilities become meaningfully distinct.

The goal is not "one function per file."

The goal is:

> related responsibilities live together, unrelated responsibilities stay separate.

### Constants vs object state vs local variables

Practice distinguishing:

- configuration/constants: league-wide rules/settings
- object state: values belonging to one persistent object
- local variables: temporary calculations inside a function

## White-Space Requirement

Do not generate the full architecture before building.

The learner should make decisions such as:

- which concepts become classes
- which functions belong as methods
- which functions stay standalone
- which modules exist
- how game simulation works
- how standings are calculated
- how the schedule is represented
- how results flow between objects/modules
- how much state each class should own

These decisions are part of the exercise.

## Constraints

- Terminal only at first
- Standard library only unless a real need appears
- No database initially
- No GUI initially
- Avoid inheritance unless a natural reason appears
- Prefer simple classes and explicit functions
- Print intermediate results often while building

## Definition of Success

The project is learning-complete when:

1. The application uses multiple modules with understandable responsibilities.
2. At least one class is used because it naturally owns state.
3. A league can progress through multiple games or weeks.
4. Game results affect team state.
5. Standings or another league-level summary updates correctly.
6. You can explain how data moves through the entire application.
7. You can identify what is global configuration, object state, and local calculation.
8. You can explain why each major class exists.
9. You can explain why each major module exists.
10. You made the important architecture decisions yourself.

## Completion Philosophy

Do not build every possible league feature.

A smaller system that you understand deeply is better than a huge one you assembled mechanically.
