# RSNA 2021

### How Does AI in Medical Imaging Work? Learn by Creating Your Own Model 

This is a guide for the session "How Does AI in Medical Imaging Work? Learn by Creating Your Own Model" in the *2021 RSNA Annual Meeting*.

### Objective:

By the end of this activity, you will be able to:

* Understand the overall process to train a deep learning model
* Learn basic concepts on how to assess model generalizability and performance


### Acknowledgements

This session used a subset of the 2019 RSNA Intracranial Hemorrhage Dataset. The paper describing the construction of the dataset can be found in this link: [Flanders A.E., Prevedello L.M., Shih G. et al. Construction of a Machine Learning Dataset through Collaboration: The RSNA 2019 Brain CT Hemorrhage Challenge](https://pubs.rsna.org/doi/10.1148/ryai.2020190211)

### Instructors for this session

* Errol Colak, MD
* Felipe C. Kitamura, MD, MSc, PhD
* Luciano M. Prevedello, MD, MPH
* Tara Retson, MD, PhD


### Before we start running our experiments, let's remember an important concept: gradient descent!

![Gradient Descent](https://github.com/kitamura-felipe/RSNASpotlight2021/blob/main/images/graddescent01.gif)

Reference: https://towardsdatascience.com/a-visual-explanation-of-gradient-descent-methods-momentum-adagrad-rmsprop-adam-f898b102325c

The path our algorithm will go through in the loss landscape during the learning process is dependent on several factors. The learning rate is one of them, as well as the order we present our images to the model during the training process. The initial weights of the model determine the starting point in the loss landscape. These are some of the many reasons why the training process can be different if rerun in other machines. It also means you could get different results than the ones shown here if you run these experiments in your computer. 

Although there is this variability in the training phase, after we finish training you should expect to get always the same results for a given test set.

### Instructions:

#### Step 1: Download the [file for Experiment 1 here](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/exp/exp_1.tm?raw=true) and save it somewhere you can find it later.

#### Step 2: Right click on the [Teachable Machine link here](https://teachablemachine.withgoogle.com/train/image) and choose "Open in a new tab" (or hold CTRL key + left mouse click)

You should see this website:

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_1_1.png?)

#### Step 3: Click on the left upper corner to open the menu and then click on "Open project from file" as below:

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_1_2.png?)

#### Step 4: Upload the file from Experiment 1 (Step 1) and wait for it to load.

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_1_3.png?)

You should see multiple head CT images loaded onto the platform organized by presence or absence of hemorrhage:

#### Step 5: Click on "Advanced" and "Under the Hood".

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_1_4.png?)

#### Step 6: Click "Train" and wait for it to finish. It may take a while for the training to start.

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_1_5.png?)


After training, **Experiment 1** should look like this:

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_1_6.png?)

#### Step 7: Click "Calculate Accuracy per class" and "Calculate confusion matrix".

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_1_7.png?)

Notice that the accuracy is not as good as one may expect from a machine learning model. This is due to the limited number of cases in this experiment (30 normal + 30 hemorrhage)

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_1_8.png?)

#### Step 6: Repeat steps 3 to 5, but now load the [file for Experiment 2 here](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/exp/exp_2.tm?raw=true)

After training, **Experiment 2** should look like this:

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_2_1.png?)

Notice that the accuracy seems to have improved significantly. However, a closer look at the confusion matrix shows that all of the positive cases have been misclassified as negative. This is due to the heavy class imbalance thas was simulated in this experiment (1000 normal + 30 hemorrhage).

#### Step 7: Repeat steps 3 to 5, but now load the [file for Experiment 3 here](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/exp/exp_3.tm?raw=true)

After training, **Experiment 3** should look like this:

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_3_1.png?)

Notice that the accuracy is lower than in the last experiment. However, a closer look at the confusion matrix shows that it is indeed correctly classifying most of the positive cases, although still nor perfect. In this experiment our dataset was balanced (1000 normal + 1000 hemorrhage).

#### Step 8: Change the number of Epochs to 75. Click "Model Trained" to retrain the model.

After training, **Experiment 4** should look like this:

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_4_1.png?)

Accuracy appears to be improving for the training set with a greater number of epochs. However, this trend is not observed with the test set. In fact, accuracy in hemorrhage detection has decreased when compared to Experiment 3.
  
  
If we repeat the same exercise with 250 epochs, results would look similar to this: 

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_4_2.png?)



#### Step 9: Repeat steps 3 to 5, but now load the [file for Experiment 5 here](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/exp/exp_5.tm?raw=true)

After training, **Experiment 5** should look like this:

![Screenshot](https://github.com/dila-ai/RSNA_2021_Workshop/blob/main/img/img_5_1.png?)

In this experiment we are able to show that the preprocessing step done to color-code the areas of intracranial hemorrhage, the model is able to achieve a significantly higher accuracy. This color-coding was done programmatically by assigning the red color to voxels that were within a certaing range of Hounsfield Units. Although this simple thresholding rule is not perfectly accurate to identify hemorrhage, it helps the model achieve a better result. More accurate segmentation of hemorrhage could be performed  manually but this is often a labour intensive and time consuming process.
