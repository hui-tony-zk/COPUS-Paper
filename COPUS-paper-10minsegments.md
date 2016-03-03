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
opts_chunk$set(echo=F, fig.width = 10, fig.height = 7)
cluster_method <- "complete"
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

![](COPUS-paper-10minsegments_files/figure-html/unnamed-chunk-9-1.png)

#### No clustering on rows

![](COPUS-paper-10minsegments_files/figure-html/unnamed-chunk-10-1.png)
