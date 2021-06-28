# Deep_learning_Project

https://jacobgil.github.io/deeplearning/pruning-deep-learning

https://drive.google.com/file/d/1IAW-1liqopJk26gS0EXGKCn2X2irXpLm/view

https://intellabs.github.io/distiller/model_zoo.html#pruning-filters-for-efficient-convnets

https://medium.com/@dkhoche2000/deployment-of-deep-learning-models-on-mobile-and-edge-devices-2763b8d9d3d3

https://atcold.github.io/pytorch-Deep-Learning/
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
We are in the era of deep learning and AI , with this comes the need of having these models in the edge devices , without degrading its originality and accuracy.This can be achieved by deploying it on the cloud and using Application Programming Interfaces(APIs) but this comes with a great cost of security and speed.To do this we develop model which can be deployed on the edge and mobile devices locally without using any external server , as such devices are the ones which are used in the physical machine, it is a great need to have complex models in such devices . With limitations due to 1) Computational power needed for inference.2) Deep Learning models are known for being large in size and computationally expensive which can’t fit into the frugal memory of edge devices.This blog includes the method to overcome such problems and deploy deep learning models on edge and mobile devices which also makes inference faster.So lets get started.

As we know that for deployment we need to reduce the computations and size of the model , we using filter pruning for removing redundant filters .

But with filter pruning we need to keep in mind that we have to reduce filter and parameters without degrading the accuracy of the model.This can be done with unsupervised learning .We will be using clustering algorithms for finding similar filter based on different metrics.After we find the similar filters we will remove the all filters except one which will help in reduction of the flops , parameters and the size of the operation.We can also perform L1 norm and for reduction of parameters and size , but this can reduce the accuracy of the model drastically.We will use Pytorch for our implementation.PyTorch is an open source machine learning library based on the Torch library, used for applications such as computer vision and natural language processing, primarily developed by Facebook’s AI Research lab.
PyTorch
Pushing the state of the art in NLP and Multi-task learning. Using PyTorch's flexibility to efficiently research new…
pytorch.org

We will user cifar 10 dataset with Vgg16 for this post.
CIFAR-10 and CIFAR-100 datasets
aquatic mammals beaver, dolphin, otter, seal, whale fish aquarium fish, flatfish, ray, shark, trout flowers orchids…
www.cs.toronto.edu

We will use spherical KMeans as our clustering algorithm.
Difference between standard and spherical k-means algorithms
begingroup$ The question is: What is the difference between classical k-means and spherical k-means? Classic K-means…
stats.stackexchange.com

After you have trained your model , you need to form clusters with help of Spherical Kmeans.This is the code for Spherical KMeans.
After this you can apply the new configuration to the model , and this will generate a pruned model which needs to be trained and fine tuned again for getting the accuracy.As now we have our fine tuned model we can jump on the deployment part .

For deployment instead of creating the whole app again we have edited the demo app which is made with pytorch mobile .Here is the github repo for the code of pytorch demo app.
pytorch/android-demo-app
HelloWorld is a simple image classification application that demonstrates how to use PyTorch Android API. This…
github.com

Now its time for the results.

Original Cifar 10 model VS Pruned model parameters

Results for cifar 10 and cifar 100
Screenshots of the app : -


Unpruned Model
Conclusion :- Modern CNNs often have large training and inference costs.In thisblog we present a method to prune filters with high similarity coefficient to produce CNNs with reduced computation costs without introducing any loss in the accuracy.It achieves about 79% reduction in parameters for VGG (on CIFAR-10) without significant loss in the original accuracy.We have successfully deployed working model on android device.
We worked in a team for this results.
Team Members :-
Jinu Lilly Joseph
Jagdeesh K
Devdatta Khoche
Parth Deshmukh
NSV Kalyan
Mentor :- Tejalal Choudhary
Thank you!!
