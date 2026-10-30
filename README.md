# Formula 1 Race Intelligence

An interactive Tableau project exploring Formula 1 data through visual
analytics. The project examines team and driver performance,
tyre-compound outcomes, Grand Prix hosting patterns, podium
achievements, and race reliability.

## Project Scenarios

### 1. F1 Team Performance Strategist

-   **Constructor Championship Points Trend:** compares team points
    across seasons.
-   **Tyre Compound Performance by Circuit Type:** explores podium
    outcomes by starting compound and circuit type.
-   **Driver Talent and Performance Ranking:** compares drivers in a
    selected season.

### 2. Motorsport Broadcast Analyst

-   **All-Time Driver Points Leaderboard:** ranks drivers by points
    across the available seasons.
-   **Countries Hosting the Most Grand Prix Rounds:** counts distinct
    races hosted by each country.
-   **Podium Achievements by Driver and Team:** compares podium finishes
    by driver and team.

### 3. F1 Technical Regulation Analyst

-   **DNF Reasons by Team:** examines recorded retirement reasons across
    teams.
-   **DNF Patterns by Circuit Type and Driver:** explores retirement
    frequency across circuit types and drivers.
-   **Driver and Team Reliability Trend:** compares race-completion
    rates over seasons.

## Dataset

The workbook uses these data tables/sheets:

  -----------------------------------------------------------------------
  Sheet                               Description
  ----------------------------------- -----------------------------------
  `circuits`                          Circuit information and attributes.

  `championship_standings`            Driver championship standings and
                                      points by season.

  `lap_intelligence`                  Lap-level information for race
                                      analysis.

  `qualifying_results`                Qualifying session results.

  `race_results`                      Race results, drivers, teams,
                                      finishing positions, tyre
                                      information, and retirement
                                      details.
  -----------------------------------------------------------------------

Check the actual field names and data types in Tableau before editing
calculations.

## Important Calculated Fields

### Podium Flag

Counts a finish in positions 1, 2, or 3. This assumes `finish_position`
is numeric.

``` tableau
IF NOT ISNULL([finish_position])
AND [finish_position] <= 3
THEN 1
ELSE 0
END
```

### Race Completion Rate

If `DNF Flag` is coded as `1` for a DNF and `0` otherwise:

``` tableau
1 - AVG([DNF Flag])
```

Format the result as a percentage. Verify the dataset's DNF/status
definitions before relying on this calculation.

## Suggested Tableau Story

1.  Introduction and dashboard overview
2.  Team performance
3.  Tyre strategy
4.  Broadcast statistics
5.  Retirement reasons
6.  Circuit-related retirement patterns
7.  Reliability trends
8.  Conclusion

Useful interactive filters may include season, team, driver, and circuit
type.

## Opening the Project

### Tableau Packaged Workbook (`.twbx`)

A `.twbx` file packages the workbook with local supporting data and
assets.

1.  Open Tableau.
2.  Select **File → Open**.
3.  Choose the `.twbx` file.
4.  Check that the data connections, worksheets, dashboards, and story
    points load correctly.

### Sharing through Tableau Public

1.  Open the workbook in Tableau Public Edition.
2.  Sign in to a Tableau Public account.
3.  Choose **Server → Tableau Public → Save to Tableau Public** (menu
    wording may vary).
4.  Open the published visualization on your Tableau Public profile.
5.  Use **Share** to copy the public link.

**Privacy warning:** Tableau Public content and its underlying data are
publicly accessible. Do not publish confidential, personal, or
restricted information.

## Suggested GitHub Repository Structure

``` text
formula-1-race-intelligence/
├── README.md
├── tableau/
│   └── formula-1-race-intelligence.twbx
├── data/
│   └── README.md
├── screenshots/
│   ├── dashboard-overview.png
│   ├── team-performance.png
│   ├── broadcast-analysis.png
│   └── reliability-analysis.png
└── docs/
    └── project-report.pdf
```

Add your actual workbook, screenshots, and report to the relevant
folders. Do not upload the dataset unless you have permission to
redistribute it.

## Tools Used

-   **Tableau** --- visualizations, dashboards, filters, and story.
-   **Microsoft Excel / spreadsheet data** --- dataset inspection and
    preparation.
-   **GitHub** --- project versioning and sharing.

## Notes and Limitations

-   The analysis covers only the seasons and records included in the
    supplied dataset. The latest season may be incomplete.
-   Championship standings are driver-level records. Team totals derived
    from them depend on correct driver-to-team assignments for each
    season.
-   Grand Prix host country is not the same as driver nationality.
    Nationality analysis requires a reliable nationality field or
    verified lookup table.
-   DNF analysis depends on the dataset's status coding. Confirm the
    definitions before drawing conclusions.
-   Joining tables with different levels of detail can duplicate
    records. Validate row counts and aggregations after joins; use
    Tableau relationships where appropriate.
-   Visual trends show associations and patterns; they do not
    independently prove causes.

## Author

Add your name, course/institution, and project details here.

## Data Source and License

Add the original dataset source, attribution requirements, and license
after confirming the dataset's terms. Do not assume that the data is
freely redistributable.
