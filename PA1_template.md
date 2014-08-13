Reproducible Research: Peer Assessment 1
========================================================

## Loading and preprocessing the data


```r
setwd("~/Documents/R/RepData")
activity <- read.csv("~/Documents/R/RepData/activity.csv")
```


## What is  mean total numbers of steps taken per day


```r
total_steps<-aggregate(steps~date, data=activity, sum, na.rm="TRUE")
hist(total_steps$steps, xlab = "Steps", col = "Red", main = "Mean total numbers of steps taken per day")
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

```r
steps_mean<-mean(total_steps$steps)
steps_median<-median(total_steps$steps)
steps_mean
```

```
## [1] 10766
```

```r
steps_median
```

```
## [1] 10765
```

## What is the average daily activity pattern?

```r
interval_steps<-aggregate(steps~interval, data=activity, mean, na.rm="TRUE")
plot(steps~interval, data=interval_steps, type="l")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

```r
max(interval_steps$steps)
```

```
## [1] 206.2
```

## Imputing missing values


```r
colSums(is.na(activity))
```

```
##    steps     date interval 
##     2304        0        0
```

```r
new_value<-mean(activity$steps, na.rm="TRUE")
activity_new<-activity
activity_new$steps[is.na(activity_new$steps)] <- new_value
colSums(is.na(activity_new))
```

```
##    steps     date interval 
##        0        0        0
```

```r
total_steps1<-aggregate(steps~date, data=activity_new, sum, na.rm="TRUE")
hist(total_steps1$steps, xlab = "Steps", col = "Red", main = "Mean total numbers of steps taken per day")
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 

```r
steps_mean1<-mean(total_steps1$steps)
steps_median1<-median(total_steps1$steps)
steps_mean1
```

```
## [1] 10766
```

```r
steps_median1
```

```
## [1] 10766
```


## Are there differences in activity patterns between weekdays and weekends ?





You can also embed plots, for example:



