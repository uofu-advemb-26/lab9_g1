# Lab 9 Advanced Embedded Systems
## Analysis of example FSM
If there are two trains present, then the arms will raise after the first train departs. This violates invariant 16, as the other train is present, but the arms are raised. This is a safety hazard.
## State Machine Table

| number | arms_down | alarm_on | northbound_present | southbound_present | north_approach | south_approach | north_depart | south_depart | time elapsed | safety_hazard |
|--------|-----------|----------|--------------------|--------------------|----------------|----------------|--------------|--------------|---------|---------------|
| 0      | 0         | 0        | 0                  | 0                  |               6|             5  |      21      |      21      |   23    |               |
| 1      | 0         | 0        | 0                  | 1                  |               7|             5  |      21      |      25      |   23    |     16        |
| 2      | 0         | 0        | 1                  | 0                  |               6|             7  |      25      |      21      |   23    |     16        |
| 3      | 0         | 0        | 1                  | 1                  |               7|             7  |      25      |      25      |   23    |     16        |
| 4      | 0         | 1        | 0                  | 0                  |               6|             5  |      21      |       21     |   0     |               |
| 5      | 0         | 1        | 0                  | 1                  |               7|             5  |      21      |       25     |   13    |               |
| 6      | 0         | 1        | 1                  | 0                  |              6 |             7  |      25      |      21      |   14    |               |
| 7      | 0         | 1        | 1                  | 1                  |              7 |            7   |      25      |       25     |   15    |               |
| 8      | 1         | 0        | 0                  | 0                  |             29 |             29 |      21      |       21     |   19    |      19       |
| 9      | 1         | 0        | 0                  | 1                  |            29  |             30 |       21     |       31     |   19    |       19      |
| 10     | 1         | 0        | 1                  | 0                  |             30 |             29 |       31     |       21     |   19    |      19       |
| 11     | 1         | 0        | 1                  | 1                  |            30  |             30 |        31    |       31     |   19    |       19      |
| 12     | 1         | 1        | 0                  | 0                  |            14  |            13  |        21    |        21    |    4    |               |
| 13     | 1         | 1        | 0                  | 1                  |             15 |              13|        21    |         4    |    23   |               |
| 14     | 1         | 1        | 1                  | 0                  |              14|              15|        4     |        21    |    23   |               |
| 15     | 1         | 1        | 1                  | 1                  |              15|             15 |        13    |        14    |    23   |               |

| number | invariant |
|--------|-----------|
| 16     |     When a train is present, the barrier is lowered      |
| 17 | The alarm is on before the barrier is lowered |
| 18 | The alarm is on after the barrier is raised |
| 19 | The alarm is on when the barrier is lowered |
| 20 | There is power to the system |
| 21 | Every train must be present before it can depart |
| 22 | Trains on each track run in exactly one direction |
| 23 | The timer must be on for timer_elapsed signal to occur (see 24) |
| 24 | If the alarm is not on, then the timer is not on |
| 25 | The Barrier must be down before a depart signal can occur |
| 26 | After a depart, it's respective train is not allowed to be present |
| 27 | If a train is present, the alarm should be on |
| 28 | For a train to depart to be valid, the barrier must be lowered |
| 29 | A train must be present before it can approach (similar to 21) |
| 30 | The alarm is on before a train approaches |
| 31 | The alarm is on before a train departs |

