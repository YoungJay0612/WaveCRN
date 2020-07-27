# WaveCRN
WaveCRN: An Efficient Convolutional Recurrent Neural Network for End-to-end Speech Enhancement

## Abstract
Due to the simple design pipeline, end-to-end (E2E) neural models for speech enhancement (SE) have attracted great interest. In order to improve the performance of the E2E model, the locality and temporal sequential properties of speech should be efficiently taken into account when modelling. However, in most current E2E models for SE, these properties are either not fully considered or are too complex to be realized. In this paper, we propose an efficient E2E SE model, termed WaveCRN. Comparing to convolutional neural network (CNN) or long short-term memory (LSTM) based models, in WaveCRN, the speech locality feature is captured by a CNN, while the temporal sequential property of the locality feature is modeled by stacked simple recurrent units (SRU). Unlike a conventional temporal sequential model that models sequence with time consuming LSTM, SRU can be efficiently parallelized in calculation with even fewer model parameters. In addition, in order to more effectively suppress the noise components in the input noisy speech, we derive a novel restricted feature masking (RFM) approach that performs enhancement on the feature maps in the hidden layers; this is different from the approach that applies the estimated ratio mask on the noisy spectral features, which is commonly used in speech separation methods. Experimental results on speech denoising and compressed speech restoration tasks confirm that with the lightweight architecture of SRU and the feature-mapping-based RFM, WaveCRN performs comparably with other up-to-date approaches with notably reduced model complexity and inference time.

## Model Architecture
![image](https://github.com/aleXiehta/WaveCRN/blob/master/images/model.png)
The architecture of the proposed WaveCRN model. For local feature extraction, a 1D CNN maps the noisy audio \textbf{x} into a 2D feature map **F**. Bi-SRU then encodes **F** into an restricted  feature mask (RFM) **M**, which is element-wisely multiplied by **F** to generate a masked feature map **F'**. Finally, a transposed 1D convolution layer recovers the enhanced waveform **y** from **F'**.

## Experimental Results
### Results of Voice Bank + Demand Dataset
<img src="https://github.com/aleXiehta/WaveCRN/blob/master/images/denoise.png" />

