install.package("data.table")
install.package("reshape2")

#load activity labels
activityLabels <- read.table("./UCI HAR Dataset 2/activity_labels.txt")[,2]

#load column names
columNames <- read.table("./UCI HAR Dataset 2/feature.txt")[,2]

#extract mean and standard deviation
extract <- grepl("mean|std", colmNames)

#load X_test and y_test data
X_test <- read.table("./UCI HAR Dataset 2/test/X_text.txt")
y_text <- read.table(".UCI HAR Dataset 2/test/y_test.txt")
subject_test <- read.table("./UCI HAR Dataset 2/test/subject_test.txt")
names(X_test)=columNames

#load activity labels
y_test[,2] = activityLabel[y_test[,1]]
name(y_test) = c("activityID","activityLabel")

testData <- cbind(as.data.table(subject_test),y_test,X_test)

#load X_train and y_train data
X_train <- read.table(".UCI HAR Dataset 2/train/X_train.txt")
y_train <- read.table(".UCI HAR Dataset 2/train/y_train.txt")
subject_train <- read.table(".UCI HAR Dataset 2/train/subject_train.txt")
names(X_train) = colmNames

#extract the mean and std
X_train = X_train[,extract]

#load activity data
y_train[,2] = activity_labels[y_train[,1]]
names(y_train) = c("activityID","activityLabel")
names(subject_train) = "subject"

trainData <-cbind(as.data.table(subject_train),y_train,X_train)

alldata = rbind(test_data,train_data)

idLabels = c("subject","activityID","activityLabel")
dataLabels = setdiff(colnames(data),id_labels)
meltData = melt(data,id = id_labels, measure.vars = dataLabels)

#apply mean to data using dcast function
tidy_data = dcast(melt_data,subject + activityLabel~ variable,mean)


write.table(tidy_data,file="./tidy_data.txt")
