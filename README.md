# Animal Image Classification: How Much Does Transfer Learning Help?

Can a neural network tell a bear from an elephant, a leopard and a zebra, and what is the *cheapest* way to get it to do so reliably? This project answers that with a sequence of controlled experiments, changing one thing at a time and measuring the effect on validation accuracy.

## The data

1,400 photos in four classes (**bear, elephant, leopard, zebra**), resized to 224 × 224 and split 80 / 20 into 1,120 training and 280 validation images. A fixed random seed makes every experiment repeatable, and each model is trained for 16 epochs.

## The experiments and what they showed

Validation accuracy after the final (16th) epoch:

| # | Experiment | Idea | Validation accuracy |
|---|---|---|---|
| 1 | **Baseline CNN** | A small network trained from scratch: convolutions, batch norm, dropout, max-pooling | 81.4 % |
| 2 | Transfer learning: **AlexNet** | Reuse ImageNet features, train only a new final classifier | 95.4 % |
| 3 | Transfer learning: **VGG16** | A deeper pre-trained backbone | 97.9 % |
| 4 | Transfer learning: **ResNet-18** | Residual connections | **99.3 %** |
| 5 | Transfer learning: **GoogLeNet** | Inception modules | **99.3 %** |
| 6 | Baseline + **data augmentation** | Random horizontal flips and small rotations | 87.5 % |
| 7 | Augmentation + **regularisation** | Extra dropout (0.4 to 0.5) and weight decay | 65.0 % |
| 8 | Different hyperparameters | Padding, dropout rate and extra convolutional layers | 62.9 % |

## Reading the results

- **Pre-trained features are a huge head start.** With about a thousand training images, a network trained from scratch reaches about 81 %, while every pre-trained backbone lands between 95 % and 99 %. Their early layers already detect edges, textures and shapes; only the last layer has to learn which combination means "zebra".
- **Backbone choice matters, but less than using one at all.** The three modern networks (VGG16, ResNet-18, GoogLeNet) are within a few points of each other; ResNet-18 and GoogLeNet reach the best score.
- **Augmentation helps a small model.** Mild flips and rotations lifted the from-scratch baseline from 81 % to 87.5 % without adding any data.
- **More regularisation is not automatically better.** Adding heavy dropout and weight decay on top of the augmented model *lowered* accuracy to 65 %. In a short 16-epoch run the network cannot even fit the training data, so extra regularisation only makes it underfit. Changing several hyperparameters at once (the last row) was the worst of all and made it impossible to say which change hurt, which is why the project varies one factor per experiment.

## What you can take from this

1. With limited data, start from a pre-trained model before designing your own architecture.
2. Change one thing at a time and keep the seed fixed, otherwise you cannot attribute differences to a cause.
3. Regularisation fixes overfitting; if the model is underfitting it makes things worse. Look at the training curves first.
4. Compare every idea with a simple baseline.

## Files

- `Animal_Image_Classification.ipynb`: data pipeline, all experiments, training curves and the written comparison
