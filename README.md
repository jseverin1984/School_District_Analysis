# School District Analysis

## Overview

For this school district analysis, I was tasked with aggregating and analyzing the standardized testing scores of all students from a specific
school district. The overall goal was to aggregate, analyze, prepare, and showcase the data in order to identify any trends in school performance.
Providing a full analytical breakdown of the data will help those in charge of district make the best informed decisions possible when it comes 
to allocating resources and priorities when moving forward into the new school year.

## Results

After finishing the analysis, I was informed that testing scores from the ninth-grade students at Thomas High School might have been falsified
in some form or fashion. In order to better reflect all of the true data for the district, I removed all Thomas 9th grade test scores and reiterated
through all the data that would be affected by those false scores and updated the reports accordingly. Below is some of the information I found
and how it was affected. Below is the code used in order to remove the ninth-grade student test scores without affecting overall district averages
based off of a percentage of total district students.

```student_data_df.loc[(student_data_df["grade"] == "9th") & (student_data_df["school_name"] == "Thomas High School"), "reading_score"] = np.NaN```
```student_data_df.loc[(student_data_df["grade"] == "9th") & (student_data_df["school_name"] == "Thomas High School"), "math_score"] = np.NaN```

- How is the district summary affected?

	Overall, the district summary was the least affected of the data. Since the sample size was every student in the district, removing the subset
	data of ninth-graders from Thomas High School only affected the outcomes by one tenth of a percentage point.  Removing 461 scores from the
	roughly 39,000 students did not affect the data significantly.

- How is the school summary affected?

	The school summary as a whole was not affected. But, individually, the percentage passing scores for Thomas High School were affected.
	Especially before accounting for new total school count for Thomas High School. The percentage of students passing math, reading and overall
	dropped after removing the ninth-grade's scores. The first dataframe below is the data before removing the ninth-graders, and the
	second dataframe is after. The last five columns are the affected data.
![alt text](https://github.com/jseverin1984/School_District_Analysis/blob/master/Resources/thomas_before.png "scores before change")
![alt text](https://github.com/jseverin1984/School_District_Analysis/blob/master/Resources/thomas_after.png "scores after change")

- How does replacing the ninth-graders' math and reading scores affect Thomas High School's performance relative to the other schools?

	There was actually no change in performance of the tenth, eleventh, and twelfth graders from Thomas High School relative to all of the
	grades from the other schools in the district.  Thomas stayed as the second best performing school for highest standardized test scores.
 
- How does replacing the ninth-grade scores affect the following:

	1. Math and reading scores by grade
		
		Scores were unaffected.

	2. Scores by school spending
		
		Scores were unaffected.

	3. Scores by school size

		Scores were unaffected.

	4. Scores  by school type

		Scores were unaffected.

## School District Analysis Summary
	
	Several changes needed to be made to the district analysis in order to properly display student standardized testing performance.
		
		1. Removal of all ninth-grade math and reading scores from Thomas High school in the student data dataframe before merging
		   with the school data dataframe.

		2. Finding the new total student count for Thomas High School by subtracting the total number of ninth-graders from the
		   original total student count.
		
		3. Adjusting the percentage calculations for Thomas High School in the per school summary dataframe. Without recalculating
		   the total student count for Thomas High School, there percentage of students passing math, reading, and both dropped
		   significantly. And if the new adjusted percentages weren't replaced with the proper numbers after removing the ninth-graders
		   scores, the per school summary dataframe would have shown grossly under performing scores for Thomas High School.
		   Causing issues for those trying to help correct the false poor student performance.

		4. Lastly, re-analyzing all the comparative data between schools, size of schools, spending at each school, and charter
		   vs. district schools. Even though no difference ultimately resulted, making sure no changes occurred was necessary.
	