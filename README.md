# RepData_PeerAssessment1
## Assignment
This assignment will be described in multiple parts. You will need towrite a report that answers the questions detailed below. Ultimately,you will need to complete the entire assignment in a **single Rmarkdown** document that can be processed by **knitr** and betransformed into an HTML file.
Throughout your report make sure you always include the code that youused to generate the output you present. When writing code chunks inthe R markdown document, always use `echo = TRUE` so that someone elsewill be able to read the code. **This assignment will be evaluated viapeer assessment so it is essential that your peer evaluators be ableto review the code for your analysis**.
For the plotting aspects of this assignment, feel free to use anyplotting system in R (i.e., base, lattice, ggplot2)
Fork/clone the [GitHub repository created for thisassignment](http://github.com/rdpeng/RepData_PeerAssessment1). Youwill submit this assignment by pushing your completed files into yourforked repository on GitHub. The assignment submission will consist ofthe URL to your GitHub repository and the SHA-1 commit ID for yourrepository state.
NOTE: The GitHub repository also contains the dataset for theassignment so you do not have to download the data separately.

### Loading and preprocessing the data
Show any code that is needed to
1. Load the data (i.e. `read.csv()`)
2. Process/transform the data (if necessary) into a format suitable for your analysis
### What is mean total number of steps taken per day?
For this part of the assignment, you can ignore the missing values inthe dataset.
1. Make a histogram of the total number of steps taken each day
2. Calculate and report the **mean** and **median** total number of steps taken per day
### What is the average daily activity pattern?
1. Make a time series plot (i.e. `type = "l"`) of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)
2. Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?
### Imputing missing values
Note that there are a number of days/intervals where there are missingvalues (coded as `NA`). The presence of missing days may introducebias into some calculations or summaries of the data.
1. Calculate and report the total number of missing values in the dataset (i.e. the total number of rows with `NA`s)
2. Devise a strategy for filling in all of the missing values in the dataset. The strategy does not need to be sophisticated. For example, you could use the mean/median for that day, or the mean for that 5-minute interval, etc.
3. Create a new dataset that is equal to the original dataset but with the missing data filled in.
4. Make a histogram of the total number of steps taken each day and Calculate and report the **mean** and **median** total number of steps taken per day. Do these values differ from the estimates from the first part of the assignment? What is the impact of imputing missing data on the estimates of the total daily number of steps?
### Are there differences in activity patterns between weekdays and weekends?
For this part the `weekdays()` function may be of some help here. Usethe dataset with the filled-in missing values for this part.
1. Create a new factor variable in the dataset with two levels -- "weekday" and "weekend" indicating whether a given date is a weekday or weekend day.
1. Make a panel plot containing a time series plot (i.e. `type = "l"`) of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all weekday days or weekend days (y-axis). The plot should look something like the following, which was created using **simulated data**:
![Sample panel plot](instructions_fig/sample_panelplot.png) 
**Your plot will look different from the one above** because you willbe using the activity monitor data. Note that the above plot was madeusing the lattice system but you can make the same version of the plotusing any plotting system you choose.
## Submitting the Assignment
To submit the assignment:
1. Commit your completed `PA1_template.Rmd` file to the `master` branch of your git repository (you should already be on the `master` branch unless you created new ones)
2. Commit your `PA1_template.md` and `PA1_template.html` files produced by processing your R markdown file with the `knit2html()` function in R (from the **knitr** package)
3. If your document has figures included (it should) then they should have been placed in the `figure/` directory by default (unless you overrode the default). Add and commit the `figure/` directory to your git repository.
4. Push your `master` branch to GitHub.
5. Submit the URL to your GitHub repository for this assignment on the course web site.
In addition to submitting the URL for your GitHub repository, you willneed to submit the 40 character SHA-1 hash (as string of numbers from0-9 and letters from a-f) that identifies the repository commit thatcontains the version of the files you want to submit. You can do thisin GitHub by doing the following:
1. Go into your GitHub repository web page for this assignment
2. Click on the "?? commits" link where ?? is the number of commits you have in the repository. For example, if you made a total of 10 commits to this repository, the link should say "10 commits".
3. You will see a list of commits that you have made to this repository. The most recent commit is at the very top. If this represents the version of the files you want to submit, then just click the "copy to clipboard" button on the right hand side that should appear when you hover over the SHA-1 hash. Paste this SHA-1 hash into the course web site when you submit your assignment. If you don't want to use the most recent commit, then go down and find the commit you want and copy the SHA-1 hash.
A valid submission will look something like (this is just an **example**!)
```rhttps://github.com/rdpeng/RepData_PeerAssessment1
7c376cc5447f11537f8740af8e07d6facc3d9645```

