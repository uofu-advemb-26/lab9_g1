# Lab 9 Advanced Embedded Systems
## Analysis of example FSM
If there are two trains present, then the arms will raise after the first train departs. This violates invariant 16, as the other train is present, but the arms are raised. This is a safety hazard.
## State Machine Table

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
