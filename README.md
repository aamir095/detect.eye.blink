# Eye Blinking EEG Signal Analysis Using Brain Computer Interface Devices 

Abstract— In this paper, electroencephalogram signals were acquired and analyzed during different physical activities like rest, anger, and eye blinking. The eye blinking artifact in electroencephalogram signal is studied and analyzed. For this purpose, an Open-Source Brain-Computer Interface device is used for the acquisition of electroencephalogram signals from a single subject (me). The brain waves were acquired at a regular interval, and around 142 instances of eyeblinks were recorded. Eyeblinks preprocessing was done in MATLAB using Butterworth filters. I have developed the algorithm to find the duration of eye blink using MATLAB. Also, I have applied various techniques like Independent Component Analysis (ICA), Machine Learning Algorithm (Random Forest Classifier, Gradient Boosting, Logistic Algorithms) to determine the EEG signals were eyeblink signals or not. Among all the techniques and algorithms, Random Forest Classifier has the highest accuracy.

Keywords— Electroencephalogram (EEG), EEGLAB, MATLAB, Brain Waves, Open Source BCI, ICA, Machine Learning

## Introduction
The human brain is one the most complex system found in our body, and an exacting task to understand the brain, brainwaves. Different techniques have been evolved from past to understand the brainwaves. Among them the most used technique is Electroencephalogram. Both invasive and non-invasive EEG recording have an increasing role in neuroscience and brain computer devices interfaces. The invasive devices should be inserted in brain by surgery while non-invasive devices can be easily fit into the scalp. Using non- invasive devices is a simple and fast process to analyzing the brain activities. However, signal quality from invasive devices is 20 to above 100 times better than the simultaneously obtained from non-invasive devices [1]. While dealing with eye blink and movements EEG signals, the use of non-invasive devices has significant signal quality as compared to the invasive devices. Comparing blink related artifacts in non-invasive and invasive EEG, simultaneously recorded from prefrontal and motor cortical regions using an approach suitable for detection of small artifact contamination. As expected, it is found that blinks to cause pronounced artifacts in non-invasive EEG both above prefrontal and motor cortical regions [1]. In this experiment we have used non-invasive devices from OPENBCI and Emotiv to analyze brainwaves. We are more focused in analyzing brain activities due to eye movements and controlling other devices like RC car, drone using brain waves. 

![five frequency band of EEG signal](https://user-images.githubusercontent.com/48818645/209178340-adfd2930-b1cf-416a-929a-6a87ab23e0a1.PNG)

EEG signal is bio-potential generated from brain activities, represented as voltage (very small in magnitude) fluctuations from ionic movement of neurons within the brain [2]. Depending on brain activities different magnitude and frequency of signals are generated from brain. The amplitude of the EEG signals ranges between 10 - 200 V with a frequency falling in the range 0.5 - 40Hz. EEG waveform is classified into five different frequency bands (alpha, beta, theta, delta, and gamma bands) [3]. Delta (𝛿) waves (0.5 -4Hz) are the slowest EEG waves, normally detected during the deep and unconscious sleep. Theta (Ɵ) waves (4 - 8Hz) are observe- d during some states of sleep and quiet focus. Alpha (α) band (8 - 14Hz) originates during periods of relaxation with eyes closed but still awake. Beta (β) band (14 - 30Hz) originates during normal consciousness and active concern- traction. Finally, Gamma (γ) waves (over 30Hz) are known to have stronger electrical signals in response to visual stimulation. Fig.1 shows the five frequency bands of EEG signal. Different acquisition protocols have been tested for human recognition tasks such as relaxation with eye closed, EEG recordings based on visual stimuli, and performing mental tasks. In this paper we analyze the eye moment activities and corresponding signals generated from the brain. 
The brain-waves signals are extracted, and signal processed from BCI devices. The processed signal is transferred to the computer via Bluetooth, or any medium and feature selection processed of obtained discrete signal is handled with MATLAB. Figure 2 shows the proposed block diagram of the system. The eyeball acts as a dipole with a positive pole oriented anteriorly (cornea) and a negative pole oriented posteriorly (retina) [4]. When the eyeball rotates about its axis, it generates a large amplitude electric signal which is detectable by any electrodes near the eye known as Electrooculogram [5]. Figure 3 shows, when the eyeball rotates closer to FP1 electrode and produces a positive deflection. Similarly, when the eyeball rotates downwards the positive pole (cornea) becomes far away from Fp1 (Closet to the reference electrode) produce negative deflection. This is like what happens when the eye blinks. When the eyelid closes, the Cornea becomes closer to Fp1 and a positive deflection is produced. But when the eyelid opens the cornea rotate away from Fp1 and a negative deflection is produced as shown in figure 3.  
![block diagram of system](https://user-images.githubusercontent.com/48818645/209178696-7f85a4be-e79f-4cae-9732-941d0b9bd647.PNG)
![dipole model of eyeball](https://user-images.githubusercontent.com/48818645/209179395-31efc0b4-5061-41fd-bfb9-4f4720533b25.PNG)


## Proposed System

Any human brain interface system consists of mainly four primary modules: data acquisition, pre-processing, feature extraction and classifier module. The followings are the techniques and methodology used in this research experiment. MATLAB and Python are the tools which were used to analyze and verify the results. Different classifications techniques were implemented in the python to find the accuracy. 

### 1. Data Acquisition
Emotive Headset and OPENBCI headwear is used. Each headset consists of an ear clip with electrodes. Data acquisition is a critical process, and one should acquire data that is free from external and internal artifacts. Bio-potentials collection methods can be classified into three categories: invasive, semi-invasive, and non-invasive [9]. The most invasive technique is called deep brain recording. In this case, a microelectrode is placed inside the skull and signals can be recorded from very well-defined locations. For semi-invasive little to no surgery is required to implant in the desired location. For non-invasive no surgery is required, simply it can be put in the skull readily and fast. The source of bio-potentials (neuron) is far in the case of non-invasive electrodes, this technique is more prone to error and signal loss.

### 2. Signal processing
The raw data from the headset which needs to be further processed. Extracting discriminative characteristics from EEG recordings may be a challenging task, due to the significant presence of artifacts in the acquired data [10]. Different physiologic artifacts like Alternating Current Artifact, Electrode Artifacts, Movements in Recording Environment, Interference of Other equipment, Electrocardiogram (ECG), Skin Artifact are present in the EEG signals [11].

### 3. Feature Extraction
Feature extraction is a process of dimensionality reduction by which an initial set of raw data is reduced to more manageable groups for processing. A characteristic of these large data sets has many variables that require a lot of computing resources to process. The eye blinks were extracted from EEG using the following criterion. Eye blink has the largest amplitude in EEG signal so can be detect easily [11][12]. Also, the amplitude of these peaks will be significantly higher compared to the rhythmic brain activity. An eye-blink signal can be detected by its positive and negative peak occurrences. By examining it was found that the positive peak of eye blink is always greater than 0.3 and the negative one is smaller than -0.3 (after normalization) [11]. The eye blink signals are characterized by high value of kurtosis coefficient, normally above the value 3 [11][13]. MATLAB was used to detect the peak and to analyze and determine whether the signal is eye blink or not. Only useful data was analyzed and passed into different techniques like Independent Component Analysis (ICA) and Machine Learning Algorithms to determine the signal a blink or not.

### 3. Classification
The design of classifier is a hot topic in EEG data processing and applications. Traditional methods for EEG classifier design face the challenge caused by high dimension of EEG data sets, thus the classification result may have large deviations. Small sample size problem of EEG could lead to the overfitting phenomenon, which limits the application of traditional classifier. In this research, I have applied different binary classifications like Random Forest Classifier, Gradient Boosting, and Logistic Algorithms to determine whether the EEG signal is associated with eye blink or not. The detailed explanation of these techniques is discussed in the following sections.

## Experiment Setup and Results
EEG signals were extracted from the brain using BCI devices and transferred to the computer using Bluetooth. All the filtering, noise removal was carried out using MATLAB, ICA component analysis using BCILAB, a MATLAB module for EEG signal processing, and Machine Learning Algorithms was implemented using python programming language.
The OPEN BCI headband device was used to record 142 occurrences of eyeblink instances from a single individual (Male, 27 Years Old). With the use of a timer, the individual was instructed to blink every 2.5 seconds, and many trial were performed to collect data. The raw signals were treated with the butterworth filter. The high frequency signals were removed using the filter since eyeblink signals are low frequency signals (less than 30 HZ) [14]. Different techniques for identifying eyeblink, such as the base value method, ICA, and Machine Learning algorithms, were used after the filtered signals were normalized within range of [-1, +1]. The methods are described in detail further down.

### 1. Normalization and Base Value Method
Eyeblink signals are characterized by high amplitude compared to the rest of the signals [11] [12] [13]. EEG signals are normalized in the range of [+1,-1]. After normalization, the base value of ±0.3 and ±0.4 v is considered as eye blink and the accuracy of the system is found considering each base value. Those signals which have a base value greater than +0.3, +0.4 and less than -0.3, -0.4 are considered as eye blink. All these normalizations, and identification was done in MATLAB. Eyeblink were recorded every 2.5 seconds. Actual class were calculated based on that time.
The confusion matrix for both thresholds as described below.

![confusion matrix](https://user-images.githubusercontent.com/48818645/209185852-f38cdac8-ce5f-46cb-83c9-7a52234ef8f6.PNG)

### 2. Independent Component Analysis

The algorithm was implemented in the MATLAB programming language with the addition of a FastICA toolbox from EEGLAB [14] provided by the EEGLAB Organization at the University of California, San Diego. Some of the functions of the FastICA toolbox [15] were removed or modified to decrease the computation time. In addition, default parameters for non-linearity, orthogonalization, stopping criteria, kurtosis were changed to suit the application and improve the performance of the algorithm. The goal was to produce a fast algorithm by having a computation time shorter than the time length of the signal imported. A GUI was created to make a “user-friendly” interface for a more effective demonstration of the algorithm and results. The complete process of the algorithm is described in the following diagram. ICA is commonly to remove eye blink artifacts from the EEG signals. I have used the same technique to find the instances ICA considered the signal as an eyeblink. the predefined function runica in the EEGLAB to remove the eye blinking artifacts in the EEEG data.

![ICA](https://user-images.githubusercontent.com/48818645/209186678-75003bdf-a759-48a1-93ba-c4b3774f2eb8.PNG)

The overall accuracy of the algorithm was 0.405.


### 3. Machine Learning Algorithms
The sample rate of the OPENBCI hardware is 200 HZ. Every 5 millisecond the EEG signal voltage is recorded by the hardware. Suppose 30 seconds of EEG signal is recorded while making an eyeblink every 2.5 seconds. 
Total samples in 30 seconds = 30*200 = 6000 samples
Average time of eyeblink = 0.15 seconds 
Number of samples in an eyeblink = 0.15*200 = 30 samples
Number of eye blink in 30 seconds = 30/2.5 = 12 times
Total samples for 12 eyeblinks = 12*30 = 360 samples

For ML models, the learning data is obtained by labeling the corresponding 30 samples of data every 2.5 seconds as 1.
The eyeblink is represented by this label. For non-eyeblink, the remaining corresponding samples column are set to 0. Now we have three columns of data sets: the first column contains data samples from hardware, the second column contains the eyeblink label (generated by the user), and the third column contains the timestamp. Once the ML model has been trained with these learning datasets, the new dataset can be used to predict whether or not the signal is an eyeblink.Output set is defined in which the eye blink events are marked as ‘1’ and non-eye blink events as ‘0’. The processed EEG signal with the labels was passed into the ML algorithms to predict whether the signal is an eyeblink or not. Let’s consider the target Y (blink or no-blink) best on the given input X (spike in the voltage signal). Since this is a classification task that has only 2 outputs: 0 for no blink and 1 for blink. Some of the most common machine learning algorithms are implemented as follows.

#### I.	 Random Forest Classifier
RFC classifier is based on the classic technique of the decision tree. Since this task is a binary classification, decision trees are supposed to be yield better results [16]. RFC is an ensembling learning method for classification and regression which operates by creating multiple forests of decision trees at training time. Many parameters were tuned to increase the accuracy of the model and max_depth of 9 which is the maximum depth of a tree was implemented. Several criteria like gini, entropy was changed, however, it did not impact the results.
The final accuracy of the model was 0.681.

#### II.	Gradient Boosting
Gradient Boosting utilizes the concept of boosting. In this approach, the algorithm tries to boost the weak classifier and when the weak classifier gets combined with the best classifier it minimizes the overall prediction error [17]. N_estimators of 100 were implemented which indicates the number of boosting stages to perform. Similarly, a learning rate of 1 is the rate at which the contribution of each tree gets shrank. Similarly, max_depth of 1 was the most effective in our model. Max_depth limits the number of nodes of each tree. Usually boosting approach yields better results, however, in this case, the accuracy was 0.665 which is even lower than RFC.

#### III.	Logistic Regression
The logistic regression with normalization to reduce the overfitting of the algorithms was implemented but l1 and l2 normalization had little to no impact on our final accuracy.
The predicted accuracy of the model was 0.662.

![ima](https://user-images.githubusercontent.com/48818645/209189024-28c6c27e-417c-4980-9582-01bfacf0b9e2.PNG)

## Conclusion and Future Directions

Basic threshold, ICA, and Machine Learning Algorithms were implemented to determine the EEG signal is an eyeblink or not. Basic threshold, ICA has low accuracy as compared to ML algorithms. Basic Logistic algorithms were tested. The advanced decision tree-based algorithm such as RFC and GB were implemented, however, these two algorithms were not able to yield a significant increase in accuracy in comparison to logistic regression. This can be down to the fact that our data sets are severally limited in terms of features which is making it hard for ML algorithms to generalize well with data sets. In this project, we have a limited number of electrodes. However, if we use EEG channels of 64 or 128 (number of electrodes) then we have multiple features making Machine Learning Algorithms have high accuracies. 

EEG signal processing and application are applied to more and more fields. In this paper, I have highlighted the following perspectives. (1) EEG signal acquisition methods using different electrodes with their characteristics. (2) Some noise, artifacts are highlighted and their removal from signals are discussed. In fact, I have presented many ways to remove noise and artifacts in an EEG signal in an efficient way. (3) Eye blinking effect on EEG signals is discussed and a promising way to detect eye blinking signals is applied. I have placed an emphasis on the detection of eye blinking signals using different techniques and algorithms. In summary, the study on Brain Signals is still in its infancy. Through various research has been done in this area but much more to achieve. There is always space for better development of products and the use of algorithms.Brain-Computer Interface should not only be limited to analysis of brain activities rather BCI devices must be sophisticated to find the cure of mental diseases. There should be works done in the field of translating neural signals to text using a Brain-Computer Interface. Brain waves also can be used as a secure identification tool in this digital world. However, with every innovation there comes the risk. BCI hardware and software are subjected to risk; anyone can get in this system and simulate the brain, get unauthorized data. Also, invasive BCIs are risky since it requires neurosurgery. 

### Appendix

https://github.com/aamir095/eyeblink_dataset

BCI hardware is used to get raw data from a person. With the help of Bluetooth, data can be transferred to a computer for further processing.

![BCI device](https://user-images.githubusercontent.com/48818645/209194051-af8a8504-6ebb-4ad2-9894-d6ed4874b5d8.PNG)

The raw data from the hardware has 15 columns. There are 4 electrode channels, 4 accelerometer data,s.n, and timestamp. The data of interest is channel 0 data and eye blink is determined with the help of that.

![raw data from openbci](https://user-images.githubusercontent.com/48818645/209194629-9ec7678b-5016-4056-ac8e-bbc9982a6827.PNG)

EXG channel 0 data is selected. The raw data is filtered with a series of 2 filters. The bandpass frequency is 5-50HZ. The notch filter (bandstop) frequency is 50-60 HZ.



![raw and filtered data](https://user-images.githubusercontent.com/48818645/209195515-deb2429a-9800-4ba6-a22f-f1a1e1b4df63.PNG)

The filtered data is normalized from [-1, +1] with zero mean. A signal greater than +0.4 and less than -0.4 is considered as an eye blink.


![zero mean and comparison](https://user-images.githubusercontent.com/48818645/209196226-fa3c2132-70e3-4295-90c5-e37fc72d5358.PNG)


Detecting a number of eye-blinking instances in a given data set.

![eyeblink detection](https://user-images.githubusercontent.com/48818645/209196733-8960bf38-5582-4b36-bdb7-d40e6016221d.PNG)


