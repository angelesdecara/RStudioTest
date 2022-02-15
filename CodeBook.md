Using the UCI dataset downloaded from
 https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip  

Firstly, it is downloaded into my ~/Downloads/ folder. There I unzipped on the command line, but alternatively, we could have used unzip() on R.
Features are read into variable feat.

The training data are read separately from the testing data (traindata and testdata, respectively), and using the subject and activity files (read into trainsubj, trainact, testsubj and testact respectively for the training and testing data), we provide names for each individual/subject and for each activity they performed applying colnames.
In that way, the data are more complete, and every row represents one observation. The data are merged with the subject id and the activity id using cbind (trainset and testset for the training data and the testing data, respectively).

The training dataset and the testing dataset can be merged using rbind as they have the same columns (merged into variable mergedsets).

Then, in order, to select the columns with mean and std we used select() and selected the columns with subject and activity ids and those columns that ended with mean() and std(), into variable meansstds.
The activity id was replaced with its description after reading the file with the description into variable activities, grouping the activity ids as a factor (actgroup) which levels are then renamed as the description so that they can then be copied directly.

The description of the variables was added using gsub.

Finally, a tidy dataset called averages was created with the means of each variable after having grouped by subject and activity (variable grouped). 
