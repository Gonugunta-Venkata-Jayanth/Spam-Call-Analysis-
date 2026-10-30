# Spam Call Analysis — Power BI Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black)
![Power Query](https://img.shields.io/badge/Data%20Prep-Power%20Query-blue)
![Type](https://img.shields.io/badge/Project-Data%20Analytics-success)

A one-page Power BI report built on call-center data. It summarises how many calls were answered, how calls are spread across agents, satisfaction ratings by agent, and speed of answer by call topic.

> **Note on scope:** despite the project title, the data in the report has no spam/legitimate label, no spam categories and no date-based trend. It is call-center performance data (agent, answered flag, talk duration, satisfaction, topic, speed of answer). The report is best read as a call-handling performance dashboard.

---

## Problem Statement

A support team needs one view of how its calls are handled: how many calls go unanswered, how the load is split across agents, how satisfied callers are with each agent, and which call topics take longest to answer.

## Dataset

The data is embedded in the `.pbix` file as two tables imported from an Excel sheet (`Sheet1` and `Sheet1 (2)`). The fields used in the report are:

| Field | Description |
|---|---|
| `Agent` | Agent who handled the call |
| `Answered (Y/N)` | Whether the call was answered |
| `AvgTalkDuration` | Average talk duration of the call |
| `Satisfaction rating` | Caller satisfaction rating |
| `Time` | Time of the call |
| `Topic` | Call topic / category |
| `Speed of answer in seconds` | Time taken to answer (from `Sheet1 (2)`) |

## Report Visuals

All visuals sit on a single page titled **Spam Call Analysis**. Each row below is taken from the report definition inside the `.pbix`:

| Visual | Measure | Grouped by |
|---|---|---|
| Donut chart | Count of calls | `Answered (Y/N)` |
| Column chart | Count of `AvgTalkDuration` values (calls with a talk duration) | `Agent` |
| Pie chart | Sum of `Satisfaction rating` | `Agent` |
| Line chart | Count of `Time` values (calls logged) | `Agent` |
| Clustered column chart | Sum of `Speed of answer in seconds` | `Topic` |

## Workflow

```mermaid
flowchart LR
    A[Excel call log] --> B[Power Query<br/>import & typing]
    B --> C[Two tables:<br/>Sheet1, Sheet1 (2)]
    C --> D[Aggregations:<br/>counts and sums]
    D --> E[Visuals: answer rate,<br/>calls per agent, satisfaction,<br/>speed of answer by topic]
```

## Limitations

- No spam classification exists in the data, so the report cannot show spam share, spam types or spam trends.
- The column and line charts both count calls per agent; neither shows average talk duration or a trend over time.
- Satisfaction and speed of answer are shown as sums, which favour agents and topics with more calls. Averages would compare them more fairly.

## Tech Stack

- **Microsoft Power BI Desktop**
- Power Query (data import)

## Project Structure

```
Spam-Call-Analysis-/
├── Spam Call Analysis.pbix   # Power BI report (data model + visuals)
└── README.md
```

## How to Run

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Windows).
2. Clone or download this repository:
   ```bash
   git clone https://github.com/Gonugunta-Venkata-Jayanth/Spam-Call-Analysis-.git
   ```
3. Open `Spam Call Analysis.pbix` in Power BI Desktop.
4. Use the visuals and filters to explore the data.

## Author

**Jayanth Gonugunta Venkata** · [GitHub](https://github.com/Gonugunta-Venkata-Jayanth)
