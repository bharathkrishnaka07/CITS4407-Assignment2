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

### How to run this script:

```bash
./clean trending_videos_unclean.csv
```

## Question 2: Data Analysis

The `analyse` script reads a cleaned CSV file provided as a command-line argument and performs multiple data analysis operations on the dataset.

The default input file for this project is `trending_videos_clean.csv`, located in the same directory as the script.

### Input Data

The input CSV file contains the following fields in a fixed order:

- `video_id`
- `publish_date`
- `views`
- `likes`
- `dislikes`
- `comments_disabled`

### Error Checks

The script handles the following error cases:

| Error Case | Output |
|---|---|
| Incorrect number of command-line arguments | `ERROR: ./analyse expects exactly one argument` |
| Input file is not a CSV file | `ERROR: Input file expected in a CSV format` |
| Input file does not exist, is not readable or is empty | `ERROR: The specified input file <file_name> does not exist, is not readable or is empty` |

### Data Analysis Operations

The script performs the following analysis operations:

- Calculates and prints the `video_id` of the video with the highest number of occurrences
- Calculates and prints the mean number of views rounded to 2 decimal places
- Calculates and prints the `video_id` of the video with the maximum number of dislikes
- Calculates and prints the `video_id` and `publish_date` of the video with the highest engagement rate
- Calculates and prints the `video_id` and `publish_date` of the video with the least net sentiment rate
- Displays all tied results clearly and sensibly where applicable

### Engagement Rate Formula

```text
(likes + dislikes) / views
```

### Net Sentiment Rate Formula

```text
(likes - dislikes) / views
```

### Sample Output

```text
Most frequent video, ID: id4667
Mean number of views: 2355595.97
Max dislikes video, ID: id2798
Highest engagement rate video, ID: id2282, dated: 2018-01-04
Least sentiment rate video, ID: id2219, dated: 2017-12-13
```

### How to run this script:

```bash
./analyse trending_videos_clean.csv
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