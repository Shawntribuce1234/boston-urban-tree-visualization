# Boston Urban Tree Visualization

A DS 4200 project by Shawn Tribuce exploring tree species and geographic distribution in Boston through Tableau visualizations and a TreeBoston project report.

## Project Overview

This project focuses on two questions: **Where are trees located, and which species appear most frequently in the available records?** A geographic map, species bar chart, and treemap support exploration of location and species composition. A separate historical view examines records by the acquisition year of Boston open spaces.

The project also includes a community engagement component. The report describes volunteering with TreeBoston at New Calvary Cemetery in Mattapan and planting sawtooth oak trees.

## Repository Structure

```text
boston-urban-tree-visualization/
├── README.md
├── data/
│   └── treeboston_updated.csv
├── tableau/
│   └── boston_tree_analysis.twbx
├── report/
│   └── boston_tree_analysis_report.pdf
└── demo/
    └── boston_tree_dashboard_demo.mp4
```

## Project Materials and Data

The materials capture different stages of the project and should be interpreted separately.

| Material | Contents |
| --- | --- |
| Updated TreeBoston CSV | 619 records with species, tree type, dates, tree diameter, funder and parcel information, and geographic coordinates. |
| Packaged Tableau workbook | Four worksheets and bundled spatial datasets: BPRD Trees, Boston Open Space, and Boston neighborhood boundaries approximated by 2020 census tracts. |
| Project report | Project goals, data preparation, visualization screenshots, observations, and recommendations. |
| Video file | Supplied project video, approximately 3 minutes 15 seconds long; playback content could not be verified during this review. |

The workbook's bundled source tables contain **51,459 BPRD tree records**, **559 open-space records**, and **24 neighborhood boundary records**. These are source-table sizes, not the size of the dashboard's displayed subset. The updated TreeBoston CSV is a separate dataset and is not connected in the supplied workbook.

## Tableau Visualizations

### Dashboard documented in the report

The report presents **TreeBoston Planting Dashboard with Species and Location Explorer**, combining:

- **Geographic map:** plots TreeBoston locations to show spatial patterns.
- **Species bar chart:** compares the ten most frequent species by record count.
- **Treemap:** shows the five leading species with rectangle size representing count and a green color scale reinforcing magnitude.
- **Species selection:** a visible species checklist supports filtering; the report describes brushing and linking between views.

### Worksheets in the supplied workbook

The packaged workbook contains four worksheets:

1. **Number of Trees in Boston Open Spaces by Year Acquired** — counts BPRD tree records by open-space acquisition year.
2. **Geographic Distribution of Trees Across Boston Neighborhoods** — a geographic view using coordinate fields and neighborhood geometry.
3. **Top 10 Most Common Tree Species Planted in Boston** — a species count comparison with a top-ten filter.
4. **Boston's Top 20 Most Planted Tree Species** — a size-and-color species view with a top-twenty filter.

**The supplied workbook contains no saved dashboard.** Its worksheets and data connections differ from the finished dashboard shown in the report. The report documents the finished presentation; the packaged workbook preserves the supplied worksheet implementation.

## Analysis and Data Preparation

The workbook relates open spaces to BPRD tree records through `OS_ID` / `os_id` and relates tree records to neighborhood boundaries through neighborhood names. Its year calculation converts zero acquisition years to null values.

The report describes excluding `Empty Pit/Planting Site` entries and correcting geographic coordinates. These are documented preparation steps, not a claim that every supplied file has undergone identical cleaning.

For the updated CSV, species frequencies are calculated by counting records with each species label. They are not deduplicated estimates of unique living trees.

## Verified Findings

The updated CSV supports the following leading species counts, which agree with the bar chart shown in the report:

| Species | Records |
| --- | ---: |
| Pin Oak | 38 |
| Red Maple | 37 |
| Honey Locust | 37 |
| Sweetgum | 33 |
| Flowering Dogwood | 31 |

Pin Oak leads by one record, while Red Maple and Honey Locust are tied. These five species also appear in the report's treemap.

The dashboard map shows visible clusters and uneven spatial distribution. It does not establish a neighborhood ranking, canopy coverage, or equitable access to trees without additional geographic validation and comparison data.

## Interpretation and Limitations

- **Acquisition year is not planting year.** The report uses open-space acquisition year as a temporal substitute because planting dates were incomplete. The historical view cannot establish actual planting trends.
- **Data versions differ.** The report mentions 521 records, while the supplied updated CSV contains 619. The workbook uses a much larger BPRD source table. These counts should not be combined.
- **Some report prose conflicts with its charts.** The README uses the updated CSV and matching chart values for species rankings rather than repeating the report's inconsistent ranking statements.
- **Missing values affect mapping and species summaries.** The updated CSV contains 11 blank species values, 58 blank latitude values, and 59 blank longitude values. Latitude and longitude missing counts overlap and should not be added together.
- **Geographic relationships need care.** The workbook relates neighborhood names directly, but some BPRD labels combine neighborhoods that are separate in the boundary dataset. Coordinate fields and neighborhood matching require validation before drawing precise spatial conclusions.
- **Environmental benefits are project context, not measured outcomes.** The materials do not establish quantified effects on canopy growth, air quality, runoff, heat reduction, or twenty-year outcomes.

The report recommends standardized planting dates, coordinate validation, and tracking tree survival to improve future analysis.

## Viewing the Project

Read `report/boston_tree_analysis_report.pdf` for the visual narrative. The supplied video is stored at `demo/boston_tree_dashboard_demo.mp4`; its content was not used to establish the findings above. Open `tableau/boston_tree_analysis.twbx` in Tableau to inspect the supplied worksheets and spatial data relationships.

The workbook bundles three spatial archives, but it also retains a separate connection to `open_space.json`, which is not included. The four worksheets reference the bundled multi-connection spatial source. Opening and rendering the workbook in Tableau has not been verified, and it should not be treated as a reproducible copy of the finished dashboard.

## Tools

Tableau, CSV data, and GIS shapefiles.

## Course and Author

**DS 4200**  
**Shawn Tribuce**
