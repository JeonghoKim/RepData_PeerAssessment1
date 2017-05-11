
# "Reproducible Research Course Project 1"


.The data for the assignment can be downloaded [here] .(https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2Factivity.zip). 

## Loading and preprocessing the data


```r
library(ggplot2)
library(plyr)
activity <- read.csv("activity.csv")
activity$day <- weekdays(as.Date(activity$date))
activity$DateTime <- as.POSIXct(activity$date, format="%Y-%m-%d")
```

.pulling data without nas


```r
clean <- activity[!is.na(activity$steps),]
```

## What is mean total number of steps taken per day?

summarizing total steps per date


```r
sumTable <- aggregate(activity$steps ~ activity$date, FUN=sum, )
colnames(sumTable)<- c("Date", "Steps")
```

.Creating the historgram of total steps per day


```r
hist(sumTable$Steps, breaks=5, xlab="Steps", main = "Total Steps per Day")
```

![plot of chunk histogram1](figure/histogram1-1.png)

```r
as.integer(mean(sumTable$Steps))
```

```
## [1] 10766
```

```r
as.integer(median(sumTable$Steps))
```

```
## [1] 10765
```

## What is the average daily activity pattern?

.pulling data without nas


```r
clean <- activity[!is.na(activity$steps),]
```

.create average number of steps per interval


```r
intervalTable <- ddply(clean, .(interval), summarize, Avg = mean(steps))
```

.Create line plot of average number of steps per interval


```r
p <- ggplot(intervalTable, aes(x=interval, y=Avg), xlab = "Interval", 
            ylab="Average Number of Steps")
p + geom_line()+xlab("Interval")+ylab("Average Number of Steps")+
        ggtitle("Average Number of Steps per Interval")
```

![plot of chunk timeplot1](figure/timeplot1-1.png)

.Mean and median of total number of steps taken per day


```r
maxSteps <- max(intervalTable$Avg)
intervalTable[intervalTable$Avg==maxSteps,1]
```

```
## [1] 835
```

## Imputing missing values

.Number of NAs in original data set


```r
nrow(activity[is.na(activity$steps),])
```

```
## [1] 2304
```

.Create the average number of steps per weekday and interval


```r
avgTable <- ddply(clean, .(interval, day), summarize, Avg = mean(steps))
nadata<- activity[is.na(activity$steps),]
```

.Merge NA data with average weekday interval for substitution


```r
newdata<-merge(nadata, avgTable, by=c("interval", "day"))
```

Reorder the new substituded data in the same format as clean data set


```r
newdata2<- newdata[,c(6,4,1,2,5)]
colnames(newdata2)<- c("steps", "date", "interval", "day", "DateTime")
```

.Merge the NA averages and non NA data together


```r
mergeData <- rbind(clean, newdata2)
```

.Create sum of steps per date to compare with step 1


```r
sumTable2 <- aggregate(mergeData$steps ~ mergeData$date, FUN=sum, )
colnames(sumTable2)<- c("Date", "Steps")
```

.Mean and Median of Steps with NA data taken care of


```r
as.integer(mean(sumTable2$Steps))
```

```
## [1] 10821
```

```r
as.integer(median(sumTable2$Steps))
```

```
## [1] 11015
```

.Creating the histogram of total steps per day, categorized by data set to show impact


```r
hist(sumTable2$Steps, breaks=5, xlab="Steps", main = "Total Steps per Day with NAs Fixed", 
     col="Black")
hist(sumTable$Steps, breaks=5, xlab="Steps", main = "Total Steps per Day with NAs Fixed", col="Grey", add=T)
legend("topright", c("Imputed Data", "Non-NA Data"), fill=c("black", "grey") )
```

![plot of chunk histogram2](figure/histogram2-1.png)

## Are there differences in activity patterns between weekdays and weekends?

.Create new category based on the days of the week


```r
mergeData$DayCategory <- ifelse(mergeData$day %in% c("Saturday", "Sunday"), "Weekend", "Weekday")
library(lattice) 
```

.Summarize data by interval and type of day


```r
intervalTable2 <- ddply(mergeData, .(interval, DayCategory), summarize, Avg = mean(steps))
```

.Plot data in a panel plot


```r
xyplot(Avg~interval|DayCategory, data=intervalTable2, type="l",  layout = c(1,2),
       main="Average Steps per Interval Based on Type of Day", 
       ylab="Average Number of Steps", xlab="Interval")
```

![plot of chunk timeplot2](figure/timeplot2-1.png)
