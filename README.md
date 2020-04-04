# AlphabetSoupChallenge

AlphabetSoup provides funding to non-profit organizations. In the past, they have contributed funds to 34,299 organizations, representing about $95B. For each donation, they track the success rate and other statistics for each organization. Of the 34,299 donations, the Trustees have chosen wisely 18,261 times in which the recipients have achieved success. However, in 16,038 cases -- representing $60.5B in donations -- they have not met their success criteria. Thus their Accuracy Rate on Successful donations is 53.2%. With such a vast sum of money at stake, even a small improvement in accuracy rate ensure the donations do as much good as possible.  

The AlphabetSoup Director would like to see if the application of Machine Learning or Deep Learning can find patterns in the data to help them improve their 53.2% Accuracy Rate on choosing the correct recipients to a target level of 75% or better. AlphabetSoup has provided a data file for the past recipients and noted if they achieved success, along with other parameters which they felt might be useful as a first pass analysis. 

## Resources 
* charity_data.csv file
* Python ML and Neuro Network environment
* Specifically, Libraries TensorFlow and Scikit-Learn, Pandas

## Approach
The problem is a classic "Binary Classification" problem, in which Applicant Non-Profits need to be separated into Successful and Non-Successful groups represented by the parameter "IS_SUCCESSFUL=1 or 0." 

* The charity_data.csv file was read into a Pandas Dataframe. 
* Preprocessing of the data was performed to analyze its structure, data-types, and category of data to see what might be useful
* Columns of no consequence - like EIN number and NAME of company were eliminated from the dataset. 
* Other columns data was transformed into numerical data suitable to ML and Neuro Networks. 
* The data was scaled to ready it for input to Models.  
* The data was split into Training and Test datasets. 
* As a benchmark for the Deep Learning Network, a RandomForest ML was run to access baseline accuracy. 
* The Loss and Accuracy of the Deep Learning Network model was computed and the model parameters adjusted to try and improve or optimize the accuracy.

## Results

DataFrame Shape: 34,299 Rows X 117 Columns

* Benchmark RandomForest Model achieved an accuracy of 0.699 or 69.9%. 
* This represents quite a significant improvement in AlphabetSoup's current approval process of 53.2% - or a 16.7% improvement.
* This improvement represents an additional 5700 organizations -- or $15.7B - being placed correctly with organization destined for success. 
* 
## Deep Learning Network Baseline Results
* Starting with a Deep Learning Network consisting of:
* Input Nodes = Len(X_train_scaled) = 114
* Hidden Layer1 = 24 nodes
* Hidden Layer2 = 12 nodes
* Output Layer = 1 Node
* Activation = relu on Layer1 and Layer2 with Output set for sigmoid
* loss = binary_crossentropy
* optimizer = adam
* epochs = 50 

Achieved Loss = 0.5611  Accuracy = .7308.  
This improvement in accuracy over the RandomForest ML represents another 1028 Successful organizational donations representing over $1.5B in donations. 

## Optimizing the Results To See If >75% Accuracy Was Achieveable
Various parameters and techniques were tried to improve the overall results: Setting up a duplicate Deep Learning Model code section, parameters were randomly adjusted and results recorded in the code comments and are repeated here for understanding. 

* Input dataset - the dataset was pulled into excel and using the sort function on different colomns, features were searched for those which would have little influence on the output. With a 40/60 split in Is_Successful outcomes, data features which were virtually a single value -- or showed little variation, were eliminated from the dataset to simplify the model's inputs. Starting with elimination of EIN and NAME columns, I also eliminated the Status and Special_Consideration columns which were binary in nature and very imbalanced 99.9% of data in a single state out of two states. Slight improvement in Loss from 0.5611 to 0.5340 and Accuracy 0.7308 to 0.7401 was achieved.  

* Add more neurons to a hidden layer - doubled Layer 1 from 24 to 48 and Layer 2 from 12 - 24. Results got slightly better by a few hundreds lower on loss and a few tenths of a percent on Accuracy.  

* Add additional hidden layers - a 3rd hidden layer of 4 neurons was tried and results worsened by a tenth of a percent. 

* Different activation function for the hidden layers - tried Tanh replacing Relu and tried using Relu in place of Sigmoid. No significant improvements in loss or output accuracy.

* Add additional epochs to the training regimen - increased from 50 to 300. Results got worse by a few tenths of a percent. 

Conclusion: The current model is close to optimizing at 73-74% accuracy. To improve the accuracy further, a statistical sample of say 30 organizations from each Success Outcome group could be pulled and interviews conducted with the intent of looking for additional features which might have influence over outcomes. Both ML and DeepLearning is an iterative process and tight marriage between data collected and data analyzed -- thus an ongoing process to constantly strive to improve the models. 

