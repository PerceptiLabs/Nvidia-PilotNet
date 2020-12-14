[![PerceptiLabs](./pl_logo.png)](https://www.perceptilabs.com/home)

# Nvidia PilotNet
Computer Vision is a key technology for building algorithms to enable self-driving cars. For this model, we've used PerceptiLabs to build Nvidia's end-to-end deep Learning approach to map raw pixels using images captured from front-facing cameras mounted on a car. Each image has a corresponding steering angle associated with it that tells the position of the car's steering for that frame.

For this project, we have used [Udacity’s Car simulator](https://github.com/udacity/self-driving-car-sim) to collect the dataset.

The car captures three pictures - left, center, right - for every single frame using the cameras that are fitted on the front of the car:

![](./carsim2.png)

Each frame has its own steering angle value that will be used as labels.

We've collected and pre-processed (normalized) the training data and have made it available for use with the model. You can download it [here](https://netorgft3205013-my.sharepoint.com/personal/arunesh_m_perceptilabs_com/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Farunesh%5Fm%5Fperceptilabs%5Fcom%2FDocuments%2FPerceptiLabs%20Files%2FNVidia%20Datasets&originalPath=aHR0cHM6Ly9uZXRvcmdmdDMyMDUwMTMtbXkuc2hhcmVwb2ludC5jb20vOmY6L2cvcGVyc29uYWwvYXJ1bmVzaF9tX3BlcmNlcHRpbGFic19jb20vRWo1NlVmbGVXWjVKcXYyRW5kVjFjaTBCOTlIQ2hIWDJXN2FieGd2R3dFa0xqUT9ydGltZT1PaUhHcjhhYjJFZw). 

Happy hacking!

# PilotNet Architecture
The model is based around the *PilotNet* model which is composed of nine layers: 
* Five Convolutional Layers. These layers, which form a [Convolutional neural network (CNN)](https://en.wikipedia.org/wiki/Convolutional_neural_network), play a big part in computer vision, namely in the training of features using images as input.
* Three Dense layers.
* An output layer (implemented as a fully-connected Dense [component](https://www.perceptilabs.com/docs/components) in PerceptiLabs). 

![](./pilotnetarch.png)
Network Layout - Credits: [NVIDIA](https://developer.nvidia.com/blog/deep-learning-self-driving-cars/).

Additionally, we have modified the code in our model's components so that each uses *elu* (not *ReLU*) as an activation function, except for the last Dense component (output node). Finally, for the (regression) training component we've kept the batch size at 100 and the epochs at 20, but have modified its code to use mean squared error (MSE) as the loss function. 

# Structure
This repo has the following structure:
* **/PilotNet_Model**: contains the PerceptiLabs model file (model.json).

# Installation
Follow the steps below to load and prepare the sample model in PerceptiLabs:

1. Download the pre-processed data files from [here](https://netorgft3205013-my.sharepoint.com/personal/arunesh_m_perceptilabs_com/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Farunesh%5Fm%5Fperceptilabs%5Fcom%2FDocuments%2FPerceptiLabs%20Files%2FNVidia%20Datasets&originalPath=aHR0cHM6Ly9uZXRvcmdmdDMyMDUwMTMtbXkuc2hhcmVwb2ludC5jb20vOmY6L2cvcGVyc29uYWwvYXJ1bmVzaF9tX3BlcmNlcHRpbGFic19jb20vRWo1NlVmbGVXWjVKcXYyRW5kVjFjaTBCOTlIQ2hIWDJXN2FieGd2R3dFa0xqUT9ydGltZT1PaUhHcjhhYjJFZw).
2. Clone or download the sample model from GitHub.
3. On PerceptiLabs' Model Hub screen, import the sample model into PerceptiLabs. When prompted for the model's folder, navigate to and select the location of the **model.json** file obtained in the previous step.
4. Open the topmost **Data** component in the model workspace and set its file to **NVIDIA_X.npy** that you downloaded in Step 1.
5. Open the second **Data** component in the model workspace and set its file to **NVIDIA_Y.npy** that you downloaded in Step 1.

Once you have built your model, it should look something like this:

![](./plscreenshot.png)

# Community

Got questions, feedback, or want to join a community of machine learning practitioners working with exciting tools and projects? Check out our [Community page](https://www.perceptilabs.com/community)!

