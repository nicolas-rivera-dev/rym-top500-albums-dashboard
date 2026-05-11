# rym-top500-albums-dashboard
Interactive Power BI dashboard analyzing the Top 500 best-reviewed albums on RateYourMusic.com

# Albums Dashboard — Dataset Documentation

**Top 500 Best Reviewed Albums of All Time**  
Source: [RateYourMusic.com](https://rateyourmusic.com) · Collected as of April 21, 2026
---

## Dataset Overview

| Property | Value |
|---|---|
| File | `Dataset_Albums_Enriched.xlsx` |
| Rows | 500 |
| Columns | 12 |
| Year Range | 1958 – 2025 |
| Null Values | None |
| Avg. Rating | 4.05 ★ |

---

## Column Reference

| Column | Type | Description | Example |
|---|---|---|---|
| `Ranking` | Integer | Position in the Top 500 list (1 = highest rated) | `1` |
| `Album Title` | Text | Full official album name | `To Pimp a Butterfly` |
| `Release Year` | Integer | Year the album was released | `2015` |
| `Decade` | Text | Decade of release (pre-aggregated) | `2010s` |
| `Artist` | Text | Performing artist or band name | `Kendrick Lamar` |
| `Rating` | Float | Average community rating (scale 1.00–5.00) | `4.38` |
| `Genre` | Text | Primary genre classification | `Hip Hop` |
| `Subgenre` | Text | More specific sub-genre tag | `Conscious Hip Hop` |
| `Country` | Text | Country of origin of the artist | `USA` |
| `Album Type` | Text | Type of release | `Studio Album` |
| `Label` | Text | Record label that released the album | `Top Dawg Entertainment` |
| `Language` | Text | Primary language of the album's lyrics | `English` |

---

## Key Statistics

### Rating Distribution
| Metric | Value |
|---|---|
| Minimum | 3.80 |
| 25th Percentile | 3.96 |
| Median | 4.03 |
| 75th Percentile | 4.13 |
| Maximum | 4.40 |
| Std. Deviation | 0.11 |

### Top 5 Highest Rated Albums
| Ranking | Album Title | Artist | Year | Rating |
|---|---|---|---|---|
| 1 | 98.12.28 Otokotachi no wakare | Fishmans | 1999 | 4.40 |
| 2 | To Pimp a Butterfly | Kendrick Lamar | 2015 | 4.38 |
| 3 | Wish You Were Here | Pink Floyd | 1975 | 4.36 |
| 4 | Stop Making Sense | Talking Heads | 1984 | 4.34 |
| 5 | The Black Saint and the Sinner Lady | Charles Mingus | 1963 | 4.33 |

### Genre Distribution (Top 10)
| Genre | Count |
|---|---|
| Hip Hop | 57 |
| Alternative Rock | 47 |
| Jazz | 34 |
| Rock | 28 |
| Electronic | 23 |
| Progressive Rock | 23 |
| Folk | 20 |
| Indie Rock | 14 |
| Art Rock | 13 |
| Experimental Rock | 13 |

### Album Type Breakdown
| Type | Count |
|---|---|
| Studio Album | 443 |
| Live Album | 38 |
| Soundtrack (OST) | 12 |
| Classical Recording | 6 |
| Compilation | 1 |

### Artists with Most Albums in the Top 500
| Artist | Albums |
|---|---|
| Swans | 8 |
| John Coltrane | 7 |
| Bob Dylan | 7 |
| Miles Davis | 6 |
| Kanye West | 6 |

### Countries Represented
- **Total unique countries:** 25
- Top countries: USA, UK, Japan, Canada, Germany

---

## Dashboard Visualizations Built From This Dataset

| Visual | Fields Used |
|---|---|
| KPI — Total Albums | `Ranking` (COUNT) |
| KPI — Total Artists | `Artist` (DISTINCTCOUNT) |
| KPI — Total Countries | `Country` (DISTINCTCOUNT) |
| KPI — Average Rating | `Rating` (AVERAGE) |
| KPI — Top Genre | FIRSTNONBLANK(TOPN(1, VALUES('Albums'[Genre]), CALCULATE(COUNTROWS('Albums')), DESC), 1) |
| Bar chart — Artists with most albums | X-Axis `Album Title` (COUNT) | Y-Axis `Artist` |
| Map (Azure) — Countries with most albums | Location `Country` | Size `Album Title` (COUNT) | Tooltips `Album Title` (COUNT) |
| Data table — Ranking table | `Ranking`, `Album Title`, `Artist`, `Rating` |
| Bar+Line combo — Albums and average rating by decade | X-Axis `Decade`| Y-Axis Column `Album Title` (COUNT) | Y-Axis Line `Rating` (AVERAGE) |
| Bar chart — Albums by genre/subgenre | X-Axis `Album Title` (COUNT) | Y-Axis `Genre` |

---

**Slicers/Filters:**
- Genre
- Decade
- Release Year
- Country
- Language

---

## DAX Measures Used

```dax
Top Genre = FIRSTNONBLANK(TOPN(1, VALUES('Albums'[Genre]), CALCULATE(COUNTROWS('Albums')), DESC), 1)
```

---

## Data Quality Notes

- No null values across any column
- The `Decade` column was pre-calculated during data preparation (not derived in DAX) — values follow the format `1960s`, `1970s`, etc.
- `Language` field contains `Instrumental` for albums with no vocal content
- `Country` reflects the artist's country of origin, not the label's country
- Album rankings reflect community-weighted averages as of **April 21, 2026**
- The dataset was enriched with `Label`, `Subgenre`, `Album Type`, and `Language` fields beyond the base source data
