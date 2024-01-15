Meliha Çağla Kara
040180014
15.01.2024

Video: https://youtu.be/GwXWSbKewI0

# Data Collection

I decided to do my own data collection and prepared a setup like this:

![image](https://github.com/chayoung0/artificial-neural-networks-final/assets/79144571/ff7c6fe9-f2f1-4342-89c1-c360758f2193)


The coin is dropped towards a mat from a height of 1 meter.

Before releasing the coin, I consistently held it in the same manner. That is, with the head facing away from me, and my fingers in the same count and positions.

I thought I needed more input features, so I decided to add the angle. I positioned myself around the mat with varying angles from 0 to 180 degrees. Where I released the coin really affects the landing position. Once again, I held it consistently with the head facing away from me with 2 fingers.

To increase the inputs, I also considered starting with a three-finger grip, but I abandoned the idea as I was already tired from 150 squats.

I recorded landing orientations as well as position with respect to the center of the mat. The coin generally falls close to the center, but there are instances where it deviates significantly. It can be seen in the scatter plot below. 

![Pasted image 20240115171710](https://github.com/chayoung0/artificial-neural-networks-final/assets/79144571/b882f75c-f5fb-4f3c-ad6d-547ffa755b7f)


Then transferred the data to Excel and then converted it to CSV.

# Preprocessing

As for preprocessing step, I used `OneHotEncoder()` for tranforming categorical data. It is the best way to differentiate heads, tails and vertical.

For numerical data, I simply used `StandardScaler()`.

# Architecture Selection

  
The model architecture was quite confusing. However, in the end, I decided to use two separate models for landing orientation and landing position. I couldn't successfully develop a model that would output both for them simultaneously, and I'm not entirely sure if it's a good idea in general.

For landing orientation, I used a binary classifier as requested. For landing position, I used a multiple-output regressor because it has two coordinate outputs, namely x and y.

# Evaluation and Discussion

For the evaluation, landing orientation is coming out with approximately 50% accuracy, which is just an ordinary probability expected from a coin. Instead of exact positions for landing, I conducted an examination based on distances. Trying to predict the actual position seemed a bit... impossible. The model has about %75 accuracy at predicting the landing distance.

# Challenges

- Tensorflow is not compatible with python 3.12, so I had to downgrade my python version. But I didn't even use tensorflow at the end.
- Excel uses semicolon as seperator in csv files, anyway.
- Vs Code gets buggy if you don't type a commit message.
- Made a lot of mistakes while calculating accuracy.
