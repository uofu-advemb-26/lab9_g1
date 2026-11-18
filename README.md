# Lab 9 Advanced Embedded Systems
## State Machine Table
How would you go about proving that your model is correct?

1. Fill in this table (you can copy the markdown into your docs).
1. The first four variables (after `number`) are booleans, you should have 16 possible states.
1. Create your own list of invariants. Use the second table below; start the `number` column at number 16 (because the `number` column of the first table ends at `15`). Add more invariants as needed.
1. For each row, mark "safety_hazard" with the number of the invariant it violates or leave it blank.
1. For each row, write down the number of the state your system will transition to on that event.
   1. If an event violates an invariant (e.g. event not allowed in that state), write down the number of the invariant.
   1. If an event has no effect, you can stay in the same state.
  
**Update Oct 14** the `ringing` column should be something like "time elapsed" to reflect the 10-second delay. That way, it is an event related to the `alarm_on` state of the world (instead of being redundant).

| number | arms_down | alarm_on | northbound_present | southbound_present | north_approach | south_approach | north_depart | south_depart | time elapsed | safety_hazard |
|--------|-----------|----------|--------------------|--------------------|----------------|----------------|--------------|--------------|---------|---------------|
| 0      | 0         | 0        | 0                  | 0                  |               0|             0  |      0       |      0       |   0     |              |
| 1      | 0         | 0        | 0                  | 1                  |               0|             1  |       0      |      0       |   0     |     16        |
| 2      | 0         | 0        | 1                  | 0                  |               1|             0  |       0      |      0       |   0     |     16        |
| 3      | 0         | 0        | 1                  | 1                  |               1|             1  |       0      |       0      |   0     |     16        |
| 4      | 0         | 1        | 0                  | 0                  |               0|             0  |       0      |       0      |   0     |               |
| 5      | 0         | 1        | 0                  | 1                  |               0|             1  |       0       |       0       |    0    |               |
| 6      | 0         | 1        | 1                  | 0                  |              1 |            0   |     0        |      0       |   0     |               |
| 7      | 0         | 1        | 1                  | 1                  |              1 |            1   |      0       |       0      |   0     |               |
| 8      | 1         | 0        | 0                  | 0                  |             0  |             0  |       0      |       0      |    10    |       19      |
| 9      | 1         | 0        | 0                  | 1                  |             0  |              1 |        0     |       0      |    10    |        19     |
| 10     | 1         | 0        | 1                  | 0                  |              1 |              0 |        0     |        0     |     10   |        19     |
| 11     | 1         | 0        | 1                  | 1                  |             1  |              1 |        0     |        0     |     10   |         19    |
| 12     | 1         | 1        | 0                  | 0                  |             0  |              0 |        0     |         0    |     0   |               |
| 13     | 1         | 1        | 0                  | 1                  |              0 |               1|         0    |         0    |     0   |               |
| 14     | 1         | 1        | 1                  | 0                  |               1|               0|         0    |         0    |       0 |               |
| 15     | 1         | 1        | 1                  | 1                  |               1|              1 |          0   |        0     |     0   |               |

| number | invariant |
|--------|-----------|
| 16     |     When a train is present, the barrier is lowered      |
| 17 | The alarm is on before the barrier is lowered |
| 18 | The alarm is on after the barrier is raised |
| 19| The alarm is on when the barrier is lowered |
| 20 | There is power to the system |
| 21 | Every train must approach before it departs |
| 22 | Trains on each track run in exactly one direction |
