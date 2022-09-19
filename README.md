# Project 1 Report

# New Method Combined with DeepLearning to Improve Performance of Drone Image Reconstruction on 3D Point Clouds
Yifan Wu

## Problem Statement/Applications
It is important nowadays to use 3D construction technique to reshape scanned drone images for either better detecting, testing or developing during engineering domain. The topic is about how to improve the quality and speed when we use innovative methods to construct 3D point clouds. 3D point clouds __[1]__ mean 3D Machine Vision captures an object’s location and shape in a format suitable for processing by a computer or a PAC/PLC.  An object’s surface is represented by a list of three-dimensional coordinates (X, Y, Z), referred to as a “Point Cloud.”

It is useful in terms of using digital simulation to develop system without taking risk of physical destroy or cost in reality. For example, digital twins is one of the application of 3D construction goes for. Convoluted and structural digital twins were used to develop new ideas or fresh-new design in engineering field. Additionally, the self-driving was also one of the application. What’s more, it may be used to detect and construct the 3D environment in space like mars or moon, helping people have a better view of what it look like outside the earth.

When it comes to how to improve the speed and the quality of reconstruction drone image, researchers have come up with many machine learning method combined with other physical approaches to do that. Including *__CNN, SO-Net, EllipsoidNet, pointwise CNN, ECC, PointNet, SGMNet, PAT, Spec-GCN, PointGrid, PointCNN, DGCNN, PCNN, PointConv, A-CNN, Point2Sequence, PointNet++, PointASNL and so on.__* Then they input a large amount of training and test data into those algorithms, comparing the performance of different learning approaches in terms of time consuming, reconstruction quality and loss rate. Set different batch size and training epochs. 

## Current Research

Past research has illustrated that neural networks are able to used to proceed numerous 3D point clouds data to reconstruct simulated environment around us,Point cloud data sets are frequently used in machines to sense the real world because sensors
such as LIDAR are readily available to be used in many applications including autonomous cars and drones. PointNet and PointNet++ are widely used point-wise embedding methods for interpreting Point clouds. However, even for recent models based on PointNet, real-time inference is still challenging. The solution to a faster inference is sampling, where, sampling is a method to reduce the number of points that is computed in the next module. Furthest Point Sampling (FPS) is widely used, but disadvantage is that it is slow and it is difficult to select critical points. In this paper, we introduce Feature-Based Sampling (FBS), a novel sampling method that applies the attention technique. The results show a significant speedup of the training time and inference time while the accuracy is similar to previous methods. Further experiments demonstrate that the proposed method is better suited to preserve critical points or discard unimportant points. <br>

<div align = center>
<img src = "https://user-images.githubusercontent.com/81452190/191117395-2752d837-0626-45cc-88e6-c9621a040288.png" width = "500px"><br>
</div>

__FIGURE 2__. Feature-based Sampling’s Process and Flow Diagram: (a) shows the sampling process of an example point cloud
image. (b) shows the step-by-step process of the feature-based sampling module.<br>
</div>

### GROUPING NEIGHBOUR POINTS
For each i-th point, K neighborhood points are determined. The proposed method utilizes the query ball scheme where
it only collects information from neighbors that are only a certain distance away (inside a certain radius).<br>

<div align = center>
$index_{i} = Q(p_{i},K,P)$<br>
$index_{i}(P) = {p_{i}^{1}\cdots p_{i}^{2}\cdots p_{i}^{k}} $<br>
$index_{i}(K) = {f_{i}^{1}\cdots f_{i}^{2}\cdots f_{i}^{k}} $
</div>
<br>
The Q is the Query ball point algorithm, P is the x-y-z coordinates of the points, and F is the feature of the points.
$index_{i}$ is the index set for the i-th point detemined using the query ball point scheme. $p_{i}$ denotes the center point (centroid)in P. For each centroid $p_{i}$ (dashed line in Fig. 2), the indexi is applied to P and F. The points surrounding the centroid $p_{K}^{i}$(yellow-green (N, k) in Fig. 2), and the features corresponding to the surrounding points are expressed as $f_{i}^{K}$ (orange(N, k) in Fig.2).

### FEATURE EXTRACTION
For each centroid $p_{i}$ (yellow (1, 3) in Fig. 2), geometric information is extracted using the set of K points close to the centroid $p_{i}^{1}\cdots p_{i}^{1}\cdots p_{i}^{K}$ .<br>
<br>
<div align = center>
$e_{i}^{k} = MLP(p_{i}\oplus p_{i}^{k}\oplus(p_{i}-p_{i}^{k}))$
</div>
<br>
$p_{i}$ and $p_{k}^{i}$ consist of x-y-z coordinates, and results are derived through concatenation marked as $\oplus$ . Then using a multi-layer perceptron (MLP) module, the features $e_{k}^{i}$(green in Fig. 2) are determined. This method is similar to the method used in randLA-Net. The difference is that the Query Ball Point scheme is used. The resulting features are used to calculate the score in subsection III-C.

<div align = center>
<img src = "https://user-images.githubusercontent.com/81452190/191131629-4ce6a4cd-05de-4a5b-898b-7b5390fbaff1.png" width = "200px"><img src = "https://user-images.githubusercontent.com/81452190/191131684-bbe41692-607f-4005-adb0-5ba2d9f575a7.png" width = "200px">
</div>
<br>

<div align = center>
  
__FIGURE 3__. Experimental results of training and inference times according to the number of points in ModelNet40.

</div>

<div align = center>
  
__TABLE 1__. Overall accuracy results of the classification task using the ModelNet40 dataset, where ‘‘pnt’’ stands for coordinate of points, ‘‘nor’’ stands for feature of points. #points stands for input number of points. Result of 93.0 is the rounded up value of 92.96.
 
<img src = "https://user-images.githubusercontent.com/81452190/191132537-c0ab279b-a479-4c26-932b-6db52b9dad43.png" width = "300px">
  
</div>
<br>
As shown in Table 1, the overall accuracy of the two best methods using 1k points, PointNet++ and Point-ASNL is 92.9%. Compared to these methods, the overall accuracy of
the proposed method that uses FBS was slightly increased to
92.96%. All methods are run 100 times and the average is
shown. SO-Net is inserted into Table 1 to be a reference of
the accuracy performance. SO-Net uses a lot more points to
solve the classification problem and therefore it is difficult
to compare directly. However, as shown in the table, the
accuracy performance is comparable.<br><br>
Train and Inference Time is determined for different
number of input points (e.g., 512, 1024, and 2048). This
experiment is aimed to compare the performance when the
number of points is increased such that the results can be a
guide for similar tasks or applications that use that number
of points. The performance counter (perf_counter()) from the
Python Time package was used to profile the computational
time. While training time was determined per batch, inference
time was measured in terms of the end-to-end time of the
method. The three methods are run 100 times and the average
time was used for comparison.<br><br>
When compared to PointNet++, the proposed method
completed the task faster for 512, 1024, and 2048 input data
points as shown in Table 3. For both 512 and 1024 points,
our method reduced training time by around 40% and time
was reduced by about 23% for the 2048 points case. The most
time consuming part is the sampling process and the proposed
method in this paper effectively reduces the time to sample
while also determining the points that are important. Furthest
Point Sampling idea, which is used by previous research,
approximates the importance of points using the distance and thus it is not a sampling method that requires learning.
On the other hand, FBS has learning parameters because it
proceeds in the form of calculating and learning the relationship between points. Even though FBS has more learning
parameters than FPS, our method is still faster because of
the reason discussed in Section III. The inference speed is
about three times faster for 512 and 1024 points cases. For
the 2048 points case, the inference time was reduced by
about 21%.


## Current Open-Source Solutions

* Github
* The link in original paper index or appendix 
* kaggle website
<div align = center>
<img src = "https://user-images.githubusercontent.com/81452190/191134111-2989501e-ba00-406f-a60e-b144ffee9b2d.png" width = "600px">
</div>

## Conclusion

the Feature-based Sampling (FBS), a sampling method using the importance sampling idea. FBS is a fast and robust sampling method that uses Positional Encoding and Attention Scoring. Results show that FBS significantly reduces the training time and inference time compared to the PointASNL and PointNet++ methods while achieving comparable accuracy for the classification
task (minimal increase) and part segmentation task (slight decrease). Outlier removal experiment shows that FBS is
better suited to discard outliers (i.e., noise in images) than the Furthest Point Sampling method that is used by PointNet++
and PointASNL. The next step is to apply our sampling method to various other tasks.

## References
[1]https://hermary.com/learning/3d-vision-data-look-like/?gclid=EAIaIQobChMIwonapPaK-gIVAvjICh2yxAKfEAAYAiAAEgIbOPD_BwE<br><br>
[2]F. Chen, Y. Lu, B. Cai and X. Xie, "Multi-Drone Collaborative Trajectory Optimization for Large-Scale Aerial 3D Scanning," 2021 IEEE International Symposium on Mixed and Augmented Reality Adjunct (ISMAR-Adjunct), 2021, pp. 121-126, doi: 10.1109/ISMAR-Adjunct54149.2021.00034.<br><br>
[3]J. -W. Han, D. -J. Synn, T. -H. Kim, H. -C. Chung and J. -K. Kim, "Feature Based Sampling: A Fast and Robust Sampling Method for Tasks Using 3D Point Cloud," in IEEE Access, vol. 10, pp. 58062-58070, 2022, doi: 10.1109/ACCESS.2022.3178519.<br><br>
[4]X. Qu, J. Zhao, Y. Sun and L. Wang, "3D Reconstruction Method Based on Aerial Sequence of UAV," 2020 International Conference on Virtual Reality and Visualization (ICVRV), 2020, pp. 33-37, doi: 10.1109/ICVRV51359.2020.00017.<br><br>
[5]D. Marchisotti and E. Zappa, "Uncertainty mitigation in drone-based 3D scanning of defects in concrete structures," 2022 IEEE International Instrumentation and Measurement Technology Conference, doi: 10.1109/I2MTC48687.2022.9806652.
[6]Y. Chen, S. Liu, X. Shen, and J. Jia, ‘‘Fast point R-CNN,’’ in Proc. IEEE/CVF Int. Conf. Comput. Vis. (ICCV), Oct. 2019, pp. 9775–9784.<br><br>
[7]R. Q. Charles, H. Su, M. Kaichun, and L. J. Guibas, ‘‘PointNet: Deep learning on point sets for 3D classification and segmentation,’’ in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jul. 2017, pp. 652–660.<br><br>
[8]X. Yan, C. Zheng, Z. Li, S. Wang, and S. Cui, ‘‘PointASNL: Robust point clouds processing using nonlocal neural networks with adaptive sampling,’’ in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR),Jun. 2020, pp. 5589–5598.<br><br>
[9]R. Huang, D. Zou, R. Vaughan, and P. Tan. Active image-based modeling with a toy drone. In 2018 IEEE International Conference on Robotics and Automation (ICRA), pp. 6124–6131. IEEE, 2018.<br><br>
[10]C. Szegedy, W. Liu, Y. Jia, P. Sermanet, S. Reed, D. Anguelov, D. Erhan,V. Vanhoucke, and A. Rabinovich, “Going deeper with convolutions,” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun 2015,pp. 1–9.<br><br>
[11]R. Klokov and V. Lempitsky, “Escape from cells: Deep kd-networks for the recognition of 3d point cloud models,” in Proc. IEEE Int. Conf. Comput. Vis. (ICCV), Oct 2017, pp. 863–872.<br><br>
[12]Q. Xu, X. Sun, C.-Y. Wu, P. Wang, and U. Neumann, “Grid-GCN for fast and scalable point cloud learning,” in Proc. IEEE Conf. Comput.Vis. Pattern Recognit. (CVPR), Jun 2020, pp. 5661–5670.
