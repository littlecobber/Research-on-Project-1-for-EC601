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
<img src = "https://user-images.githubusercontent.com/81452190/191117395-2752d837-0626-45cc-88e6-c9621a040288.png" width = "600px"><br>
</div>
__FIGURE 2__. Feature-based Sampling’s Process and Flow Diagram: (a) shows the sampling process of an example point cloud image. (b) shows the step-by-step process of the feature-based sampling module.<br>
### GROUPING NEIGHBOUR POINTS
For each i-th point, K neighborhood points are determined. The proposed method utilizes the query ball scheme where
it only collects information from neighbors that are only a certain distance away (inside a certain radius).<br>

### FEATURE EXTRACTION

## Current Open-Source Solutions


## Conclusion

## References
[1]https://hermary.com/learning/3d-vision-data-look-like/?gclid=EAIaIQobChMIwonapPaK-gIVAvjICh2yxAKfEAAYAiAAEgIbOPD_BwE<br><br>
[2]F. Chen, Y. Lu, B. Cai and X. Xie, "Multi-Drone Collaborative Trajectory Optimization for Large-Scale Aerial 3D Scanning," 2021 IEEE International Symposium on Mixed and Augmented Reality Adjunct (ISMAR-Adjunct), 2021, pp. 121-126, doi: 10.1109/ISMAR-Adjunct54149.2021.00034.<br><br>
[3]J. -W. Han, D. -J. Synn, T. -H. Kim, H. -C. Chung and J. -K. Kim, "Feature Based Sampling: A Fast and Robust Sampling Method for Tasks Using 3D Point Cloud," in IEEE Access, vol. 10, pp. 58062-58070, 2022, doi: 10.1109/ACCESS.2022.3178519.<br><br>
[4]X. Qu, J. Zhao, Y. Sun and L. Wang, "3D Reconstruction Method Based on Aerial Sequence of UAV," 2020 International Conference on Virtual Reality and Visualization (ICVRV), 2020, pp. 33-37, doi: 10.1109/ICVRV51359.2020.00017.<br><br>
[5]D. Marchisotti and E. Zappa, "Uncertainty mitigation in drone-based 3D scanning of defects in concrete structures," 2022 IEEE International Instrumentation and Measurement Technology Conference, doi: 10.1109/I2MTC48687.2022.9806652.
[6]Y. Chen, S. Liu, X. Shen, and J. Jia, ‘‘Fast point R-CNN,’’ in Proc. IEEE/CVF Int. Conf. Comput. Vis. (ICCV), Oct. 2019, pp. 9775–9784.<br><br>
[7]R. Q. Charles, H. Su, M. Kaichun, and L. J. Guibas, ‘‘PointNet: Deep learning on point sets for 3D classification and segmentation,’’ in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jul. 2017, pp. 652–660.<br><br>
[8]X. Yan, C. Zheng, Z. Li, S. Wang, and S. Cui, ‘‘PointASNL: Robust point clouds processing using nonlocal neural networks with adaptive sampling,’’ in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR),Jun. 2020, pp. 5589–5598.
