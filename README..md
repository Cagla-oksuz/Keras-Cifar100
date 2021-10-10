# Keras-Cifar100

First, I downloaded the dataset with the load_data method, and inserted the necessary variables. Train and test
I created the folders. I created the folders of the classes I need in the ifs and I have 6 folders.

I saved the necessary .pngs with the label control to the folders in the Train folder.

I saved the necessary .pngs with the label control to the folders in the Train folder.

After these processes, there are 500 images in each file in the Train folder and 100 images in the files in my Test folder are ready.
I entered each folder separately and added the number of all the pictures in that folder.

For example, I added 1 to the beginning of all the image names in the tulip folder, 2 to the beginning of the names of the images in the sea folder, and so on. I wrote the label_img function to express which object each of the images is.

The label_img function looks at the first character in the name of the image sent as a parameter and sees the numbers I have added.
It performs the necessary return operation, so I have allocated which picture belongs to which class.

# MODEL

    • 5 convolutions
    • I created it using 3 dense layers.
I chose relu as activation function, but softmax as activation function in last layer
I chose.
Since I have 6 image classes, the output of the last dense layer is determined as 6.

After creating the model, the data in the arrays containing my training and test data should be separated as images and labels. This was done with the help of the Numpy library.

Then I used the fit function to start the training. X with my Train images
I gave the variable Y array where my Train labels are.
I have given my test data as validation as stated in the document. I set it to batch_size and
I set shuffle to TRUE.

30 epoch training was carried out on the network. And as val_acc: 0.7767
calculated.
The plot of graphs was made using the matplotlib.pyplot library.







