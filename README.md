# Ely-Sean-Eye-Mouse-Control-CNN
This project was completed by Ely Hahami and Sean Wu in July 2023. The ultimate function of this project it to create a control system in which the user can update the coordinates of their mouse by moving their eyes. For instance, if the user's pupil's look to the right, the user's mouse will adjust the coordinates to the right. This control system has far-ranging applications and has potential to help disabled individuals. By using their eyes to control the mouse, users can overcome physical limitations, enabling them to use technology more easily and independently, ultimately allowing for greater access. 

In terms of technical architecture, this project is done in two main steps: 1) developing prediction models using CNNs and Deep Learning, which was done in Python (Tensorflow/keras API) and 2) via web camera, capturing an image of a user every 0.5 seconds (done in JavaScript), and feeding said image into the model, which updates the mouse's coordinates based on the gaze prediction of the user. 


There exist three seperate models, all trained on thousands of images from diverse subjects via the Columbia Gaze Dataset: 
1) Estimation of head position (-30 degrees, -15 degrees, 0 degrees, +15 degrees, and +30 degrees to represent the user's head titlting far-left, moderately-left, straight, moderately-right, and far-right, respectively) using transfer learning (pre-trained VGG-16 model) and CNN, which achieved 90% validation accuracy;
2) Estimation of vertical gaze position (-10 degrees, 0 degrees, and +10 degrees to represent the user's pupils looking down, straight, and up, respectively), which achieved 89% accuracy;
3) Estimation of horizontal gaze position (-15 degrees, -10 degrees, -5 degrees, 0 degrees, +5 degrees, +10 degrees, and +15 degrees to represent far-left, moderately-left, semi-left, straight, semi-right, moderately right, and far-right horizontal gazes), which again used transfer learning (VGG-16) that achieved ~85% validation accuracy.

For the models, data augmentation, learning rate schedules, and methods to reduce overfitting (Dropout, BatchNormalization, etc.) were employed. For each seperate model, we used the softmax activation function to achieve probability classes for the appropriate number of classes. In the eye-mouse control system, these models were integral for gaze predictions. 
