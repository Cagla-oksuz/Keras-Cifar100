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

![222](https://user-images.githubusercontent.com/61979226/136682175-d30863e2-7bc9-46b5-9dca-ef504677f30f.png)

        •Training accuracy increased while validation accuracy decreased in some areas.    
        •Validation accuracy encountered but circumvented local minimums.


![111](https://user-images.githubusercontent.com/61979226/136682206-4ec8a38e-9a6a-481a-a4a2-493eb357bc29.png)

        •While the training loss decreased, the validation loss continued to decrease by experiencing increases in some places and the                       difference increased.

# Dropout

Dropout aims to increase the success level of the network by making random cuts between neurons.
On the side is the network structure used by dropouts. 3 dropouts were used in the network.
The first and second dropouts are in the convolution layer and the third dropout is in the dense layer.

The network has been retrained. A 30 epoch training took place. And val_acc is calculated as: 0.7683.

![333](https://user-images.githubusercontent.com/61979226/136682382-c6f3b43d-5ec0-49c1-9d11-df168c503655.png)

        •Both training accuracy and validation accuracy increase, although training accuracy encounters local minimums and maximums, the success of the over    network increases with dropout.

![444](https://user-images.githubusercontent.com/61979226/136682415-9d63d355-bc65-4352-8aee-74b704bcf6b2.png)

        •Training loss and accuracy loss decrease proportionally.

# DATA AUGMENTİON

Image data augmentation is a technique that can be used to artificially expand the size of a training dataset by creating modified versions of images in the dataset.

Rotation_range and width_shift_range are used in this project.
After creating the model and running fit, datagen.fit(X) connects X (train images) to datagen, that is, it performs the operations given as parameters.
Flow takes data and label arrays, and I gave batch_size and ran model.fit_generator.

30. Epoch training was held. And it is calculated as val_acc:7883.

 *rotation_range images are for doing random rotations.
 *width_shift_range implements image scrolling.
 
 
![555](https://user-images.githubusercontent.com/61979226/136682724-a024586f-2098-4804-a141-a69965064bcf.png)

        •Validation accuracy has stutters while training accuracy is less bugged. Many local minimums are observed and the network succeeds.

![666](https://user-images.githubusercontent.com/61979226/136682727-d2e35333-132f-4b64-95b8-54b70875854e.png)

        •Validation accuracy stalls down while training accuracy drops more. Validation accuracy continues to decrease without stuttering, although it increases occasionally




