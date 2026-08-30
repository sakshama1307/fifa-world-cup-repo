# FIFA World Cup 2026 – Power BI Dashboard ⚽

This is my **FIFA World Cup 2026 Power BI project**, where I used Power BI to turn football data into an interactive dashboard.

The report has **7 pages**, covering teams, matches, players, referees, stadiums, FIFA rankings, and detailed team statistics. I also used DAX measures to calculate the main KPIs and metrics shown in the report.

---

## 📊 Dashboard

The report contains the following 7 pages:

### 1. FIFA World Cup 2026 – Tournament Overview

This is the main overview page of the dashboard.

It shows:
- Total Team Goals – **308**
- Total Teams – **48**
- Total Matches – **104**
- Yellow Cards – **253**
- Top teams by goals
- Match event distribution
- Attacking efficiency using possession and total shots

There is also a **Team** filter that allows the dashboard to be explored for individual teams.

---

### 2. Teams & Referee Analysis

This page focuses on team performance and referees.

It includes:
- Total Tournament Points – **288**
- Total Referees – **28**
- Average Cards per Referee – **4.26**
- Team goals and tournament points
- Average possession by team
- Top referees by average cards
- Goals vs Tournament Points by group
- Matches officiated by each referee

The page can be filtered by **Stage**.

---

### 3. Match Performance Analysis

This page looks at scoring and match performance.

The main KPIs are:
- Expected Goals (xG) – **276.00**
- Total Penalty Goals – **25**
- Goals per Match – **2.96**

The visuals compare:
- Actual goals vs expected goals
- Penalty shootouts by tournament stage

The **Stage** filter can be used to explore different parts of the tournament.

---

### 4. Player Analysis

This page provides an overview of the players in the tournament.

The main KPIs are:
- Average Age – **27.96**
- Total Players – **1K**
- Average Market Value – **15.49M**

It includes:
- Player age distribution
- Player position distribution
- Top clubs by player representation

The page can be filtered by **Team**.

---

### 5. Venue & Stadium Analysis

This page focuses on the stadiums and host cities.

The main KPIs are:
- Total Stadiums – **16**
- Total Capacity – **1M+**
- Average Stadium Capacity – **66.08K**

The visuals show:
- Stadium capacity by city
- Goals scored at each stadium
- Matches hosted by each stadium

A **Venue** filter is available for exploring individual stadiums.

---

### 6. Advanced Team Statistics

This page provides a more detailed view of a selected team.

The dashboard shows:
- Total Goals
- Total Saves
- Total Minutes Played
- Team performance summary
- Saves and own goals
- Top players by minutes played
- Yellow cards by position
- Market value by position

For example, when **Argentina** is selected, the dashboard shows:
- **18 goals**
- **23 saves**
- **8,885 minutes played**
- **13 yellow cards**

The page can be used to compare and explore individual teams.

---

### 7. FIFA Rankings & Tournament Insights

The final page connects FIFA rankings with tournament statistics.

It includes:
- Highest Ranked Team
- Total Market Value
- Pre-Tournament FIFA Rankings
- Goals by team
- Market Value vs Goals
- Tournament progression

The ranking table compares teams using their FIFA rank and goals, while the scatter plot helps explore whether higher squad market value is associated with more goals.

The page can be filtered by **Team**.

---

## 🧮 DAX

I created DAX measures for the dashboard KPIs and calculations.

Some of the measures used include:

- Total Team Goals
- Total Teams
- Total Matches
- Yellow Cards
- Total Tournament Points
- Total Referees
- Average Cards Per Referee
- Expected Goals
- Total Penalty Goals
- Goals / Match
- Total Players
- Average Age
- Average Market Value
- Total Stadiums
- Total Capacity
- Average Stadium Capacity
- Total Saves
- Total Minutes Played
- Highest Ranked Team
- Total Market Value

The DAX documentation is available in:

**`DAX.md`**

---

## 🗃️ Data

The project uses several datasets covering different parts of the tournament.

The main tables include:

- `matches_detailed` – match scores, xG, penalties, teams, stages and venues
- `match_events` – goals, cards, assists and other match events
- `squads_and_players` – player information, positions, clubs, age and market value
- `teams` – team information and FIFA ranking data
- `references` – referee information
- `stadiums` – stadium capacity, cities and venue information

---

## 🛠️ Tools Used

- **Microsoft Power BI**
- **DAX**
- **Power Query**
- **Data Modeling**
- **Data Visualization**
- **GitHub**

---

## 📁 Project Structure

```text
fifa-world-cup-repo/
│
├── README.md
├── DAX.md
│
├── fifa datasets/
│   └── Dataset files
│
├── fifa powerbi/
│   └── FIFA World Cup 2026 Power BI report
│
└── fifa ss/
    └── Dashboard screenshots
```

---

## 🔍 What I Explored

Through this project, I explored questions such as:

- Which teams scored the most goals?
- Which teams collected the most tournament points?
- How do actual goals compare with expected goals?
- Which referees had the highest average cards?
- How are players distributed by age and position?
- Which clubs have the most players represented?
- Which stadiums hosted the most matches?
- Which stadiums had the most goals?
- Does market value have a relationship with goals?
- How do FIFA rankings compare with tournament performance?
- How does the performance of an individual team look in detail?

---

## 📌 Project Goal

The main goal of this project was to practice **Power BI, DAX, data modeling, and data visualization** by building a complete dashboard around a real-world football dataset.

Instead of looking at the data through separate tables, I wanted to build one interactive report where the user can move from a **tournament overview to team, match, player, referee, venue, and ranking analysis**.

