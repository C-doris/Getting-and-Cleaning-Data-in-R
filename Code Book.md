Steps for data  data preprocessing and processing in the run_analysis.R script :

1.	Install and Load packages.

2.	Download the dataset: Dataset downloaded and extracted under the folder called UCI HAR Dataset

3.	Assign each data to variables
[1]	features <- features.txt : 561 rows, 2 columns
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
[2]	activities <- activity_labels.txt : 6 rows, 2 columns
List of activities performed when the corresponding measurements were taken and its codes (labels)
[3]	subject_test <- test/subject_test.txt : 2947 rows, 1 column
contains test data of 9/30 volunteer test subjects being observed
[4]	x_test <- test/X_test.txt : 2947 rows, 561 columns
contains recorded features test data
[5]	y_test <- test/y_test.txt : 2947 rows, 1 columns
contains test data of activities’code labels
[6]	subject_train <- test/subject_train.txt : 7352 rows, 1 column
contains train data of 21/30 volunteer subjects being observed
[7]	x_train <- test/X_train.txt : 7352 rows, 561 columns
contains recorded features train data
[8]	y_train <- test/y_train.txt : 7352 rows, 1 columns
contains train data of activities’code labels

4.	Merges the training and the test sets to create one data set
[1]	X (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function
[2]	Y (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function
[3]	Subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function
[4]	Merged_Data (10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function

5.	Extracts only the measurements on the mean and standard deviation for each measurement
[1]	TidyData (10299 rows, 88 columns) is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

6.	Uses descriptive activity names to name the activities in the data set
[1]	Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable

7.	Appropriately labels the data set with descriptive variable names
[1]	code column in TidyData renamed into activities
[2]	All Acc in column’s name replaced by Accelerometer
[3]	All Gyro in column’s name replaced by Gyroscope
[4]	All BodyBody in column’s name replaced by Body
[5]	All Mag in column’s name replaced by Magnitude
[6]	All start with character f in column’s name replaced by Frequency
[7]	All start with character t in column’s name replaced by Time

8.	From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
[1]	FinalData (180 rows, 88 columns) is created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.
[2]	Export FinalData 
