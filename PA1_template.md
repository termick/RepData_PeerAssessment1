Reproducible Research: Peer Assessment 1
========================================================

## Loading and preprocessing the data


```r
setwd("~/Documents/R/RepData")
activity <- read.csv("~/Documents/R/RepData/activity.csv")
```


## What is  mean total numbers of steps taken per day


```r
total_steps<-aggregate(steps~date, data=activity, mean, na.rm="TRUE")
hist(total_steps$steps, ylab = "Steps", col = "Red", main = "Mean total numbers of steps taken per day")
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

## What is the average daily activity pattern?



## Imputing missing values

## Are there differences in activity patterns between weekdays and weekends ?





You can also embed plots, for example:



