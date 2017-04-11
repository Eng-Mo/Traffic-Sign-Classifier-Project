**Traffic Sign Recognition-Project2-Report** 



[//]: # (Image References)

[iSoft1]: ./SoftPredict0.png "ImgSoft0"
[iSoft2]: ./SoftPredict1.png "ImgSoft1"
[iSoft3]: ./SoftPredict2.png "ImgSoft2"
[iSoft4]: ./SoftPredict3.png "ImgSoft3"
[iSoft5]: ./SoftPredict4.png "ImgSoft4"
[iSoft6]: ./SoftPredict5.png "ImgSoft5"
[iSoft7]: ./SoftPredict6.png "ImgSoft6"
[iSoft8]: ./SoftPredict0.png "ImgSoft7"


**Data Set Summary & Exploration**

The follwoing are the data exploration from test.p,train.p data and the number of unique classes were explored from signnames.csv.

* The size of training set is 31367
* The size of the validation set is 7842
* The size of test set is 12630
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43

The images (train,validation,test) samples are presented below and the following chart shows the histogram of each class ID:


![train sample][itrain]

![alt text][ivalidation]

![alt text][itest]

![alt text][iHist] 
[itrain]: ./train.png 
[ivalidation]: ./validation.png 
[itest]: ./test.png 
[iHist]: ./class_histogram_plot.png 

**Design and Test a Model Architecture**

Not many presprocerssing technioque was used as the only prerossessing was normalisation the test, train, valoidation set to reduce computation and big error when adding and multiplying the weights by using the follwing equation (X/122.5)-1 and the result as following:

![alt text][iNorm] 
[iNorm]: ./normtest.png



**Model Architecture**

the Lenet model was chosen to start the experments. this work is adopted code of LeNet Lab That we studied in the class. the model is the same except the batch size changed to 64 for better accuracy after trying 128,256. 
My final model contaion the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
|Input         		    | 32x32x3 RGB image   							| 
|Convolution 5x5x6    	| 1x1 stride, valid padding, outputs 28x28x6 	|
|RELU					| outputs 28x28x6 								|
|Max pooling 28x25x6 	| 2x2 stride,valid padding,output 14x14x6 		|
|Convolution 14x14x16   | 2x2 stride,valid padding,output 10x10x16      |
|RELU                   |                          output 14x14x16      |
|Max pooling 10x10x16   |                          Output = 5x5x16      |
|flatten 5x5x16         |                          Output = 400         |
|Fully connected 400	|                          output =120    		|
|Fully connnected  120  |                          output =84           |
|Fully connnected  84   |                          output =43           |
|Softmax				|                                  43           |


The LeNet model was chosen and the hyperparameters were tuned try and error. the best result calculated using the following parameter values:

* Epoch:10
* Batch_Size=64
* Sigma=.1
* Learning rate= .003

The mjor challenge was the not steady increasing in accuracy as it some point of Epochs can be decreased and the proposed tuning increase regulary except one epoch.Alos by increasing the learning rate to .003 it helped to keep the number of epochs to 10 to not increasse the computations. 
* validation set accuracy of %97
* test set accuracy of %90



**Test a Model on New Images**

Here are five German traffic signs that I found on the web. The following images are the images before and after preprocessing.
![alt text][image1]
![alt text][image2]

No Park sign was tested but excluded  as they are not listed in signname.csv and hence the prediction is totally wrong. Also, the images are collected from web and almost in good condition for predection.


Here are the results of the prediction:

| Image			        |     Prediction	        					     | 
|:---------------------:|:---------------------------------------------:     | 
|Speed limit (30km/h)	               |Speed limit (30km/h)		         | 
|Right-of-way at the next intersection |Right-of-way at the next intersection|
|Stop				                   | No vehicles						 |
|Keep right	      	                   | Keep right	     				     |
|Speed limit (20km/h)		           | Speed limit (20km/h) 			     |
|Ahead only                            |Ahead only                           |
|Speed limit (80km/h)                  |Speed limit (80km/h)                 |

The model was able to correctly guess 4 of the 5 traffic signs with accuracy %85.7 and sometimes can achieve %100 

The Following are the softmax propabilities for each new Images. The vaules shows high accuracy due to the clearness of the new test images as this project didn't considered new images with noise or in bad lighting conditions. 

Here are the results of the prediction:

| Class ID 			                   |  Soft probability| 
|:------------------------------------:|:-----------------| 
|Speed limit (30km/h)	               |%100		      | 
|Right-of-way at the next intersection |%100              |
|Speed limit (20km/h)                  | %81			  |
|Keep right	      	                   |%100     		  |
|Speed limit (20km/h)		           | %100 			  |
|Ahead only                            |%100              |
|Speed limit (80km/h)                  | %99.8            |

![alt text][iSoft1]
![alt text][iSoft2]
![alt text][iSoft3]
![alt text][iSoft4]
![alt text][iSoft5]
![alt text][iSoft6]
![alt text][iSoft7]
![alt text][iSoft8]