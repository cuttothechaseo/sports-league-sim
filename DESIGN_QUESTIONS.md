# Design Questions — Football League Simulator

## How to Use This File

This is not a checklist.

These questions are here to help me think when I feel stuck.

I do not need to answer all of them before coding.

## Start With the World

1. What things exist in my league?
2. What information does each thing need to remember?
3. What changes over time?
4. What is temporary?
5. What results do I want to print and inspect?

## Class Questions

For each concept I consider turning into a class:

6. Does this thing have multiple pieces of data that belong together?
7. Does it need to remember state over time?
8. Does it have behavior that naturally acts on its own state?
9. Will many instances of this thing exist?
10. Would passing its values around separately become annoying?

Potential concepts to think about:

- Player
- Team
- Game
- League
- Season

Do not assume every one needs a class.

## `self` and Object-State Questions

11. What object does `self` represent?
12. Which values belong permanently to this object?
13. Which values are only needed during this method?
14. Am I changing object state?
15. Should this method return something after changing the object?
16. Could another object need access to this one?

## Function Questions

17. What is the function's one main responsibility?
18. What exact values does it need?
19. What types are those values?
20. Should those values be passed as parameters?
21. Is one of those values already object state on `self`?
22. Does the function calculate and return something?
23. Does it mutate an object?
24. Does it do both?
25. Who receives the return value?

Mental contract:

`inputs → work → side effects → output`

## Global Constant vs Parameter vs Object State

26. Is this value the same across the entire simulation?
27. Could I reasonably want to change it between simulations?
28. Does it belong to one specific object?
29. Is it only needed temporarily inside one function?
30. Would passing it explicitly make the dependency clearer?

Examples to reason about:

- league size
- home-field advantage
- scoring randomness
- team rating
- team wins
- current week's games
- temporary simulated score

## Module / File Questions

Before creating a new `.py` file:

31. What responsibility would this file own?
32. Are the functions/classes inside it strongly related?
33. Would moving this code make another file easier to understand?
34. Is this module reusable by other parts of the app?
35. Does this module need to import another module?
36. Does that dependency make conceptual sense?
37. Am I creating a file because of a real boundary, or just because the current file feels long?

Potential responsibilities might eventually include domain objects, game simulation, scheduling, standings, configuration, and orchestration.

These are examples, not prescribed files.

## Import Questions

38. What exactly am I importing?
39. Why does this module need to know about that thing?
40. Is the dependency flowing in a sensible direction?
41. Am I accidentally creating circular imports?
42. Could a value be passed into a function instead of imported globally?

## League-State Questions

43. Who owns the list of teams?
44. Who owns the schedule?
45. Who knows what week it is?
46. Who decides which games happen next?
47. Who stores game results?
48. Who updates team records?
49. Who calculates standings?
50. Are standings stored permanently, or calculated from Team records when needed?

## Game Simulation Questions

51. What information must exist before a game can be simulated?
52. Does the simulation function need full Team objects or just ratings?
53. What should one simulated game return?
54. Should a Game object store the result?
55. Should the game itself update Team records?
56. Or should another layer take the result and update the teams?
57. What happens if the same game is accidentally simulated twice?

There may be multiple valid designs.

## Schedule Questions

58. What does one matchup look like in Python?
59. What does one week look like?
60. What does an entire schedule look like?
61. Should games exist as Game objects before they are played?
62. Or should Game objects be created when needed?
63. How will I know which games are complete?
64. How will teams avoid impossible duplicate matchups?

## Testing / Visibility Questions

After every meaningful function or method:

65. What small result can I print to prove it works?
66. Can I test it with only two teams?
67. Can I manually predict the expected state afterward?
68. What object changed?
69. What value was returned?
70. Did anything change that I did not expect?

Useful habit:

> Build one relationship, print it, understand it, then connect another relationship.

## Value-Flow Questions

When confused, trace one concrete example:

Team A → passed into ? → Game result created → result returned/stored → Team A record changes → standings reads new record

Then ask:

71. What type exists at each arrow?
72. Which module is executing?
73. Is the value being passed, imported, or read from `self`?
74. Is the same object still being referenced?
75. Did a function return new data or mutate existing state?

## Architecture Checkpoints

76. Does `main.py` mostly orchestrate, or is it doing everything?
77. Does one module know too much?
78. Does one class have too many unrelated responsibilities?
79. Am I passing five separate values that clearly belong to one object?
80. Am I storing derived data that could simply be recalculated?
81. Are my imports easy to explain?
82. Could I describe the codebase in a few sentences?

If I cannot explain the architecture simply, I may need to simplify it.

## Optional Later Questions

Only if the core league is already working:

83. How could I save/load a season?
84. How could player ratings affect team strength?
85. How could injuries alter state?
86. How could trades transfer a Player object from one Team to another?
87. How could playoffs reuse Game simulation?
88. How could I add a CLI menu without mixing UI code with simulation logic?
89. How could tests verify that state updates correctly?
90. How could I add statistics without turning one class into a giant object?

These are extensions, not requirements.
