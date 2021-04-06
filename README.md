# CNN model for detecting COVID19 
## Mn Classifier repurposed to classify Raman spectra  
This repository copies a model used originally for classifying spectra containing isotope of manganese. Here we used the same model but trained it on Raman spectra taken on 
blood samples from covid-patients (free, confirmed and suspected).
The original report along with the model was published here: https://doi.org/10.1038/s41598-019-38482-1

### 10 fold stratified train-test split
I used a 10-fold startified train-test split method on each training iteration and used the average evaluation accuracy and loss on the test-data as a reference for the perfomance
of each model. One such 10-fold iteration of training and validation was then repeated 10 times to further minimize the effect of stochasticity.

### TransferTraining.ipynb
In this notebook I import the best weights from the original work and employ transfer learning. I test the performance of models, holding 17%, 33%, 50% and 67% of the pre-trained weights fixed while retraining the rest of the weights to fit the data. To mitigate overtraining, early stopping is used. To minimize uncertainty with respect to 
the complexity of the solution-space each model is trained 10 times and the average evaluation accuracy over all attempts is then used as a measure of how well the model can 
be expected to perform.

#### Results of transfer training
Overall, the performance of these models were bad and barely perform better than random guessing.

| # blocks fixed | 17%   | 33%   | 50%   | 63%   |
|----------------|-------|-------|-------|-------|
| Accuracy       | 63.1% | 63.9% | 62.7% | 66.5% |
| Loss           | 56.9% | 58.0% | 60.4% | 57.1% |
