



# Reproducible Data Assignment 1

### Loading and preprocessing the data

Show any code that is needed to: 

- Load the data (i.e. read.csv())


```r
alldata <- read.csv("activity.csv")
```

- Process/transform the data (if necessary) into a format suitable for your analysis


```r
alldata$date <- as.Date(alldata$date, format = "%Y-%m-%d")
```

### What is mean total number of steps taken per day?

For this part of the assignment, you can ignore the missing values in the dataset.

- Calculate the total number of steps taken per day


```r
daystep <- (with(alldata,tapply(steps,date,sum)))
print(as.data.frame(daystep))
```

```
##            daystep
## 2012-10-01      NA
## 2012-10-02     126
## 2012-10-03   11352
## 2012-10-04   12116
## 2012-10-05   13294
## 2012-10-06   15420
## 2012-10-07   11015
## 2012-10-08      NA
## 2012-10-09   12811
## 2012-10-10    9900
## 2012-10-11   10304
## 2012-10-12   17382
## 2012-10-13   12426
## 2012-10-14   15098
## 2012-10-15   10139
## 2012-10-16   15084
## 2012-10-17   13452
## 2012-10-18   10056
## 2012-10-19   11829
## 2012-10-20   10395
## 2012-10-21    8821
## 2012-10-22   13460
## 2012-10-23    8918
## 2012-10-24    8355
## 2012-10-25    2492
## 2012-10-26    6778
## 2012-10-27   10119
## 2012-10-28   11458
## 2012-10-29    5018
## 2012-10-30    9819
## 2012-10-31   15414
## 2012-11-01      NA
## 2012-11-02   10600
## 2012-11-03   10571
## 2012-11-04      NA
## 2012-11-05   10439
## 2012-11-06    8334
## 2012-11-07   12883
## 2012-11-08    3219
## 2012-11-09      NA
## 2012-11-10      NA
## 2012-11-11   12608
## 2012-11-12   10765
## 2012-11-13    7336
## 2012-11-14      NA
## 2012-11-15      41
## 2012-11-16    5441
## 2012-11-17   14339
## 2012-11-18   15110
## 2012-11-19    8841
## 2012-11-20    4472
## 2012-11-21   12787
## 2012-11-22   20427
## 2012-11-23   21194
## 2012-11-24   14478
## 2012-11-25   11834
## 2012-11-26   11162
## 2012-11-27   13646
## 2012-11-28   10183
## 2012-11-29    7047
## 2012-11-30      NA
```

- Make a histogram of the total number of steps taken each day


```r
hist(daystep, breaks = 20, xlab = "Number of steps taken each day", col = "red",
     main = "Histogram of steps taken each day")
```

![plot of chunk histogram](figure/histogram-1.png)

- Calculate and report the mean and median total number of steps taken per day


```r
library(dplyr)
meanmed <- alldata
meanmed %>% 
        group_by(date) %>% 
        summarize(mean = mean(steps), median = median(steps)) %>% 
        print.data.frame
```

```
##          date       mean median
## 1  2012-10-01         NA     NA
## 2  2012-10-02  0.4375000      0
## 3  2012-10-03 39.4166667      0
## 4  2012-10-04 42.0694444      0
## 5  2012-10-05 46.1597222      0
## 6  2012-10-06 53.5416667      0
## 7  2012-10-07 38.2465278      0
## 8  2012-10-08         NA     NA
## 9  2012-10-09 44.4826389      0
## 10 2012-10-10 34.3750000      0
## 11 2012-10-11 35.7777778      0
## 12 2012-10-12 60.3541667      0
## 13 2012-10-13 43.1458333      0
## 14 2012-10-14 52.4236111      0
## 15 2012-10-15 35.2048611      0
## 16 2012-10-16 52.3750000      0
## 17 2012-10-17 46.7083333      0
## 18 2012-10-18 34.9166667      0
## 19 2012-10-19 41.0729167      0
## 20 2012-10-20 36.0937500      0
## 21 2012-10-21 30.6284722      0
## 22 2012-10-22 46.7361111      0
## 23 2012-10-23 30.9652778      0
## 24 2012-10-24 29.0104167      0
## 25 2012-10-25  8.6527778      0
## 26 2012-10-26 23.5347222      0
## 27 2012-10-27 35.1354167      0
## 28 2012-10-28 39.7847222      0
## 29 2012-10-29 17.4236111      0
## 30 2012-10-30 34.0937500      0
## 31 2012-10-31 53.5208333      0
## 32 2012-11-01         NA     NA
## 33 2012-11-02 36.8055556      0
## 34 2012-11-03 36.7048611      0
## 35 2012-11-04         NA     NA
## 36 2012-11-05 36.2465278      0
## 37 2012-11-06 28.9375000      0
## 38 2012-11-07 44.7326389      0
## 39 2012-11-08 11.1770833      0
## 40 2012-11-09         NA     NA
## 41 2012-11-10         NA     NA
## 42 2012-11-11 43.7777778      0
## 43 2012-11-12 37.3784722      0
## 44 2012-11-13 25.4722222      0
## 45 2012-11-14         NA     NA
## 46 2012-11-15  0.1423611      0
## 47 2012-11-16 18.8923611      0
## 48 2012-11-17 49.7881944      0
## 49 2012-11-18 52.4652778      0
## 50 2012-11-19 30.6979167      0
## 51 2012-11-20 15.5277778      0
## 52 2012-11-21 44.3993056      0
## 53 2012-11-22 70.9270833      0
## 54 2012-11-23 73.5902778      0
## 55 2012-11-24 50.2708333      0
## 56 2012-11-25 41.0902778      0
## 57 2012-11-26 38.7569444      0
## 58 2012-11-27 47.3819444      0
## 59 2012-11-28 35.3576389      0
## 60 2012-11-29 24.4687500      0
## 61 2012-11-30         NA     NA
```

### What is the average daily activity pattern?

- Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)


```r
tseries <- as.data.frame(with(alldata,tapply(steps,interval,mean,na.rm=TRUE)))
plot(y=t(tseries),
     x=row.names(tseries),
     typ="l",
     lwd=2,
     col="blue",
     main="Average number of step taken across days, by interval", 
     ylab="Average number of steps", 
     xlab = "Interval")
```

![plot of chunk tseries](figure/tseries-1.png)

- Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?


```r
tseries[which(tseries==max(tseries)),]
```

```
##      835 
## 206.1698
```

### Imputing missing values

Note that there are a number of days/intervals where there are missing values (coded as NA). The presence of missing days may introduce bias into some calculations or summaries of the data.

- Calculate and report the total number of missing values in the dataset (i.e. the total number of rows with NAs)


```r
sum(is.na(alldata))
```

```
## [1] 2304
```

- Devise a strategy for filling in all of the missing values in the dataset. The strategy does not need to be sophisticated. For example, you could use the mean/median for that day, or the mean for that 5-minute interval, etc.


```r
alldata %>% group_by(date) %>% summarize(nas = sum(is.na(steps))) %>% filter(nas>0)
```

```
## Source: local data frame [8 x 2]
## 
##         date   nas
##       (date) (int)
## 1 2012-10-01   288
## 2 2012-10-08   288
## 3 2012-11-01   288
## 4 2012-11-04   288
## 5 2012-11-09   288
## 6 2012-11-10   288
## 7 2012-11-14   288
## 8 2012-11-30   288
```

*Comment:*  isolating NAs shows that they exist for whole days only, so appropriate strategy is to replace NAs with interval mean computed across days.

- Create a new dataset that is equal to the original dataset but with the missing data filled in.


```r
repdata <- alldata    
i = 1    
for (i in (1:nrow(repdata))) {
    if (is.na(repdata$steps[i])) {
        repdata$steps[i] <- mean(subset(alldata,
                                        alldata$interval==alldata$interval[i])[,1], 
                                na.rm = TRUE)

    }
    i = i+1
}
```

- Make a histogram of the total number of steps taken each day and Calculate and report the mean and median total number of steps taken per day. Do these values differ from the estimates from the first part of the assignment? What is the impact of imputing missing data on the estimates of the total daily number of steps?


```r
repdaystep <- (with(repdata,tapply(steps,date,sum)))
hist(repdaystep, breaks = 20, xlab = "Number of steps taken each day", col = "red",
     main = "Histogram of steps taken each day")
```

![plot of chunk rephistogram](figure/rephistogram-1.png)


```r
repmeanmed <- repdata
repmeanmed %>% 
        group_by(date) %>% 
        summarize(mean = mean(steps), median = median(steps)) %>% 
        print.data.frame
```

```
##          date       mean   median
## 1  2012-10-01 37.3825996 34.11321
## 2  2012-10-02  0.4375000  0.00000
## 3  2012-10-03 39.4166667  0.00000
## 4  2012-10-04 42.0694444  0.00000
## 5  2012-10-05 46.1597222  0.00000
## 6  2012-10-06 53.5416667  0.00000
## 7  2012-10-07 38.2465278  0.00000
## 8  2012-10-08 37.3825996 34.11321
## 9  2012-10-09 44.4826389  0.00000
## 10 2012-10-10 34.3750000  0.00000
## 11 2012-10-11 35.7777778  0.00000
## 12 2012-10-12 60.3541667  0.00000
## 13 2012-10-13 43.1458333  0.00000
## 14 2012-10-14 52.4236111  0.00000
## 15 2012-10-15 35.2048611  0.00000
## 16 2012-10-16 52.3750000  0.00000
## 17 2012-10-17 46.7083333  0.00000
## 18 2012-10-18 34.9166667  0.00000
## 19 2012-10-19 41.0729167  0.00000
## 20 2012-10-20 36.0937500  0.00000
## 21 2012-10-21 30.6284722  0.00000
## 22 2012-10-22 46.7361111  0.00000
## 23 2012-10-23 30.9652778  0.00000
## 24 2012-10-24 29.0104167  0.00000
## 25 2012-10-25  8.6527778  0.00000
## 26 2012-10-26 23.5347222  0.00000
## 27 2012-10-27 35.1354167  0.00000
## 28 2012-10-28 39.7847222  0.00000
## 29 2012-10-29 17.4236111  0.00000
## 30 2012-10-30 34.0937500  0.00000
## 31 2012-10-31 53.5208333  0.00000
## 32 2012-11-01 37.3825996 34.11321
## 33 2012-11-02 36.8055556  0.00000
## 34 2012-11-03 36.7048611  0.00000
## 35 2012-11-04 37.3825996 34.11321
## 36 2012-11-05 36.2465278  0.00000
## 37 2012-11-06 28.9375000  0.00000
## 38 2012-11-07 44.7326389  0.00000
## 39 2012-11-08 11.1770833  0.00000
## 40 2012-11-09 37.3825996 34.11321
## 41 2012-11-10 37.3825996 34.11321
## 42 2012-11-11 43.7777778  0.00000
## 43 2012-11-12 37.3784722  0.00000
## 44 2012-11-13 25.4722222  0.00000
## 45 2012-11-14 37.3825996 34.11321
## 46 2012-11-15  0.1423611  0.00000
## 47 2012-11-16 18.8923611  0.00000
## 48 2012-11-17 49.7881944  0.00000
## 49 2012-11-18 52.4652778  0.00000
## 50 2012-11-19 30.6979167  0.00000
## 51 2012-11-20 15.5277778  0.00000
## 52 2012-11-21 44.3993056  0.00000
## 53 2012-11-22 70.9270833  0.00000
## 54 2012-11-23 73.5902778  0.00000
## 55 2012-11-24 50.2708333  0.00000
## 56 2012-11-25 41.0902778  0.00000
## 57 2012-11-26 38.7569444  0.00000
## 58 2012-11-27 47.3819444  0.00000
## 59 2012-11-28 35.3576389  0.00000
## 60 2012-11-29 24.4687500  0.00000
## 61 2012-11-30 37.3825996 34.11321
```

*Comment:* Data are much more concentrated around the mean

### Are there differences in activity patterns between weekdays and weekends?

- Create a new factor variable in the dataset with two levels -- "weekday" and "weekend" indicating whether a given date is a weekday or weekend day.


```r
repdata <- mutate(repdata,sapply(weekdays(alldata$date), 
                                 function(x) {
                                     ifelse(x == "Saturday" | x == "Sunday", 
                                            "weekend",
                                            "weekday")}))
colnames(repdata)[4]="day"
```

- Make a panel plot containing a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all weekday days or weekend days (y-axis).


```r
tsweekday <- as.data.frame(with(subset(repdata, day == "weekday"),
                                tapply(steps,interval,mean)))
tsweekend <- as.data.frame(with(subset(repdata, day == "weekend"),
                                tapply(steps,interval,mean)))

par(mfrow=c(2,1), mar = c(4, 4, 2, 1), oma = c(0, 0, 2, 0))
plot(y=t(tsweekday),
     x=row.names(tsweekday),
     typ="l",
     lwd=2,
     col="blue",
     main="Average number of step taken during weekdays", 
     ylab="Average number of steps", 
     xlab = "Interval")

plot(y=t(tsweekend),
     x=row.names(tsweekend),
     typ="l",
     lwd=2,
     col="blue",
     main="Average number of step taken during weekends", 
     ylab="Average number of steps", 
     xlab = "Interval")
```

![plot of chunk timeseries](figure/timeseries-1.png)

