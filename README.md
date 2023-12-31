# Ely-Sean-Eye-Mouse-Control-CNN
Check out this Google Slides Presentation for a user demo & more information: https://docs.google.com/presentation/d/1WNoLTHfMZlPreAAKZQxeCeXQ5fFtg3-y_nkTj3Gb4zE/edit#slide=id.p

This project was completed by Ely Hahami and Sean Wu in July 2023 for the STEMist Hacks summer hackathon. We coded an **eye-mouse control system** that allows a user to move their cursor left, right, up, or down by moving their eyes to the desired position. It also enables them to perform click operations via tilting their head. No hands or wrists are involved whatsoever. 

This control system has far-ranging applications and has potential to help disabled individuals. By using their eyes to control the mouse, users can overcome physical limitations, neurological conditions, arthritis, and other repetitive strain injuries (RSIs) that prevent them from using their hands or wrists, and by extension, prevent them from navigating the web on a computer or laptop. Our control system enables them to use technology more easily and independently, ultimately allowing for greater access. 

In terms of technical architecture, this project is done in two main steps: 
1) we develop three predictive models using CNNs and Deep Learning, which were done in Python, specifically Tensorflow using the Keras API. Each model was trained on thousands of images of ethnically diverse subjects in various head/ eye gaze positions via the Columbia Gaze Dataset, which can be downloaded from the following link: https://www.cs.columbia.edu/CAVE/databases/columbia_gaze/
2) we code a script that via web camera, captures an image of a user every 0.5 seconds, which was originally done in JavaScript and converted to opencv. The script then feeds said image into each of the three models, which updates the mouse's coordinates based on the gaze prediction of the user and performs desired clicks when necessary. 

The 'Head Position Prediction CNN.ipynb' is the Jupyter Notebook file for the CNN (90% validation accuracy) that classifies a user's head position -- whether it is -30 degrees, -15 degrees, 0 degrees, +15 degrees, or +30 degrees, to represent the user's head titlting far-left, moderately-left, straight, moderately-right, and far-right, respectively. 

The 'Vertical Gaze Prediction CNN.ipynb' is the Jupyter Notebook file for the CNN (89% accuracy) that classifies a user's vertical gaze position -- the model first crops the input image to only the user's face (employing Haar Cascades/the Viola-Jones algorithm for object detection) and then estimates whether it is -10 degrees, 0 degrees, or +10 degrees, to represent the user's pupil looking downwards, straight, or upwards, respectively. 

The 'Horizontal Gaze Prediction CNN.ipynb' is the Jupyter Notebook file for the CNN (85% accuracy) that classifies a user's horizontal gaze position --the model first crops the input image to only the user's face (employing Haar Cascades/the Viola-Jones algorithm for object detection) and then estimates whether it is -15 degrees, 0 degrees, or +15 degrees, to represent the user's pupil looking leftwards, straight, or rightwards, respectively. 

Lastly, the 'Eye-Mouse-Control.ipynb' is the Jupyter Notebook file for the UI. Essentially, the code opens a web-camera on the user's laptop that takes an image of the user every 0.5 seconds. Each image is feed into each of the three models defined above, and each model provides a prediction as an output. For instance, a model might output that a user's vertical gaze is 10 degrees and its horizontal gaze is -15 degrees. This indicates a northwest gaze, where the user is looking upwards and leftwards. Then, using Python's pyautogui library, we match the model's predictions to movement of the user's mouse cursor. In the provided example, the mouse will automatically update its position move 200 pixels in the northwest direction in relation to its original position. 

In addition, if the user tilts their head to the left, they may perform a click and if a user tilts their head to the right, they may perform a right click. This adds further functionality for a user to browse the web with their eyes rather than their wrists/hands. 

For an example of a user demonstrating the eye-mouse control system to navigate and 'add to cart' their favorite item on Amazon, please check out slide #4 of the google slides presentation: https://docs.google.com/presentation/d/1WNoLTHfMZlPreAAKZQxeCeXQ5fFtg3-y_nkTj3Gb4zE/edit#slide=id.p. 

The Jupyter Notebook files and the slides presentation contain further details about the three models' architectures, including data pre-processing and implementation details regarding data augmentation, learning rate schedules,  methods to reduce overfitting, the Haar Cascades/the Viola-Jones algorithm for object detection, activation functions to achieve probability classes, etc. 

Note: this project was inspired by the academic journal article "Gaze Estimation using Convolutional Neural Network," which can be downloaded here: https://assets.researchsquare.com/files/rs-2613596/v1/f2a046e4e18f1ad577f705c4.pdf?c=1677233889
