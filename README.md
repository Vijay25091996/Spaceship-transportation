# Spaceship-transportation

A fictional case scenario:
Welcome to the year 2912, where my data science skills are needed to solve a cosmic mystery. We've received a transmission from four lightyears away and things aren't looking good.

The Spaceship Titanic was an interstellar passenger liner launched a month ago. With almost 13,000 passengers on board, the vessel set out on its maiden voyage transporting emigrants from our solar system to three newly habitable exoplanets orbiting nearby stars.

While rounding Alpha Centauri en route to its first destination—the torrid 55 Cancri E—the unwary Spaceship Titanic collided with a spacetime anomaly hidden within a dust cloud. Sadly, it met a similar fate as its namesake from 1000 years before. Though the ship stayed intact, almost half of the passengers were transported to an alternate dimension!

To help rescue crews and retrieve the lost passengers, I'm predicting which passengers were transported by the anomaly using records recovered from the spaceship’s damaged computer system.

The following features with total of 8693 entries were provided in the train.csv i.e training set
 
 #   Columns/Features
 0   PassengerId
 1   HomePlanet
 2   CryoSleep
 3   Destination
 4   Age
 5   VIP             
 6   RoomService     
 7   FoodCourt       
 8   ShoppingMall    
 9   Spa             
10   VRDeck          
11   Transported       


  


 #   Data Cleaning
On generating a heatmap it was clearly visible that 
Features: 'Name','Cabin'  deleted as completely unique values nor numerical nor caetgorical that can be one hot encoded.




And then blindly had a look on how whether any of the feature had any null values

![image](https://user-images.githubusercontent.com/26757681/202535424-da2df66d-f263-4040-9a51-e211dc023d1d.png)

All were roughly around 180-200 nos per feature

I thought of to start cleaning with 'Age' just like "Titanic problem" but the catch observed her is that the box plot variations are overlapped 

Tried all the plots to resolve the nulls but the distribution is so bad that if mean of it is taken and mapped to null it will spoil the model training.

Hence

Applying .dropna() on the training set we get 7620 entries  which is 87 % of the actual old training dataset

 
Then for any dataset to be fed into Machine Learning Model it should be numerised or one hot encoded.

And in this case we have the features 'CryoSleep','VIP','Transported','Destination' & 'HomePlanet' which had string values.



Feature 'CryoSleep' which has 2 categorical entries ('True','False')

Feature 'VIP' which has 2 categorical entries ('True','False')

Feature 'Transported' which has 2 categorical entries ('True','False')

Feature 'Destination' which has 3 categorical entries ('PSO J318.5-22','TRAPPIST-1e','55 Cancri e')

Feature 'HomePlanet' which has 3 categorical entries ('Europa','Earth','Mars')

all of them were one hot encoded with drop_first= True

#   Machine Learning (Training the model)
Imported almost all the popular Classifier Algorithms

test_size was taken as 30%

The accuracy scores were computed as below
![image](https://user-images.githubusercontent.com/26757681/202545316-680520f8-dc44-4e92-9ecf-0b78df395f42.png)
![image](https://user-images.githubusercontent.com/26757681/202545339-6fbd5e86-308e-4cf6-bbc4-6342b63d409d.png)


The top three that is  AB,LGBM & GB were applied on the test dataset and submitted on Kaggle for scores 

GB submission scored slightly better compared to the other two 

Then did Hyper parameter tuning using Grid_Search_CV on GB model then applied it on the test dataset and submitted on Kaggle for scores

  Accuracy_score= 0.79985 
  My best on Kaggle so far and ranking is 728/2295  that is top 31 of the total submissions on kaggle for this competiton.
