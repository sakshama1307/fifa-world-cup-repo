Total Goals by tea,m=
VAR SelectedTeam =
    SELECTEDVALUE('teams'[team_name])

VAR HomeGoals =
    CALCULATE(
        SUM('matches_detailed'[home_score]),
        FILTER(
            ALL('matches_detailed'),
            'matches_detailed'[home_team_name] = SelectedTeam
        )
    )

VAR AwayGoals =
    CALCULATE(
        SUM('matches_detailed'[away_score]),
        FILTER(
            ALL('matches_detailed'),
            'matches_detailed'[away_team_name] = SelectedTeam
        )
    )

RETURN
    HomeGoals + AwayGoals
