# Netflix Content Analysis — Exploratory Data Analysis (EDA)

**Author:** Lokanath Satapathy
**Dataset:** [Netflix Movies and TV Shows (Kaggle)](https://www.kaggle.com/datasets/shivamb/netflix-shows) — `netflix_titles.csv`, 8,807 titles
**Notebook:** `netflix_eda_github.ipynb`
**Companion:** `Database_analysis.sql` (SQL-based analysis with joins, subqueries, `CASE` expressions, and window-function ranking) + a 4-page Power BI dashboard

## Overview
This notebook is the Python/pandas companion to the SQL-based Netflix analysis — the same catalog normalized into a relational schema (`titles`, `genres`, `title_genres`, `actors`, `title_actors`) in MySQL. It reproduces and visualizes the same **20 business insights** end-to-end, working directly from the flat CSV using pandas for the "relational" logic (splitting multi-value fields, grouping, ranking) and matplotlib/seaborn for the visuals. Each code cell is annotated with the SQL query it mirrors.

## Data
The notebook expects the following file in the working directory:

| File | Description |
|---|---|
| `netflix_titles.csv` | Netflix catalog — type, title, director, cast, country, date added, release year, rating, duration, genres (`listed_in`) |

Update the file path in the **Load the Data** section if the CSV lives elsewhere.

## Requirements
```bash
pip install pandas numpy matplotlib seaborn
```

## Notebook Structure
1. **Setup & Configuration** — imports pandas, numpy, matplotlib, seaborn; sets a Netflix-branded color palette and plot styling defaults.
2. **Load the Data** — reads `netflix_titles.csv`, prints shape and `.info()`.
3. **Data Quality Assessment** — missing-value audit (director ~30%, cast ~9%, country ~9% missing) and a structural fix for rows where `duration` values were shifted into the `rating` column.
4. **Feature Engineering** — parses `date_added`, derives `year_added`/`month_added`, splits `duration` into `duration_minutes`/`duration_seasons`, and explodes the comma-separated `listed_in` (genres) and `cast` fields into long-format tables — the pandas equivalent of the SQL genre/actor bridge tables.
5. **Section A — Content Trends** (A1–A4) — Movie vs. TV Show split, library growth by year, release-to-addition freshness gap by type, seasonality by month added.
6. **Section B — Genre Analysis** (B1–B4) — top genres by title count, genre evolution by average release year, genre mix for Movies vs. TV Shows, early vs. recent era genre focus.
7. **Section C — Country & Geography** (C1–C4) — top content-producing countries, movie/TV ratio by country, top genre per top-5 country, single-country vs. co-production titles.
8. **Section D — Actor & Director Analysis** (D1–D4) — top directors and actors by title count, frequent director-actor collaborations, type/country focus of the top-5 directors.
9. **Section E — Ratings & Duration** (E1–E4) — content rating distribution, average movie duration trend by decade, TV show season-count distribution, longest/shortest average runtime by genre.
10. **Summary of Findings** — table recapping all 20 insights with their key numbers.

## Key Findings (from the notebook's summary)
- **Content mix:** Movies dominate the catalog — 6,131 titles (69.6%) vs. 2,676 TV Shows (30.4%).
- **Freshness:** TV Shows are added to Netflix far sooner after release than Movies (smaller release-to-addition gap).
- **Genres:** "International Movies" is the single biggest genre tag (2,752 titles); Movies and TV Shows have almost no overlap in their top-5 genres.
- **Geography:** The United States (3,211) and India (1,008) are the two dominant content-producing countries; India is the most Movie-skewed major country.
- **Cast & crew:** Rajiv Chilaka leads directors (19 titles); Anupam Kher leads actors (43 titles) — Bollywood names dominate the top of the actor list.
- **Ratings & duration:** TV-MA is the largest rating (3,207 titles, 36.4%); movie runtimes have shortened every decade since pre-2000; 67% of TV Shows never get renewed past a single season.

## How to Run
1. Place `netflix_titles.csv` in the same directory as the notebook (or update the path in Section 2).
2. Install the requirements above.
3. Open `netflix_eda_github.ipynb` in Jupyter and run all cells top to bottom.

## Related
For the relational SQL analysis — joins across the normalized schema, window-function ranking, and the 4-page Power BI dashboard — see `Database_analysis.sql` and `netflix_dashboard.pbix` in the `data-science-core-toolkit` repo, `sql/netflix_analytics/` folder.
