# RSNA Bone Age Prediction Challenge
### Objective:
Develop a deep learning model for automated bone age assessment using hand X-ray images.
### Data and Preprocessing:
In the preprocessing stage of our model development, we divided the data into twenty groups based on sex and bone age score. We then randomly sampled 400 data points from each group, resulting in 8,000 data points. These were further divided into a training set of 6,000 and a validation set of 2,000 points. Finally, we determined that an input pixel dimension of 500 x 500 was optimal for this specific problem.
### Model Architecture:
Our model architecture was inspired by the winner of the 2017 RSNA Bone Age Challenge.  This architecture cleverly combines both gender information and the visual data from the X-ray image into a single network.
we use inception v3 architecture for the image data. The layer after the final concatenation layer from the Inception V3 network was extracted and passed through a 2D pooling layer to reduce its dimensionality. After flattening the output from this pooling layer, we concatenate it with the gender information. The gender information itself is provided as a binary input (0 for female, 1 for male) and is processed through a separate dense layer with 32 neurons before this concatenation step.  Following the concatenation, two additional dense layers with 1000 neurons each and ReLU activation are used.  The final layer of the network then predicts the bone age in months.
### Training and Results
The model was trained with a minibatch size of 32 with the ADAM optimizer attempting to minimize the mean absolute error of the output. The best model(model_v2) achieved a MAD of 5.5949 Months on the validation set

