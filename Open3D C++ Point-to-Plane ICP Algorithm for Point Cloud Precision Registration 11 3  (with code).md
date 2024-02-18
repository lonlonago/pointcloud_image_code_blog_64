##  First, the principle of the algorithm 

###  1. Algorithm overview 

>  Point-to-plane metrics are often solved using standard nonlinear least squares methods, such as Levenberg-Marquardt. Each iteration of the point-to-plane ICP algorithm is usually slower than that of the point-to-point algorithm, but the convergence rate is significantly faster. The relative rotation between the two point clouds is less than 30 °. Replace sintheta with theta in the rotation matrix, and replace costheta with 1 to achieve linear approximation of the nonlinear least squares optimization problem, speeding up the calculation. To improve the numerical stability of the calculation, a distance comparable to the size of the rotation angle needs to be used. The simplest approach is to re-scale and move the two input point clouds so that they are bounded within a unit sphere or cube centered on the origin. [1] 

###  2. Point-to-plane ICP precision registration 

![avatar]( 20210516145658292.png) 

   The traditional ICP algorithm adopts minimizing the distance between the corresponding points of the source point cloud and the target point cloud as the registration criterion, as shown in Figure (a). The point-to-plane ICP adopts minimizing the distance from the point in the source point cloud to the plane where the corresponding point in the target point cloud is located as the registration criterion, in which the transformation matrix is represented; the corresponding points in the source point cloud and the target point cloud are represented respectively; and the normal vector of the corresponding points is represented. Its principle is shown in Figure (b). Compared with the traditional ICP algorithm, the point-to-plane ICP can better reflect the spatial structure of the point cloud; can better resist erroneous corresponding point pairs; and has a faster iterative convergence speed.  

>  [2] Linear least squares optimization: pcl :: registration :: TransformationEstimationPointToPlaneLLS 

###  3. References 

>  [1] Low K L. Linear left-squares optimization for point-to-plane icp surface registration [J]. Chapel Hill, University of North Carolina, 2004, 4 (10): 1-3 [2] Efficient variants of the ICP algorithm Canada, 2001, pp.145-152 [3] Li Yuxiang, Guo Jiming, Pan Shangyi, Lu Lili, Lu Zhuxing, Zhang Di. A point cloud registration algorithm based on IS-SHOT features [J]. Surveying and Mapping Bulletin, 2020 (04): 21-26. 

Rusinkiewicz 2001 has shown that the point-to-point ICP algorithm has a faster convergence rate than the point-to-point ICP algorithm. 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574535449
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574535449
 ```  
###  1. Initial position 

![avatar]( abf69e9d88f5411ab3e490d1ee80e3d9.png) 

###  2. Registration results 

![avatar]( 4eb1a797865f4f47a259403d701f1d96.png) 

##  IV. Python code 

Open3D Point-to-Surface ICP Registration Algorithm 

