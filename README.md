#School District Analysis - Pandas

## Overview of the School District Analysis

The purpose of this analysis is to understand and showcase if the trends of a school district performance changed after taking out some datapoints. The raw data file used for an analysis of a school district showed evidence of dishonesty. As a result, an additional analysis had to be made, taking out the data showing evidence of dishonestoy. Given that the math and reading scores for Thomas High School showed evidence of academic dishonesty, they were replaced with NaNs while keeping the rest o the data intact.

## Results

### How is the district summary affected?

- After taking out the math and reading results of the 9th graders at Thomas High School, the average math score decreased by 0.1 points (from 79 to 78.9)

  <img src="images/district_summary_df.png">

### How is the school summary affected?

- Replacing the Thomas High School 9th grade data with NaNs only slighlty affected the school summary for Thomas High School.
- Thomas High School percent of passing math went up from 93.27% to 94.59% and its percent of passing reading went down from 97.3% to 95.9%
- Thomas High School percent overall passing went slightly down from 90.94% to 90.54%

Below image shows the updated metrics for Thomas High School:

  <img src="images/ths_nans_updated.png">

### How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?

- Replacing the night graders'math and reading scores did not affect its performance relative to other schools. Thomas School is still ranked #2 after replacing the ninth graders data.

Below image shows the updated top performing schools:

  <img src="images/top_schools_updated.png">

### Math and reading scores by grade

- Replacing the ninth-grade scores affects only Thomas High School score for 9h grade, showing NaN.

### Scores by school spending

- Replacing the ninth-grade scores does not affect the scores by school spending.

### Scores by school size

- Replacing the ninth-grade scores does not affect the scores by school size.

### Scores by school type

- Replacing the ninth-grade scores does not affect the scores by school type.

## Summary

The results of the updated school district analysis did not change significantly after reading and math scores for the ninth grade at Thomas High School were replaced with NaNs. However, the process to obtain results in the updated analysis was a bit different from the one followed in the initial analysis.

1. In the updated analysis we had to calculate a new student total for Thomas High School in order to consider only students from grades 10th-12th and obtain a correct percent metrics.

```
# Step 5.  Get the number of 10th-12th graders from Thomas High School (THS).
tenth_grade = school_data_complete_df["grade"] == "10th"
eleventh_grade = school_data_complete_df["grade"] == "11th"
twelfth_grade = school_data_complete_df["grade"] == "12th"
ths_students = school_data_complete_df["school_name"] == "Thomas High School"

ths_tenth_twelfth_count = school_data_complete_df.loc[( tenth_grade | eleventh_grade | twelfth_grade) & ths_students]["Student ID"].count()
ths_tenth_twelfth_count

```

2. In the updated analysis we had to filter the school_data_complete_df dataframe using .loc to retrieve only the infomration pertaining to 10-12th grades in Thomas High School.

3. In the updated analysis we had to change the information pertaining to Thomas High School night graders in the per_school_summary_df dataframe.

`per_school_summary_df.loc["Thomas High School","% Passing Math"] = ths_passing_math_pct`

4. In the updated analysis the scores by grade dataframe does not show information (NaNs) for 9th grade Thomas High School
