# CITS4407 — Assessment 2

**Unit:** CITS4407  
**Author:** BHARATH KRISHNA  
**Student ID:** 25182359  

## Question 1: Error Checks and Data Cleaning

The `clean` script reads an input CSV file provided as a command-line argument and generates a cleaned output file named `trending_videos_clean.csv`.

The default input file for this project is `trending_videos_unclean.csv`, located in the same directory as the script.

### Input Data

The input CSV file contains the following fields in a fixed order:

- `video_id`
- `publish_date`
- `views`
- `likes`
- `dislikes`
- `comments_disabled`
- `ratings_disabled`

### Error Checks

The script handles the following error cases:

| Error Case | Output |
|---|---|
| No input file specified | `ERROR: No input CSV file provided` |
| Input file not found in the current directory | `ERROR: Input file not found in the current directory` |
| Input file is not a CSV file | `ERROR: Input file expected in a CSV format` |
| Input file is empty | `ERROR: Empty file provided` |
| Incorrect number of fields in the header | `ERROR: Expected 7 columns in the header` |

### Data Cleaning Operations

The script performs the following cleaning operations:

- Removes the `ratings_disabled` column
- Removes rows with inconsistent field counts (including rows with empty fields)
- Removes duplicate rows
- Removes rows with missing `video_id`
- Removes rows where `likes` or `dislikes` are zero
- Removes the time component from `publish_date`

Example:

```text
2009-09-18T15:36:33.000Z
```

becomes:

```text
2009-09-18
```

### Usage

```bash
./clean trending_videos_unclean.csv
```

## Submission Contents

The ZIP submission includes:

- `clean`
- `analyse`
- `prompts.pdf`
- `git_backup`
- `README.md`

To create `git_backup` from the repository:

```bash
cp -r .git git_backup
```