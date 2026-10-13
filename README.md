# Expected Goals Analysis
## Where Defenses Break and Attacks Convert: An xG Analysis of the 2025/26 Premier League

An ECON 570 group project examining how Premier League teams create, concede, and convert scoring chances. Using shot-level data from Understat, the analysis combines spatial visualization, player-position enrichment, and team- and player-level aggregation to explore defensive vulnerabilities and attacking efficiency.

## Research questions

- Where on the pitch do teams concede the most expected goals?
- Which attacking positions account for those chances?
- Which teams and players score above or below their expected output?
- How does finishing change late in matches?
- Which passer–shooter partnerships generate the most dangerous opportunities?

## Data and preparation

The project report identifies the source as **Understat shot data for the 2025/26 Premier League**. Each observation represents a shot and includes an existing expected-goals (xG) value. This project analyzes those supplied probabilities; it does not claim to train a new xG prediction model.

The report describes excluding penalties to focus on chances that better reflect defensive structure. Because player positions were not recorded in the source data, the team manually mapped approximately **300 players to nine positional roles**, excluding goalkeepers from the position analysis.

The dataset extraction date and exact match coverage are not documented. Results below refer to the analyzed sample, rather than an independently verified complete season.

## Analytical approach

| Area | Method | Output |
| --- | --- | --- |
| Defensive geography | Bin shot locations into a **30 × 20 grid** and sum xG within each cell | Half-pitch heatmaps for **20 teams**, using a shared logarithmic color scale |
| Positional vulnerability | Compare total xG conceded with xG conceded to opposing strikers | Team scatterplot and league-average striker-share reference line |
| Finishing efficiency | Aggregate goals and xG by team and player; calculate **goals − xG** | Parity plots identifying over- and underperformance |
| Individual shot quality | Examine shot locations and xG per shot | Player shot maps, including Erling Haaland |
| Late-game finishing | Analyze shots in the **80th minute or later**; retain players with at least **0.5 cumulative late-game xG** | Ranking by late-game goals minus xG |
| Chance creation | Compare shot volume, total xG, and xG per shot | Team comparison of chance quantity and quality |
| Creative partnerships | Aggregate xG and goals by passer–shooter pair | Rankings of attacking partnerships |

**Late-game definition:** The report initially specifies a score margin within one goal, but later describes the filter using only the match minute. Whether the close-score condition is implemented needs to be checked in the notebook.

## Selected findings

The following values and interpretations are reported in the team's ECON 570 write-up; they have not been independently recomputed for this README.

- **Defensive patterns:** Arsenal, Liverpool, and Manchester City showed relatively light, concentrated xG-conceded heatmaps. Burnley, West Ham, and Wolves showed broader areas of vulnerability.
- **Chance quality:** Chelsea generated approximately **64.6 xG from 414 shots**, or **0.156 xG per shot**, illustrating why shot quality matters alongside volume.
- **Finishing above expectation:** Antoine Semenyo scored **15 goals from 11.2 xG**, approximately **+3.8 goals above expectation**.
- **Late-game output:** Mohamed Salah recorded **3 goals from 1.454 late-game xG**, a delta of approximately **+1.546** in the reported sample.
- **Creative partnerships:** The top reported passer–shooter pairing generated approximately **3.63 xG**. Haaland appeared as the shooter in **three of the five highest-ranked partnerships**.

These are descriptive results. They do not establish that a formation caused a defensive pattern or that late-game overperformance is a persistent player skill.

## Project files

| File | Purpose |
| --- | --- |
| [Group21Code.ipynb](Group21Code.ipynb) | Main analysis notebook and saved outputs |
| [pl_2025_shots.csv](pl_2025_shots.csv) | Bundled shot dataset |

The accompanying report, *Where Defenses Break and Attacks Convert*, provides six figures and two main tables covering the analyses above. The report is not currently included in this repository.

## Explore locally

Keep the CSV alongside the notebook.

```bash
git clone https://github.com/AllanBijuGregory2006/expected-goals-analysis.git
cd expected-goals-analysis
python -m pip install jupyter
jupyter notebook Group21Code.ipynb
```

Install the additional packages imported by the notebook before executing its cells. A pinned dependency file and a verified clean-environment run are not yet provided.

## Limitations and interpretation

- **Coverage:** The extraction date and exact match coverage should be recorded before describing results as full-season totals.
- **Position labels:** Manual role assignments simplify players who change positions across matches.
- **Small samples:** The 0.5-xG threshold removes some very small samples, but late-game rankings remain noisy.
- **Model dependence:** Findings depend on Understat's supplied xG estimates; goals minus xG is a descriptive difference, not proof of finishing skill.
- **Tactical explanations:** Formations and tracking data were not incorporated to test the suggested explanations for defensive patterns.
- **Reproducibility:** Notebook dependencies, data provenance/reuse terms, and the precise late-game filter still need documentation.

## Credits and portfolio context

This was a collaborative ECON 570 project by **Faraz Behlum, Bach Pham, Luke DeFrance, and Allan Biju Gregory**. The methods and findings above describe the team's work; individual responsibilities are not specified in the report.

The project connects football analytics with economic reasoning about noisy outcomes, expected performance, and the distinction between opportunity quality and realized results.

## Future directions

- Extend the analysis across multiple seasons to examine the stability of finishing and defensive patterns.
- Incorporate formations or player-tracking data to test tactical explanations.
- Add uncertainty estimates and sensitivity checks for late-game rankings.
- Document dataset coverage, resolve the late-game filter definition, and provide a reproducible environment.
