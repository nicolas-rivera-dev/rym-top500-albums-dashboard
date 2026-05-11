## Data Sources & Collection Notes

### Source
- **Website:** [RateYourMusic.com](https://rateyourmusic.com)
- **Snapshot date:** April 21, 2026
- **Collection method:** Manual — data was hand-collected 
  directly from the website (no scraping tools were used)

### Dataset File
`Dataset_Albums_Enriched.xlsx` — 500 rows, 12 columns

### Enrichment Process
The following columns were collected **manually** from RateYourMusic.com:

| Column | Method |
|---|---|
| `Ranking` | Manually collected from RateYourMusic.com |
| `Album Title` | Manually collected from RateYourMusic.com |
| `Artist` | Manually collected from RateYourMusic.com |
| `Release Year` | Manually collected from RateYourMusic.com |
| `Rating` | Manually collected from RateYourMusic.com |

The following columns were **added during enrichment**:

| Column | Method |
|---|---|
| `Decade` | AI-assisted generation based on Release Year, manually reviewed |
| `Genre` | AI-assisted, manually reviewed |
| `Subgenre` | AI-assisted, manually reviewed |
| `Country` | AI-assisted, manually reviewed |
| `Album Type` | AI-assisted, manually reviewed |
| `Label` | AI-assisted, manually reviewed |
| `Language` | AI-assisted, manually reviewed |

### Important Notes
- Rankings reflect community-weighted averages as of **April 21, 2026**
  and may have changed since collection
- RateYourMusic.com does not allow scraping per their Terms of Service;
  all data was collected manually in compliance with their policies
- This dataset is intended for educational and portfolio purposes only
