# Peer Assessment 1
Robert Huntsman  
Saturday, March 26, 2016  

# Loading and preprocessing the data

```r
setwd("C:/Users/rhuntsman/Desktop/Coursera/Reproducible Research/Project 1")
library(ggplot2)
```

```
## Warning: package 'ggplot2' was built under R version 3.1.3
```

```r
library(plyr)
```

```
## Warning: package 'plyr' was built under R version 3.1.3
```

```r
library(dplyr)
```

```
## Warning: package 'dplyr' was built under R version 3.1.3
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:plyr':
## 
##     arrange, count, desc, failwith, id, mutate, rename, summarise,
##     summarize
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
library(lattice)
```

```
## Warning: package 'lattice' was built under R version 3.1.3
```

```r
library(data.table)
```

```
## Warning: package 'data.table' was built under R version 3.1.3
```

```
## 
## Attaching package: 'data.table'
```

```
## The following objects are masked from 'package:dplyr':
## 
##     between, last
```

```r
library(knitr)
```

```
## Warning: package 'knitr' was built under R version 3.1.3
```

```r
library(lubridate)
```

```
## Warning: package 'lubridate' was built under R version 3.1.3
```

```
## 
## Attaching package: 'lubridate'
```

```
## The following objects are masked from 'package:data.table':
## 
##     hour, mday, month, quarter, wday, week, yday, year
```

```
## The following object is masked from 'package:plyr':
## 
##     here
```

```r
library(psych)
```

```
## Warning: package 'psych' was built under R version 3.1.3
```

```
## 
## Attaching package: 'psych'
```

```
## The following objects are masked from 'package:ggplot2':
## 
##     %+%, alpha
```

```r
library(reshape)
```

```
## Warning: package 'reshape' was built under R version 3.1.3
```

```
## 
## Attaching package: 'reshape'
```

```
## The following object is masked from 'package:lubridate':
## 
##     stamp
```

```
## The following object is masked from 'package:data.table':
## 
##     melt
```

```
## The following object is masked from 'package:dplyr':
## 
##     rename
```

```
## The following objects are masked from 'package:plyr':
## 
##     rename, round_any
```

```r
library(rmarkdown)
```

```
## Warning: package 'rmarkdown' was built under R version 3.1.3
```

```r
activity <- read.csv("activity.csv",stringsAsFactors=FALSE)
activity$date <- as.Date(activity$date)
```

# What is mean number of steps taken per day?

```r
dailySteps <- aggregate(steps ~ date, activity, sum)
names(dailySteps) <- c("date","steps")
hist(dailySteps$steps,col="blue",xlab="# Steps",ylab="Frequency of Days with X Steps", main="Histogram of Total Steps by Day")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png)

```r
meanSteps<- round(mean(dailySteps$steps),0)
medianSteps <- round(median(dailySteps$steps),0)

sprintf("Mean Steps Per Day: %s", meanSteps)
```

```
## [1] "Mean Steps Per Day: 10766"
```

```r
sprintf("Median Steps Per Day: %s", medianSteps)
```

```
## [1] "Median Steps Per Day: 10765"
```

# What is the average daily activity pattern?

```r
intMeanSteps <- aggregate(steps ~ interval, activity, mean)
intMedianSteps <- aggregate(steps ~ interval, activity, median)

xyplot(steps ~ interval,data=intMeanSteps,type="l",col="blue", lwd=2, main = "Avgerage Steps Per Interval", xlab = "Interval", ylab = "Steps")
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png)

```r
maxInterval <- intMeanSteps[which(intMeanSteps$steps==max(intMeanSteps$steps)),]
sprintf("Max Step Interval: %s", maxInterval$interval)
```

```
## [1] "Max Step Interval: 835"
```

```r
sprintf("Max Steps: %s", maxInterval$steps)
```

```
## [1] "Max Steps: 206.169811320755"
```

# Imputing missing values

```r
missing <- nrow(activity[is.na(activity$steps) == TRUE,])
sprintf("Numberof NA's in original data set is %s", missing)
```

```
## [1] "Numberof NA's in original data set is 2304"
```

```r
activity$steps2 <- ifelse(is.na(activity$steps), intMeanSteps[intMeanSteps$interval == activity$interval, 2], activity$steps)

dailySteps2 <- aggregate(steps2 ~ date, activity, sum)
names(dailySteps2) <- c("date","steps")

hist(dailySteps2$steps, col="blue", main = "Total Daily Steps (NA's Replaced)", xlab="Daily Steps", ylab="# Days")
```

![](PA1_template_files/figure-html/unnamed-chunk-4-1.png)

```r
meanDailySteps2 <- mean(dailySteps2$steps)
medianDailySteps2 <- median(dailySteps2$steps)

sprintf("Original Mean Steps Per Day: %s", meanSteps)
```

```
## [1] "Original Mean Steps Per Day: 10766"
```

```r
sprintf("Original Median Steps Per Day: %s", medianSteps)
```

```
## [1] "Original Median Steps Per Day: 10765"
```

```r
sprintf("New Mean Steps Per Day, NA replaced: %s", round(meanDailySteps2,0))
```

```
## [1] "New Mean Steps Per Day, NA replaced: 10766"
```

```r
sprintf("New Median Steps Per Day, NA replaced: %s", round(medianDailySteps2,0))
```

```
## [1] "New Median Steps Per Day, NA replaced: 10766"
```
## The mean and median number of steps between the original and new (NA's replaced) data sets are approximately equal.  
### The impact of imputing values for NA's is minimal.  However, the new mean and median are identical, a result
### of replacing NA's with mean values.

# Are there differences in activity patterns between weekdays and weekends?

```r
activity$weekdayGroup <- as.factor(ifelse(weekdays(activity$date) %in% c("Saturday","Sunday"),"Weekend","Weekday"))
weekdayIntervalSteps <- aggregate(steps2 ~ interval + weekdayGroup, activity, mean)

xyplot(steps2 ~ interval | weekdayGroup,
       data = weekdayIntervalSteps,
       type = "l",
       layout=c(1,2),
       lty = c(1, 2, 2, 1),
       lwd = c(2,2),
       col = c("blue"),
       main = "Average Steps Per Interval: Weekdays vs. Weekends",
       xlab = "Interval",
       ylab = "Average Steps Per Interval")
```

![](PA1_template_files/figure-html/unnamed-chunk-5-1.png)


![](PA1_template_files/figure-html/unnamed-chunk-6-1.png)

```
## png 
##   3
```

```
## png 
##   2
```

![](PA1_template_files/figure-html/unnamed-chunk-6-2.png)

```
## png 
##   3
```

```
## png 
##   2
```

![](PA1_template_files/figure-html/unnamed-chunk-6-3.png)

```
## png 
##   3
```

```
## png 
##   2
```

![](PA1_template_files/figure-html/unnamed-chunk-6-4.png)

```
## png 
##   3
```

```
## png 
##   2
```


