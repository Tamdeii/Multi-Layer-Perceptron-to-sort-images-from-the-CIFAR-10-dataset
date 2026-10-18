# 🤖 MLP Image Classifier on CIFAR 10

A small deep learning project that sorts tiny colour photos into 10 classes with a Multi Layer Perceptron built in TensorFlow and Keras.

## 📖 About

This is my course project for Foundation of Generative AI (CS 6615, Fall 2026).

The job: take photos from the CIFAR 10 set and predict which class each photo belongs to.

The data: 50,000 photos for training plus 10,000 photos for testing. Every photo is 32 pixels by 32 pixels with 3 colour channels.

The 10 classes:

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

## 🛠 Built With

🐍 Python 3.12

🟢 TensorFlow 2.20 and Keras

🔢 NumPy for number work

📊 Pandas for result tables

📈 Matplotlib for plots

☁️ Google Colab with GPU T4

## 🧱 Model

The network flattens each photo into 3072 numbers, then passes them through dense layers. The last layer returns 10 scores, one per class.

Baseline model:

📌 Input: 32 by 32 by 3 pixels

📌 Flatten: 3072 features

📌 Hidden layer 1: 200 units, ReLU

📌 Hidden layer 2: 150 units, ReLU

📌 Output: 10 units, softmax

📌 Params: about 646 thousand

Training setup:

📌 Optimizer: Adam

📌 Learning rate: 0.0005

📌 Batch size: 32

📌 Epochs: 10

📌 Loss: categorical cross entropy

## 🧪 Results

I trained many versions and kept the test scores here.

📌 Baseline: test 47.95 %, train 50.96 %, 48 s

📌 Narrow net 100 to 50: test 44.73 %, 47 s

📌 Wide net 512 to 256: test 47.44 %, 48 s

📌 One layer 200: test 45.51 %, 45 s

📌 Three layers 512 to 256 to 128: test 47.83 %, 51 s

📌 Leaky ReLU: test 46.36 %, 48 s

📌 Tanh: test 42.26 %, 48 s

## 📊 Progress

Project roadmap:

✅ Step 1: load and check CIFAR 10 data. Done.

✅ Step 2: build baseline MLP. Done.

✅ Step 3: train baseline for 10 epochs. Done.

✅ Step 4: plot train and val curves. Done.

✅ Step 5: run tests on width, depth, and activation. Done.

✅ Step 6: run tests on dropout, L2, learning rate, and batch size. Done.

✅ Step 7: save plots, models, and zip results. Done.

Baseline training journey:

📌 Epoch 5: train 46.48 %, val 44.34 %.

📌 Epoch 7: train 48.67 %, val 46.16 %.

📌 Epoch 10: train 50.96 %, val 47.34 %.

📌 End: test 47.95 %, train loss 1.38, val loss 1.48.

📌 Gap train to val stays near 2 to 4 points, so overfitting stays mild.

📌 All curves and model files sit in the outputs folder and the result zip.

## 🔍 Analysis

Width and depth:

📌 Narrow net 100 to 50 scores lowest at 44.73 %. It lacks power.

📌 Wide net 512 to 256 trains to 52.92 % but tests at 47.44 %. Extra units add noise.

📌 Three layers train best at 53.76 % but the train to val gap jumps to 7.54 points. Depth with no control overfits.

📌 Baseline stays balanced: train 50.96 %, test 47.95 %, gap 3.62 points.

Activation:

📌 ReLU gives 47.95 % and trains fast.

📌 Leaky ReLU trains higher at 52.11 % but tests lower at 46.36 %. It memorizes more.

📌 Tanh falls to 42.26 %. It learns slowly here.

Regularization:

📌 Dropout 0.2 pulls train to 42.53 % and below val at 44.48 %. The net underfits a little but the gap closes.

📌 Dropout 0.5 is too much. Scores fall near 30 %.

📌 L2 with strength zero point zero zero one keeps the gap small near 2 points.

Learning rate:

📌 Rate 0.0001 trains slow and tests at 46.72 %.

📌 Rate 0.0005 is the sweet spot and tests at 47.95 %.

📌 Rate 0.005 breaks training and tests at 35.58 %.

Batch size:

📌 Batch 32 tests at 47.95 % in 48 s.

📌 Batch 128 tests at 47.52 % in 17.6 s. Faster with almost same score.

📌 Batch 512 tests at 47.00 % in 11.9 s. Fastest but a bit lower.

Loss and output:

📌 Softmax plus cross entropy gives 47.95 %. It fits this task best.

📌 Softmax plus MSE trains to 50.36 % but tests at 46.00 %. That loss does not match the task.

## 📈 What I Found

✅ ReLU beats Tanh on this data.

✅ More units do not always mean better scores.

✅ One hidden layer is too shallow here.

✅ Three layers learn the train set well but the gap to val grows.

✅ Dropout and L2 calm overfitting but slow training.

✅ Learning rate 0.005 is too high and the accuracy falls to about 36 %.

✅ Bigger batches train faster. Batch 512 trains in about 12 s.

✅ The plain baseline gives one of the best test scores.

## 🚀 Run It Yourself

1. Open HongTon_MLP.ipynb in Google Colab.
2. Mount Google Drive so the notebook can read and save data.
3. Run all cells from top to bottom.
4. Find the plots and saved models in the outputs folder.

## 📁 Files

📓 HongTon_MLP.ipynb : full code and charts

📝 CIFAR10_MLP_Report_HongTon.docx : written report

🗜 result_HongTon.zip : saved figures and model files

📄 PROJECT_PRESENTATION.md : short project slides in text form

## 🎯 Things I Learned

A Multi Layer Perceptron can sort small photos, but it reads pixels with no sense of shapes or edges. A convolutional net would likely score higher on CIFAR 10. This project taught me how layers, units, activation, dropout, L2, learning rate, and batch size change accuracy and training time in real training runs.

## 👤 Author

HongTon • Foundation of Generative AI • Fall 2026