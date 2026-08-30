# DAX Measures

This file documents the DAX measures visible in the Power BI model screenshots.

> **Note:** The screenshots show the measure names and the available fields, but not the original DAX expressions. The expressions below are reconstructed from those fields and are intended to match the visible measures. If your original PBIX measures use different business logic, keep the PBIX version as the source of truth.

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

## Player / Squad Table

The following measures correspond to the measures visible in the player/squad table.

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

> If the PBIX uses a differently named minutes column, replace `[minutes_played]` with the actual field name.

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

> If saves are stored in another table, use that table instead.

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

> Use the actual market-value column name if it differs.

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

## Teams

### Highest Ranking

```DAX
Highest Ranking =
MIN('teams'[fifa_ranking_points])
```

> If `[fifa_ranking_points]` is not the ranking field in the PBIX, use the actual FIFA ranking column.

### Total Teams

```DAX
Total Teams =
DISTINCTCOUNT('teams'[team_id])
```

---

## Stadiums

### Average Stadium Capacity

```DAX
Average Stadium Capacity =
AVERAGE('stadiums'[capacity])
```

---

## Useful Additional Measures

These are useful for the same FIFA World Cup dashboard and are consistent with the fields visible in the screenshots.

### Total Matches by Status

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

---

## Important

The uploaded `match_events` CSV contains these columns:

- `event_id`
- `match_id`
- `minute`
- `event_type`
- `team_id`
- `player_id`

Therefore the **Yellow Cards** measure can be defined directly and reliably from that table.

For the other measures, the screenshots expose the field names but not the underlying DAX formulas. The formulas above are reconstructed versions, not extracted originals.
