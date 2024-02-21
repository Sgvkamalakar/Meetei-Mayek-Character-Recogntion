# Hybrid Model CNN+LSTM for Meetei Mayek Character Recognition
This repository contains code for building a hybrid model of Convolutional Neural Network (CNN) and Long Short-Term Memory (LSTM) networks to classify Meetei Mayek (Manipuri) characters.

## Objective
The objective is to leverage the combined power of CNN and LSTM to accurately classify Meetei Mayek characters.

## Why the hybrid model? 
Using a hybrid model, such as the combination of CNN and LSTM, can offer several advantages over using either model individually. Here are some reasons why a hybrid model might be preferred:

- Capture Spatial and Temporal Information: CNNs are well-suited for capturing spatial features in images, while LSTMs excel at capturing temporal dependencies in sequential data. By combining these two architectures, a hybrid model can effectively capture both spatial and temporal information present in the input data. In the context of Meetei Mayek character recognition, the spatial features of the characters (such as strokes and shapes) can be captured by the CNN, while the sequential nature of handwritten strokes can be captured by the LSTM.

- Improved Performance: Combining multiple models often leads to improved performance compared to using individual models alone. Each model brings its strengths to the table, and by leveraging the complementary nature of these models, a hybrid model can achieve higher accuracy and better generalization on the task at hand.

## Getting Started
- To run the code in this repository, ensure you have the necessary libraries installed. You can install them using pip:

```bash
 pip install tensorflow numpy pandas matplotlib seaborn opencv-python tqdm

## Model Architecture
The hybrid model consists of a combination of CNN and LSTM layers. Here's a summary of the model architecture:

```python
model = Sequential()
model.add(TimeDistributed(Conv2D(64,(3,3),activation='relu'),input_shape=(1,30,30,3)))
model.add(TimeDistributed(MaxPooling2D(pool_size=(2,2))))
model.add(TimeDistributed(Conv2D(64,(3,3),activation='relu')))
model.add(TimeDistributed(MaxPooling2D(pool_size=(2,2))))
model.add(TimeDistributed(Conv2D(32,(3,3),activation='relu')))
model.add(TimeDistributed(MaxPooling2D(pool_size=(2,2))))
model.add(TimeDistributed(Flatten()))

model.add(LSTM(100,return_sequences=False))

model.add(Dense(56,activation='softmax'))


## Results
After training the model, you can evaluate its performance using various metrics such as accuracy, loss, and classification report.