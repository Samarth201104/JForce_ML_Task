# Student Marks Processing

## Objective

Convert student subject-wise exam records into one row per **Roll No** and **Subject**. A student may attempt the same subject multiple times; the output keeps the three most recent attempts.

## Input

The program reads `data/input.csv`, with these columns:

| Column | Description |
|---|---|
| Roll No | Student identifier |
| Subject | Subject attempted |
| Marks | Marks for that attempt |
| Date | Attempt date in `DD-MM-YY` format |

Example:

```csv
Roll No,Subject,Marks,Date
1,DS,25,01-01-23
1,Java,40,02-01-23
2,DS,30,01-01-23
2,Java,26,02-01-23
1,DS,40,15-01-23
2,Java,50,15-01-23
```

## Output

The program writes the consolidated records to `data/output.csv`:

| Roll No | Subject | M1 | M2 | M3 | Date |
|---:|---|---:|---:|---:|---|
| 1 | DS | 40 | 25 | 0 | 15-01-23 |
| 1 | Java | 40 | 0 | 0 | 02-01-23 |
| 2 | DS | 30 | 0 | 0 | 01-01-23 |
| 2 | Java | 50 | 26 | 0 | 15-01-23 |

- `M1`, `M2`, and `M3` are the latest, second-latest, and third-latest marks, respectively. Attempts older than the latest three are ignored.
- Missing attempt marks are filled with `0`.
- `Date` is the date of the latest attempt (`M1`).

## Run

Install the dependency and run the script from the project directory:

```bash
pip install -r requirements.txt
python main.py
```
