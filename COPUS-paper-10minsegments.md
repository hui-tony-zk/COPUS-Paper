# COPUS Analysis for publication
Tony Hui  

# Processing the data


```
## Loading required package: knitr
```



## Cluster ignoring time

### Cluster of all classes

The x-axis labels represent course-instructor-semester pairings:

Course 11, instructor A, semester 1 = 11-A-1

Fractional time was calculated as a mean of all observations



![](COPUS-paper-10minsegments_files/figure-html/all_years_all_times_cluster-1.png)

### Cluster of first-year classes



![](COPUS-paper-10minsegments_files/figure-html/first_year_all_times_cluster-1.png)

## Cluster, slicing time into 10-minute intervals

### All classes, sliced, clustered



![](COPUS-paper-10minsegments_files/figure-html/all_years_sliced_times_cluster-1.png)

### first year classes, sliced, clustered



![](COPUS-paper-10minsegments_files/figure-html/first_year_sliced_times_cluster-1.png)

### first year and second year classes, sliced, clustered based on classes X chunk*metric



![](COPUS-paper-10minsegments_files/figure-html/jr_sliced_times_cluter_rows-1.png)

#### No clustering on columns

![](COPUS-paper-10minsegments_files/figure-html/unnamed-chunk-8-1.png)

#### No clustering on rows

![](COPUS-paper-10minsegments_files/figure-html/unnamed-chunk-9-1.png)

### first year only

![](COPUS-paper-10minsegments_files/figure-html/unnamed-chunk-10-1.png)

## Rule association mining

From first and second year classes

![](COPUS-paper-10minsegments_files/figure-html/unnamed-chunk-11-1.png)

**Cluster one** on the right, **cluster two** on the left


```
## Joining by: "id"
```

See which "features" are significantly different between the two clusters


|measure                              |  pval|   fdr|
|:------------------------------------|-----:|-----:|
|Instructor.Lecturing-chunk3          | 0.000| 0.000|
|Instructor.WritingOnBoard-chunk5     | 0.003| 0.117|
|Instructor.Lecturing-chunk4          | 0.009| 0.342|
|Instructor.Lecturing-chunk5          | 0.009| 0.342|
|Instructor.GivingFeedback-chunk3     | 0.019| 0.684|
|Instructor.WritingOnBoard-chunk3     | 0.022| 0.770|
|Instructor.WritingOnBoard-chunk2     | 0.024| 0.816|
|Instructor.WritingOnBoard-chunk4     | 0.030| 0.990|
|Students.GroupWork-chunk3            | 0.035| 1.000|
|Instructor.MovingThroughGroup-chunk1 | 0.036| 1.000|

Visualize the chunks with pvalue < 0.05

![](COPUS-paper-10minsegments_files/figure-html/unnamed-chunk-14-1.png)

## Heatmap over time for the two clusters

Average the of all classes that fall within cluster 1 or 2 and plot over time.


```
## Joining by: "id"
```

![](COPUS-paper-10minsegments_files/figure-html/unnamed-chunk-15-1.png)

