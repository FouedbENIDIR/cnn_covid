This project aimed to use the public dataset found on this link "https://www.kaggle.com/datasets/maedemaftouni/covid19-ct-scan-lesion-segmentation-dataset" and create a cnn to do segmentation to find lesion in lungs.

A simple model Unet was used. The encoder block got 3 layers (2 conv2D and 1 MaxPooling), and the decoder block got 4 layers (1 conv2D transpose, 1 concatenation and 2 con2D).
The bridge has 2 layers of Conv2D
The output layer is a conv2D

So the pipeline is simple : from the dataset, the images got they masks to see exactly were is the lesion. 
Theire size are 512x512x3. 

Configuration : Due to limited ressources, I used a Batch of 2 images only.

Dataprocessing : I reshape them into 256x256x1 on grey scale, and them I convert them into .npy file in One array before normalised them. 

Data division: 1091 preprocessed images were created for training, 137 for testing.

Results : 

-For training : Accuracy = 0.9909, dice_coef_metric =0.6446, iou_metric = 0.5670, loss = 0.0149, val_Accuracy = 0.9899, val_dice_coef_metric = 0.6242, val_iou_metric = 0.5291, val_loss = 0.0182. Best epoch: 4.

-For test : Loss = 0.0132, Accuracy = 0.9920, IoU = 0.5129, Dice Coefficient = 0.5897

Conclusion : The results show high accuracy but moderate segmentation metrics (Dice and IoU), indicating partial lesion detection. Improvement can be done, such as trying class imbalance-aware losses, a more complex architecture, and enhanced data augmentation/preprocessing.
