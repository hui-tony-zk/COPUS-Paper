# COPUS Analysis for publication
Tony Hui  

# Processing the data


```r
require(knitr)
```

```
## Loading required package: knitr
```

```r
opts_chunk$set(echo=F)
```





## Sanity check the data


```
## [1] "Number of Columns for all files: 31"
```

Remove classes that are shorter than 45 minutes and longer than 51 minutes


  x   freq
---  -----
 16      1
 17      2
 18      1
 19      3
 20      2
 21      2
 22      4
 23     17
 24     22
 25     13
 27      1
 33      1
 34      3
 35      2
 36      3
 37      3
 38      2
 39      6
 40      2

![](COPUS-paper_files/figure-html/class_lengths-1.png)



## Combine data from all classes/observations into one file



### Filter out unwanted variables

Notes from Megan: The 8 variables used in the Lund et al paper (and their short form codes from Lund’s Table 4) are:

* Student-AnsweringQuestion (AnQ-S)
* Student-AskingQuestion (SQ)
* Instructor-AskingClickerQuestion (CQ)
* Instructor-GivingFeedback (FUp)
* Instructor-Lecturing (Lec)
* Instructor-WritingOnBoard (RtW)
* Instructor-MovingThroughGroup (MG)
* Students-GroupWork (GW) 
    + this is an amalgam of the three student groupwork codes, which we need to process.  It is considered checked off (“1”) if any of the three student groupwork raw codes occurs in the given interval. (Students-ClickerQuestionInGroups. Students-Worksheet, Students-OtherGroupwork)


| time|course |instructor |semester |observation |year | Student.AnsweringQuestion| Student.AskingQuestion| Instructor.AskingClickerQuestion| Instructor.GivingFeedback| Instructor.Lecturing| Instructor.WritingOnBoard| Instructor.MovingThroughGroup| Students.GroupWork|
|----:|:------|:----------|:--------|:-----------|:----|-------------------------:|----------------------:|--------------------------------:|-------------------------:|--------------------:|-------------------------:|-----------------------------:|------------------:|
|    2|11     |A          |1        |2           |1    |                         1|                      0|                                0|                         0|                    1|                         0|                             0|                  1|
|    4|11     |A          |1        |2           |1    |                         0|                      1|                                0|                         1|                    1|                         0|                             0|                  0|
|    6|11     |A          |1        |2           |1    |                         0|                      0|                                1|                         0|                    0|                         0|                             0|                  1|
|    8|11     |A          |1        |2           |1    |                         0|                      0|                                1|                         0|                    1|                         0|                             0|                  0|
|   10|11     |A          |1        |2           |1    |                         0|                      0|                                1|                         1|                    1|                         0|                             0|                  1|
|   12|11     |A          |1        |2           |1    |                         0|                      0|                                1|                         1|                    0|                         0|                             0|                  1|

## Process the class performance data


|course |instructor |semester | EffectSize.StudentPerformance| SE.EffectSize.StudentPerformance|ClassSize     |CopusProfile                           |CopusStyle       | TeachingPracticesInventoryScore| NormalizedChange.StudentPerformance| SE.NormalizedChange.StudentPerformance|
|:------|:----------|:--------|-----------------------------:|--------------------------------:|:-------------|:--------------------------------------|:----------------|-------------------------------:|-----------------------------------:|--------------------------------------:|
|11     |A          |1        |                          2.91|                             0.17|More than 200 |Student-Centered Peer Instruction      |Collaborative    |                              20|                            74.09648|                               1.853726|
|11     |B          |1        |                          1.51|                             0.16|More than 200 |Limited Peer Instruction (with slides) |Peer Instruction |                              20|                            56.49132|                               3.643105|
|11     |C          |1        |                          2.65|                             0.15|More than 200 |Student-Centered Peer Instruction      |Collaborative    |                              20|                            70.73516|                               2.167993|
|11     |D          |1        |                          2.75|                             0.16|More than 200 |Student-Centered Peer Instruction      |Collaborative    |                              20|                            69.68558|                               1.855365|
|12     |E          |2        |                          1.36|                             0.21|More than 200 |Teacher-Centered Peer Instruction      |Peer Instruction |                              16|                            29.07547|                               3.354000|
|12     |H          |2        |                          1.05|                             0.18|More than 200 |Student-Centered Peer Instruction      |Collaborative    |                              17|                            22.28033|                               3.297568|

### Merge performance data with the classes data


```
## Joining by: c("course", "instructor", "semester")
```

# Basic exploratory analysis

## Fractional amount of time spent on each category overall per class

![](COPUS-paper_files/figure-html/frac_time_per_class-1.png)

## Fractional amount of time spent on each category overall per class year

![](COPUS-paper_files/figure-html/frac_time_per_class_per_year-1.png)

## Number of different instructor-semester pairings per per course

![](COPUS-paper_files/figure-html/instructors_per_course-1.png)

## Fractional amount of time spent on each category for course `12`, and `11`, further granuarized by instructor

The labels in each box represents the course id

![](COPUS-paper_files/figure-html/time_spent_by_course_by_instructor-1.png)

## Time spent on lecture vs student growth

All courses - each dot is one course (separated by year level)

![](COPUS-paper_files/figure-html/student_perf_vs_lecture_time-1.png)

Looks like there's a positive correlation with lecture time and student performance in first year classes, and a negative correlation in second year classes

# Question 1: Which activities (individually) has an effect on student performance?

## Plot the variation of each measure for a single course and compare across instructors-semester pairings

It really doesn't make sense to look across courses since different courses have different content = different methods of learning - scientific method: only vary one variable at a time.

### Plot the variation of each measure for course 12 between instructors-semester pairings

![](COPUS-paper_files/figure-html/variations_in_activities-1.png)

## Plot correlation between the top activities with the highest variations


|course |measure                          | mean_frac_time| sd_frac_time|
|:------|:--------------------------------|--------------:|------------:|
|11     |Instructor.GivingFeedback        |      0.3015298|    0.2239104|
|11     |Instructor.Lecturing             |      0.6415056|    0.2001084|
|11     |Student.AnsweringQuestion        |      0.2083333|    0.1909407|
|12     |Instructor.WritingOnBoard        |      0.3649902|    0.2586767|
|12     |Instructor.AskingClickerQuestion |      0.1942466|    0.1904896|
|12     |Instructor.GivingFeedback        |      0.4514269|    0.1698411|

```
## Joining by: c("course", "measure")
```

```
## Joining by: c("course", "instructor", "semester", "EffectSize.StudentPerformance")
```

![](COPUS-paper_files/figure-html/correlate_variable_activities-1.png)



# Question 3 - which classes are arranged such that they have similar amounts of time spent on each activity?

The more "red" the color, the more time that activity is spent on class



![](COPUS-paper_files/figure-html/course_of_interest_only_clustering-1.png)

## What about across all courses?


![](COPUS-paper_files/figure-html/all_courses_clustering-1.png)
