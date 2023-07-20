## Week 2 quiz - Detection algorithms

1. You are building a 3-class object classification and localization algorithm. The classes are: pedestrian (c1), car (c2), motorcycle (c3). What would be the label for the following image? Recall y=[pc,bx,by,bh,bw,c1,c2,c3]

  > ```y=[1,0.3,0.7,0.3,0.3,0,1,0]```

2. Continuing from the previous problem, what should y be for the image below? Remember that “?” means “don’t care”, which means that the neural network loss function won’t care what the neural network gives for that component of the output. As before, y=[pc,bx,by,bh,bw,c1,c2,c3].

  > ```y=[0,?,?,?,?,?,?,?]```

3. You are working on a factory automation task. Your system will see a can of soft-drink coming down a conveyor belt, and you want it to take a picture and decide whether (i) there is a soft-drink can in the image, and if so (ii) its bounding box. Since the soft-drink can is round, the bounding box is always square, and the soft drink can always appears as the same size in the image. There is at most one soft drink can in each image. Here’re some typical images in your training set: What is the most appropriate set of output units for your neural network?

  >  Logistic unit, bx, by

4. If you build a neural network that inputs a picture of a person’s face and outputs N landmarks on the face (assume the input image always contains exactly one face), how many output units will the network have?

  > 2N
> when building a neual network that inputs a picture of a face and outputs N landmarks, y_hat has shape(2N,1), where shape(output,input).

5. When training one of the object detection systems described in lecture, you need a training set that contains many pictures of the object(s) you wish to detect. However, bounding boxes do not need to be provided in the training set, since the algorithm can learn to detect the objects by itself.

  >  false

6. Suppose you are applying a sliding windows classifier (non-convolutional implementation). Increasing the stride would tend to increase accuracy, but decrease computational cost.

  > false

7. In the YOLO algorithm, at training time, only one cell ---the one containing the center/midpoint of an object--- is responsible for detecting this object.

  > true

8. What is the IoU between these two boxes? The upper-left box is 2x2, and the lower-right box is 2x3. The overlapping region is 1x1.

  >  1/9

> Correct. The left box's area is 4 while the right box 's is 6. Their intersection's area is 1. So their union's area is 4 + 6 - 1 = 9 which leads to an intersection over union of 1/9.

9. Suppose you run non-max suppression on the predicted boxes above. The parameters you use for non-max suppression are that boxes with probability ≤ 0.4 are discarded, and the IoU threshold for deciding if two boxes overlap is 0.5. How many boxes will remain after non-max suppression?

  >  5

> Correct. The bounding box with probability less than 0.4 should be eliminated.

10. Suppose you are using YOLO on a 19x19 grid, on a detection problem with 20 classes, and with 5 anchor boxes. During training, for each image you will need to construct an output volume y as the target value for the neural network; this corresponds to the last layer of the neural network. (y may include some “?”, or “don’t cares”). What is the dimension of this output volume?

  > 19x19x(5x25)

11. if we use anchor boxes in YOLO, we no longer need the coordinates of the bounding box since they are given by the cell position of the grid and the anchor box selection. True/False?
>- False

>  We use the grid and anchor boxes to improve the capabilities of the algorithm to localize and detect objects, for example, two different objects that intersect, but we still use the bounding box coordinates.

12. we are trying to build a system that assigns a value of 1 to each pixel that is of a part of a tumor from a medical taken from a patient. This is a problem of localization? True/False?
> False

> This is a problem of semantic segmentation since we need to classify each pixel from the image.

13. Using the Transpose Convolution. fill in the values of X, Y and Z.
   padding = 1, stride = 2.
Input: 2x2
   [1 ,2 ]
   [3 ,4 ]
Filter: 3x3
   [1 ,0 ,-1 ]
   [1 ,0 ,-1 ]
   [1 ,0 ,-1 ]
Resultes: 6x6
   [  ,  ,  ,  ,  ,  ]
   [  ,0 ,1 ,0 ,-2,  ]
   [  ,0 ,X ,0 , Y,  ]
   [  ,0 ,1 ,0 , Z,  ]
   [  ,0 ,1 ,0 ,-4,  ]
   [  ,  ,  ,  ,  ,  ]

X = 2, Y = -6, Z = -4

14. When using the U-net architecture with an input h × w × c, where c denotes the number of channels, the output will always have the shape h × w. True/False?
>- False
>  The output of the U-Net architecture can be h × w × k where k is the number of classes.
