# A Robust Feature Extraction Pipeline for Detecting Elephant Rumbles 🐘

## About 💬

A sound processing pipeline for accurately detecting elephant rumbles recorded by the ELOC node. For robust feature extraction and noise denoising of the elephant rumbles, a novel approach known as **Wavelet Transform** is used. The proposed research methodology incorporates 4 main modules: 
- **Pre-processing module**
- **Feature extraction module**
- **Feature selection module**
- **Classifier**

The two datasets used by this study is as follows:
- **Dataset-1:** Replayed elephant rumbles and negative dataset captured using Eloc node.
- **Dataset-2:** A collection of originally-recorded elephant rumbles and other non-elephant sounds captured in the same field has used as the positive and negative datasets.

The following figure represents the high-level diagram of the proposed methodology.

![High-Level-Architecture](https://github.com/vinuri-s/A-Robust-Feature-Extraction-Pipeline-for-Detecting-Elephant-Rumbles/blob/main/High%20Level%20Architecture.png?raw=true)

- Initially, an infrasonic sound signal is captured by the two microphones in the ELOC. 
- After capturing the audio signal, it will pass it to the pre-processing module. This module consists of 3 sub-modules; **Butterworth band-pass filter** mitigates the influence of the low-frequency noise and high-frequency noise that exists beyond the typical range of elephant rumbles. **Wavelet-based denoising** further denoise the input signal and **beamforming based stereo to mono conversion**, convert the stereo infrasound recoding into the signal channel while improves the strength of the dominant sound source and reducing the strength of noise coming from the other directions.
- Secondly, the processed signal passes into the feature extraction module. And it consists of 3 sub-modules, and it extracts the **672 features** from the given signal as well as **wavelet based reconstructed variations** of that signal to analyse the signal more precisely. 
- After that, extracted feature vector passes into the feature reduction module which consists of two pre-trained sub-modules. First, sub-module brings the feature vectors into **normalized scale** while minimizing the effects of outliers. Normalized feature vector then passes into second sub-module, and it returns the pre-defined most robust and relevant subset of features from the given feature vector.
- Finally, reduced feature vector passes into the pre-trained classifier. The classifier will determine whether given signal segment consists of infrasonic elephant rumble or not.

## Instructions 💁‍♀️

- <a href="https://github.com/vinuri-s/A-Robust-Feature-Extraction-Pipeline-for-Detecting-Elephant-Rumbles/blob/main/Feature_Extraction_Original_Dataset.ipynb" target="_blank">Feature_Extraction_Original_Dataset.ipynb</a> contains the source code for Complete Feature Extraction Process of the **Dataset 2** from Preprocessing to Feature Extraction.
- <a href="https://github.com/vinuri-s/A-Robust-Feature-Extraction-Pipeline-for-Detecting-Elephant-Rumbles/blob/main/Feature_Extraction_Replayed_Dataset.ipynb" target="_blank">Feature_Extraction_Replayed_Dataset.ipynb</a> contains the source code for Complete Feature Extraction process of the **Dataset 1** from Preprocessing to Feature Extraction. This process includes an additional step called beamformed based stereo to mono conversion, which converts the stereo sounds recorded by the eloc node's two microphones to mono sounds.
(The exported Feature CSV files can be viewed <a href="https://github.com/vinuri-s/A-Robust-Feature-Extraction-Pipeline-for-Detecting-Elephant-Rumbles/tree/main/Features%20CSV" target="_blank">here</a>.)
- The source code and the graph visualizations related to the Quantile Transformation and Feature Selection are available in <a href="https://github.com/vinuri-s/A-Robust-Feature-Extraction-Pipeline-for-Detecting-Elephant-Rumbles/blob/main/Quantile_Transformer.ipynb" target="_blank">Quantile_Transformer.ipynb</a> and <a href="https://github.com/vinuri-s/A-Robust-Feature-Extraction-Pipeline-for-Detecting-Elephant-Rumbles/blob/main/Recursive_Feature_Elimination_(RFECV).ipynb" target="_blank">Recursive Feature Elimination (RFECV).ipynb</a> files.
- <a href="https://github.com/vinuri-s/A-Robust-Feature-Extraction-Pipeline-for-Detecting-Elephant-Rumbles/blob/main/SVM_detailed_analysis_Original_Dataset.ipynb" target="_blank">SVM detailed analysis Original Dataset.ipynb</a> and <a href="https://github.com/vinuri-s/A-Robust-Feature-Extraction-Pipeline-for-Detecting-Elephant-Rumbles/blob/main/SVM_detailed_analysis_Replayed_Dataset.ipynb" target="_blank">SVM detailed analysis Replayed Dataset.ipynb</a> contain the source code for a complete detailed analysis of running Support Vector Machines with different kernels, as well as tuning the various parameters to find the best performing model using the extracted features from both datasets.
- <a href="https://github.com/vinuri-s/A-Robust-Feature-Extraction-Pipeline-for-Detecting-Elephant-Rumbles/blob/main/Binary_Classification_with_SVM_and_REFCV.ipynb" target="_blank">Binary_Classification_with_SVM_and_REFCV.ipynb</a> includes the complete binary classification process with feature selection.
