# DAX Measures

This file contains the DAX measures used in the FIFA World Cup 2026 Power BI dashboard.

---

## `match_events`

### Yellow Cards

```DAX
Yellow Cards =
CALCULATE(
    COUNTROWS('match_events'),
    'match_events'[event_type] = "Yellow Card"
)
```

---

## `matches_detailed`

### Average Goals

```DAX
Average Goals =
AVERAGEX(
    'matches_detailed',
    'matches_detailed'[home_score] + 'matches_detailed'[away_score]
)
```

### Home Points

```DAX
Home Points =
SUMX(
    'matches_detailed',
    SWITCH(
        TRUE(),
        'matches_detailed'[home_score] > 'matches_detailed'[away_score], 3,
        'matches_detailed'[home_score] = 'matches_detailed'[away_score], 1,
        0
    )
)
```

### Away Points

```DAX
Away Points =
SUMX(
    'matches_detailed',
    SWITCH(
        TRUE(),
        'matches_detailed'[away_score] > 'matches_detailed'[home_score], 3,
        'matches_detailed'[away_score] = 'matches_detailed'[home_score], 1,
        0
    )
)
```

### Total Home Goals

```DAX
Total Home Goals =
SUM('matches_detailed'[home_score])
```

### Total Away Goals

```DAX
Total Away Goals =
SUM('matches_detailed'[away_score])
```

### Total Home Points

```DAX
Total Home Points =
[Home Points]
```

### Total Away Points

```DAX
Total Away Points =
[Away Points]
```

### Total Matches

```DAX
Total Matches =
DISTINCTCOUNT('matches_detailed'[match_id])
```

### Total Team Goals

```DAX
Total Team Goals =
SUM('matches_detailed'[home_score])
    + SUM('matches_detailed'[away_score])
```

### Total Tournament Matches

```DAX
Total Tournament Matches =
DISTINCTCOUNT('matches_detailed'[match_id])
```

### Total Penalty

```DAX
Total Penalty =
SUM('matches_detailed'[home_penalty_score])
    + SUM('matches_detailed'[away_penalty_score])
```

### Total xG

```DAX
Total xG =
SUM('matches_detailed'[home_xg])
    + SUM('matches_detailed'[away_xg])
```

---

## `squads_and_players`

### Total Goals

```DAX
Total Goals =
SUM('squads_and_players'[goals])
```

### Total Minutes

```DAX
Total Minutes =
SUM('squads_and_players'[minutes_played])
```

### Total Players

```DAX
Total Players =
DISTINCTCOUNT('squads_and_players'[player_id])
```

### Total Saves

```DAX
Total Saves =
SUM('squads_and_players'[saves])
```

### Total Yellow Cards

```DAX
Total Yellow Cards =
SUM('squads_and_players'[yellow_cards])
```

### Average Market Value

```DAX
Average Market Value =
AVERAGE('squads_and_players'[market_value_eur])
```

### Target Squad

```DAX
Target Squad =
DISTINCTCOUNT('squads_and_players'[team_id])
```

### Measure

```DAX
Measure =
COUNTROWS('squads_and_players')
```

### Total Market Value

```DAX
Total Market Value =
SUM('squads_and_players'[market_value_eur])
```

---

## `referees`

### Average Cards

```DAX
Average Cards =
AVERAGE('referees'[avg_cards_per_match])
```

### Total Referees

```DAX
Total Referees =
DISTINCTCOUNT('referees'[referee_id])
```

---

## `teams`

### Highest Ranking

```DAX
Highest Ranking =
MIN('teams'[fifa_ranking_points])
```

### Total Teams

```DAX
Total Teams =
DISTINCTCOUNT('teams'[team_id])
```

---

## `stadiums`

### Average Stadium Capacity

```DAX
Average Stadium Capacity =
AVERAGE('stadiums'[capacity])
```

---

## Additional Measures

### Total Completed Matches

```DAX
Total Completed Matches =
CALCULATE(
    [Total Matches],
    'matches_detailed'[status] = "Completed"
)
```

### Average Home Goals

```DAX
Average Home Goals =
AVERAGE('matches_detailed'[home_score])
```

### Average Away Goals

```DAX
Average Away Goals =
AVERAGE('matches_detailed'[away_score])
```

### Average xG

```DAX
Average xG =
AVERAGEX(
    'matches_detailed',
    'matches_detailed'[home_xg] + 'matches_detailed'[away_xg]
)
```

### Total Yellow Cards from Events

```DAX
Total Yellow Cards from Events =
CALCULATE(
    COUNTROWS('match_events'),
    'match_events'[event_type] = "Yellow Card"
)
```

### Total Red Cards

```DAX
Total Red Cards =
CALCULATE(
    COUNTROWS('match_events'),
    'match_events'[event_type] = "Red Card"
)
```
