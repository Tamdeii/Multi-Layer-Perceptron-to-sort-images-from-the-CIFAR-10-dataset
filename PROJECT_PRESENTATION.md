# 🤖 MLP Project

## 📖 About This Project

This project is a course assignment for Foundation of Generative AI. The task is to build a Multi Layer Perceptron to sort images from the CIFAR 10 dataset into ten classes.

The dataset has sixty thousand colour photos. Each photo is 32 pixels by 32 pixels with three colour channels.

The ten classes are:

🛫 airplane
🚗 automobile
🐦 bird
🐱 cat
🦌 deer
🐶 dog
🐸 frog
🐴 horse
🚢 ship
🚛 truck

## 🛠 Tech Stack

🐍 Python 3.12

🟢 TensorFlow 2.20 with Keras

🔢 NumPy for array math

📊 Pandas for tables

📈 Matplotlib for charts

☁️ Google Colab with GPU T4

## 🧱 Model Design

The network reads a photo, flattens it into one long list of 3072 numbers, then sends it through dense layers. The last layer gives ten scores, one for each class.

Baseline setup:

Input layer: 32 by 32 by 3 pixels

Flatten layer: 3072 features

Hidden layer one: 200 neurons with ReLU

Hidden layer two: 150 neurons with ReLU

Output layer: 10 neurons with softmax

Total parameters: 646 thousand

Training settings:

Optimizer: Adam

Learning rate: zero point zero zero zero five

Batch size: 32

Epochs: 10

Loss: categorical cross entropy

## 🧪 Experiments

We changed one thing at a time to see the effect.

Baseline: test accuracy 47.95 percent, 48 seconds

Narrow net 100 to 50: test accuracy 44.73 percent, 47 seconds

Wide net 512 to 256: test accuracy 47.44 percent, 48 seconds

One layer 200: test accuracy 45.51 percent, 45 seconds

Three layers 512 to 256 to 128: test accuracy 47.83 percent, 51 seconds

Leaky ReLU: test accuracy 46.36 percent, 48 seconds

Tanh: test accuracy 42.26 percent, 48 seconds

## 📈 Main Findings

ReLU works better than Tanh for this task.

Adding more neurons does not always improve accuracy.

One hidden layer is not enough for good results.

Three layers can overfit more than two layers.

Dropout slows training but helps the model generalize.

A learning rate of 0.005 is too high and breaks training.

Smaller batches train faster but show more noise.

The best simple result came from the baseline setup.

## 🚀 How to Run

Step one: open HongTon_MLP.ipynb in Google Colab.

Step two: mount Google Drive so the notebook can load data.

Step three: run every cell in order.

Step four: open the outputs folder to see graphs and saved models.

## 📁 Project Files

HongTon_MLP.ipynb : main code notebook

CIFAR10_MLP_Report_HongTon.docx : full written report

result_HongTon.zip : charts and model weights

## 🎯 What I Learned

A Multi Layer Perceptron can classify small images but it is not the best tool for photos. Convolutional networks would likely give higher accuracy on CIFAR 10. This assignment taught me how to tune layers, neurons, activation, and regularization in a real deep learning workflow.