##  Translation (translated) 

###  1. Theoretical basis 

  Translation is the operation of moving a point a certain distance in a specific direction. Moving the point along the vector direction is obtained by writing this equation in the form of homogeneous coordinates as: where: Therefore, the conversion process to which can be obtained is expressed as:, the transformation matrix is: The matrix is generally called a translation vector. It is easy to verify that the inverse of the translation vector is:  

###  2. Main functions 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550502
 ```  
###  3. Code implementation 

  The translation algorithm uses a single three-dimensional vector to translate all the points/vertices. The code below shows the result of translating the mesh once in the x and y directions. 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550502
 ```  
###  4. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550502
 ```  
![avatar]( 1c510957ac1e4abea08377f533edc627.png) 

[Note]: The GetCenter () algorithm returns the average of the vertices of the triangular mesh. This results in the coordinate system where the origin is at [0, 0, 0], using the get_center returns [0.05167549 0.05167549 0.05167549]. This algorithm has a second parameter relative, which defaults to true. If we set it to false, the center point will be converted to the position specified by the first parameter. 

##  Second, rotation (Rotation) 

###  1. Theoretical basis 

  Rotation depends on the angle of the rotation axis to the rotation axis. First consider a rotation in a plane of the original coordinate system (note: e.g. about the z-axis) if the polar coordinates of the point are:  

The angle of rotation is recorded as, the new position is recorded as, then there is: unfolded, or  

![avatar]( 7bb1f61b66174d18865f607a5e1b08e2.png) 

    Therefore, around separately 

         z 

         , 

         x 

         , 

         y 

        z,x,y 

    The rotation matrix obtained by rotating z, x, y is:  

          R 

          z 

          = 

          R 

          z 

          ( 

          i 

          ) 

          = 

           ( 

                c 

                o 

                s 

                i 

                − 

                s 

                i 

                n 

                i 

               0 

               0 

                s 

                i 

                n 

                i 

                − 

                c 

                o 

                s 

                i 

               0 

               0 

               0 

               0 

               1 

               0 

               0 

               0 

               0 

               1 

           ) 

         R z =R z(θ)=\left( \begin{matrix} cosθ& −sinθ & 0 &0\\ sinθ &-cosθ & 0 &0 \\ 0 & 0 & 1& 0\\ 0 & 0 & 0& 1\\ \end{matrix} \right) 

     Rz=Rz(θ)=⎝

⎛​cosθsinθ00​−sinθ−cosθ00​0010​0001​⎠

⎞​  

          R 

          x 

          = 

          R 

          x 

          ( 

          i 

          ) 

          = 

           ( 

               1 

               0 

               0 

               0 

               0 

                c 

                o 

                s 

                i 

                − 

                s 

                i 

                n 

                i 

               0 

               0 

                s 

                i 

                n 

                i 

                c 

                o 

                s 

                i 

               0 

               0 

               0 

               0 

               1 

           ) 

         R x =R x(θ)=\left( \begin{matrix} 1&0& 0 &0\\ 0 &cosθ & −sinθ &0 \\ 0 & sinθ & cosθ& 0\\ 0 & 0 & 0& 1\\ \end{matrix} \right) 

     Rx = Rx (θ) =

1000 0cosθsinθ0 0−sinθcosθ0 0001

⎞​  

          R 

          y 

          = 

          R 

          y 

          ( 

          i 

          ) 

          = 

           ( 

                c 

                o 

                s 

                i 

               0 

                s 

                i 

                n 

                i 

               0 

               0 

               1 

               0 

               1 

                − 

                s 

                i 

                n 

                i 

               0 

                c 

                o 

                s 

                i 

               0 

               0 

               0 

               0 

               1 

           ) 

         Ry =Ry(θ)=\left( \begin{matrix} cosθ&0& sinθ &0\\ 0 &1 & 0 &1 \\ -sinθ &0 & cosθ& 0\\ 0 & 0 & 0& 1\\ \end{matrix} \right) 

     Ry = Ry (θ) =

cosθ0−sinθ0 0100 sinθ0cosθ0 0101

Note: 

         R 

         y 

        Ry 

    Ry  

         s 

         i 

         n 

         i 

        sinθ 

    Sin theta has the opposite sign because according to the right-hand helix rule  

         x 

         → 

         y 

         → 

         z 

         → 

         x 

        x → y → z → x 

    The order of x → y → z → x. the positive angle of rotation in the above three equations 

         i 

        \theta 

    Theta is all in line with the right-hand helix rule  

         x 

         , 

         y 

         , 

         z 

        x , y , z 

    Rotation by the x, y, and z axes. Use  

         R 

         = 

         R 

         ( 

         i 

         ) 

        R = R (i) 

    R = R (theta) represents any matrix above, then 

         R 

         ( 

         i 

         ) 

        R (i) 

    The inverse of R (theta) is:  

           R 

            − 

            1 

          ( 

          i 

          ) 

          = 

          R 

          ( 

          − 

          i 

          ) 

          = 

           R 

           T 

          ( 

          i 

          ) 

         R ^ {− 1} (i) = R (− i) = R ^ T (i) 

     R − 1 (theta) = R (− theta) = RT (theta) Translation and rotation are rigid body motions that do not change the size and dimensions of the object. 

###  2. Main functions 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550502
 ```  
###  3. Code implementation 

The rotate function implements rotation. Its first parameter is a rotation matrix. Since the rotation of a 3D object can be expressed in the form of multiple parameters, Open3d provides functions that can easily change different parameters into a rotation matrix. 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550502
 ```  
The following code shows the conversion from an Euler angle. For more details, see: Open3D quaternions, Euler angles, rotation vectors to rotation matrices. 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550502
 ```  
  The second argument of the rotate function, center, defaults to True. This means that the object is centered first before being rotated, and then moved to the previous center. If set to False, the geometric image will be rotated directly around the coordinate center. This means that the mesh center can be changed after being rotated. 

###  4. Display of results 

![avatar]( 7a0686b7fde14ac3bfd4845008cc44e2.png) 

##  Scaling (Scale) 

###  1. Theoretical basis 

![avatar]( c5b718d3629846b0a275d35a8cb582a7.png) 

   Scaling can be independently applied to three coordinate axes, such as converting a point to a new point: This results in the corresponding matrix: its inverse is: If the scaling factor is equal, then the scaling change is equal scale, and the object retains the shape but changes the size. Otherwise, it is called non-equal scale when scaling transformation, and the object deforms.  

###  2. Main functions 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550502
 ```  
###  3. Code implementation 

Scale to scale, 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550502
 ```  
  The scale algorithm defaults to the second parameter, center, which is also True. If set to False, the object is not centered before scaling, so that the center of the object can be moved. 

###  4. Display of results 

![avatar]( 5392eb885e5043388bae3d12a62b3042.png) 

##  IV. Transformation matrix (General transformation) 

###  1. The meaning of the transformation matrix 

![avatar]( 2021020521363056.png) 

###  2. Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550502
 ```  
###  3. Display of results 

![avatar]( 124c37fa7758443aa977e47df45f7c58.png) 



--------------------------------------------------------------------------------

##  Voxel 

  Point clouds and triangular meshes are very flexible but irregular geometric types. Voxel meshes are another type of geometry in 3D that is defined on a regular 3D mesh, and voxels can be thought of as 3D counterparts of 2D pixels. VoxelGrid in Open3D, can be used to work with voxel meshes. 

###  1. Main function 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574534461
 ```  
  Implement the creation of a voxel mesh from a point cloud. A voxel is occupied if at least one point of the point cloud is within that voxel. The color of the voxel is the average of all points within the voxel. The parameter voxel_size defines the resolution of the voxel mesh. 

###  2. Read and write voxels 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574534461
 ```  
##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574534461
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574534461
 ```  
![avatar]( e8f3e953f1654e738b803693e19f6dc3.png) 

##  Building voxels from mesh 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574534461
 ```  
##  V. Display of results 

![avatar]( 44716b7957904fa8a5ddc7049f71e263.png) 



--------------------------------------------------------------------------------

##  I. Overview 

  Directly call the color rendering function in Open3D to attach a color to each point in the point cloud according to the ID information of the point cloud, and save the color rendering result to a .pcd file. 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574532707
 ```  
##  III. Display of results 

![avatar]( c0ea0c9c48144396bae9929dd7e9bfef.png) 



--------------------------------------------------------------------------------

##  I. Overview 

  As the title suggests, point clouds are sorted by coordinate size 

##  Point cloud sorting 

The code is sorted from small to large according to the size of the Z coordinate as an example 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574523099
 ```  
##  III. Display of results 

>  It can be seen that the Z coordinates are arranged in ascending order. 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574523099
 ```  


--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

###  1. Implementation process 

![avatar]( 12e210bdb9ff4ecda72586d3cb158722.png) 

###  2. Main functions 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574552831
 ```  
###  3. Algorithm source code 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574552831
 ```  
###  4. References 

>  [1] Low K L. Linear least-squares optimization for point-to-plane icp surface registration[J]. Chapel Hill, University of North Carolina, 2004, 4(10): 1-3 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574552831
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574552831
 ```  


--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

###  1. Nature 

An ideal Poisson disk sampling point set needs to satisfy three conditions: 

  The sampling method that satisfies these three conditions is called maximized Poisson disc sampling. The effect after sampling is good, which can satisfy the uniform data points, retain the details better, and have better blue noise characteristics. The algorithm has a large time complexity 

###  2. Main functions 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550321
 ```  
The function samples points from the grid, where each point is approximately the same distance from its neighbors (blue noise). 

###  3. References 

>  [1] Quan Weize, Guo Jianwei, Zhang Yikuan, Meng Weiliang, Zhang Xiaopeng, Yan Dongming. Maximizing Poisson Disk Sampling Based on Sampling Radius Optimization [J]. China Science: Information Science, 2017, 47 (04): 442-454. [2] Sample Elimination for Generating Poisson Disk Sample Sets, EUROGRAPHICS, 2015. 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574550321
 ```  
##  III. Display of results 

![avatar]( 1737a8cb3459458d805fb8f8319ac19a.png) 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

###   1. Algorithm overview 

  1. CreateFromPointCloudPoisson function implements poisson surface reconstruction. An important parameter of the function is depth. It defines the depth of the octree used for surface reconstruction, so it means the resolution of the resulting triangular mesh. Higher depth values mean meshes with more detail. Note: This algorithm requires PointCloud to have normals.2. Poisson surface reconstruction also builds triangles in low-density areas, and even extrapolates to some areas. CreateFromPointCloudPoisson function's second return value densities, indicating the density of each vertex. Low density values mean that vertices are supported only by a small number of points in the input point cloud. Therefore, low-supported vertices and triangles can be removed using density values. 

###   2. Function analysis 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574577768
 ```  
This function uses the original implementation of Kazhdan in "Kazhdan and Hoppe," Screened Poisson Surface Reconstruction ", 2013." See the implementation details: https://github.com/mkazhdan/PoissonRecon 

###   3. References 

>  [1] Kazhdan M , Bolitho M , Hoppe H . Poisson surface reconstruction. The Japan Institute of Energy, 2013. [2] Poisson surface reconstruction 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574577768
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574577768
 ```  
###   1. Reconstruction results 

![avatar]( 82dced44b864443f8045e5b63d59567c.png) 

###   2. Density rendering 

![avatar]( 876d2d0ea33f47a6b92ad96bfb89d24b.png) 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

###  1. Overview of the principle 

  The singular value decomposition of a quaternion matrix is to decompose a quaternion matrix into the product of three parts, namely: where, is a quaternion matrix, and is two unitary matrices, is a quaternion matrix with real and non-negative elements on the diagonal, and * represents the conjugate of the quaternion. The SVD of a quaternion matrix can be realized by an iterative algorithm. Specifically, the Jacobi iteration method can be used to calculate the singular value decomposition of a quaternion matrix. The Jacobi iteration method is an algorithm that gradually diagonalizes a matrix by rotating the matrix. In the SVD of a quaternion matrix, it is also possible to iteratively rotate the matrix and gradually diagonalize it to obtain, and. It is important to note that the SVD of a quaternion matrix is different from the SVD of a real matrix. In the SVD of a real matrix, sums are both orthogonal matrices, while in the SVD of a quaternion matrix, sums are both quaternion matrices and are not necessarily orthogonal. 

###  2. The implementation process 

The steps of the Q-SVD algorithm are as follows: 

  Although the computational complexity of the Q-SVD algorithm is high, it shows excellent performance in computing the singular value decomposition of quaternion matrices. Therefore, the Q-SVD algorithm has been widely used in computer graphics, computer vision and other fields. 

###  3. References 

>  Xing Yan, Tan Jieqing. Color image decomposition based on singular value decomposition of quaternion matrix [J]. Journal of Engineering Graphics, 2011, 32 (02): 93-101. 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574590686
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574590686
 ```  


--------------------------------------------------------------------------------

##  Radius filtering 

###   1. Main function 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574597317
 ```  
###   2. Algorithm source code 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574597317
 ```  
##  Code implementation 

###   Version 1 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574597317
 ```  
###   Version 2 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574597317
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574597317
 ```  
![avatar]( 02472a0635ac4d85a1bd90c7d745e86c.png) 

##  IV. Python code 

Open3D Radius Filter 



--------------------------------------------------------------------------------

##  First, random sampling 

###   1. Main function 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574528764
 ```  
###   2. Algorithm source code 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574528764
 ```  
##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574528764
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574528764
 ```  
![avatar]( 05ec9b2fce3e458795aaf328afac24f4.png) 

##  IV. Python code 

Open3D random downsampling 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

See: PCL RANSAC Fitting 2D Circles 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574568329
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574568329
 ```  
![avatar]( 2295b98ae237464dbd2fe0124d917f45.png) 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

###  1. Overview 

  The random sample consensus algorithm (RANSAC) is an iterative method for calculating the parameters of a mathematical model from a series of data containing divorced values. The RANSAC algorithm essentially consists of two steps, which are continuously looping: (1) randomly select the minimum number of elements that can form a mathematical model from the input data, and use these elements to calculate the parameters of the corresponding model. The selected number of these elements is the minimum number that can determine the parameters of the model. (2) Check which elements in all the data can conform to the model obtained in the first step. Elements that exceed the error threshold are considered outliers, and elements smaller than the error threshold are considered inliers. This process is repeated many times, and the model with the most points is selected to obtain the final result. 

###  2. Fitting plane 

>  RANSAC is specific to the fitting plane in the spatial point cloud: 1. Three points are randomly selected from the point cloud. 2. These three points form a plane. 3. Calculate the distance from all other points to the plane. If it is less than the threshold T, it is considered to be a point in the same plane. 3. If there are more than n points in the same plane, save the plane and mark all points on this plane as matched. 4. The condition for termination is that the plane found after N iterations is less than n points, or three unmarked points cannot be found. 

###  3. Implementation process 

  At present, the most common and simplest method to fit a plane is least squares fitting, but the accuracy of least squares fitting is easily affected by noise. The random sampling consensus algorithm (RANSAC) can eliminate the influence of noise through iterative fitting, and the fitting accuracy is greatly improved. The random sampling consensus algorithm process is shown in Figure 1:1. From the mathematical knowledge, it is known that at least three points are required to fit the plane, so three points are randomly selected first, and then the plane model parameters are calculated according to the plane equation (1). 2. Use the remaining data points to test the plane model estimated in (1), calculate the result error, and compare the error with the set error threshold. If it is less than the set threshold, determine the point as the inner point, and count the number of inner points under the parameter model and record it. 3. Continue with steps 1 and 2. If the number of inner points of the current model is greater than the maximum number of inner points that have been saved, update the model parameters. The retained model parameters are always the model parameters with the largest number of inner points. 4. Repeat steps 1 to 3 and iterate until the iteration threshold is reached. Find the model parameters with the largest number of inner points. Finally, use the inner points to estimate the model parameters again to obtain the final model parameters. 

![avatar]( 20210516154607138.png) 

###  4. References 

>  [1] Wang Shaochen. Research on the measurement method of workpiece curved surface profile based on point cloud reconstruction technology [D]. Shandong University, 2020. 

##  Second, the main function 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574570500
 ```  
  Use the SegmentPlane function to implement RANSAC splitting the plane from the point cloud. The three parameters required by this function are as follows: 

The function returns (a, b, c, d) as a plane with axis + by + cz + d = 0 for each point (x, y, z) on the plane. The function also returns a list of indices of interior points. 

##  III. Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574570500
 ```  
##  IV. Display of results 

###  1. Primitive point cloud 

![avatar]( ef04938f71434049b8eea5049b0fa274.png) 

###  2. Segmentation results 

![avatar]( eeb2f12f85e4408f83c28a25db6f1a81.png) 

##  V. Related Links 

[1] ransac提取地面（python） [2] 线性拟合笔记之：Ransac算法 [3] RANSAC算法详解(附Python拟合曲线和平面) 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

See: PCL uses RANSAC to fit planes 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574556080
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574556080
 ```  
![avatar]( fdf602493051497b809a7eec650c202b.png) 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

###  1. Overview 

![avatar]( 576501f0438543e3b458b60f8134d5de.png) 

###  2. References 

>  Bao Jianqiang, Zhang Xianzhou, Li Yuan, Xiao Yuanmiao, Chen Xiao, Luo Chao. Application Analysis of Multiple Space Straight Line Fitting Methods [J]. Journal of Surveying and Mapping, 2020, 45 (05): 132-139 + 151. DOI: 10.16251/j.cnki.1009-2307.2020.05.020. 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574567496
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574567496
 ```  
![avatar]( a9822eaf2dd44c41ad8df4c789aacec9.png) 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

###  1. Calculation process 

  Space spherical equation: Formula (1) can be written as: let, then formula (2) is simplified as: write formula (3) in the form of a matrix, as shown in (4): solve the parameters to be obtained, substitute them, to obtain the coordinates of the spherical center of space and the radius of the spherical sphere. 

###  2. References 

>  Wang Hua, Hou Daishuang, Zhang Shuang, Gao Jingang. Spatial straightness detection of train axle [J]. Computer Applications, 2019, 39 (10): 2960-2965. 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574534226
 ```  
##  III. Display of results 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574534226
 ```  
![avatar]( a05e93b469564f49a3623af8895a0015.png) 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

###  1. Implementation process 

![avatar]( 20210323085455478.jpg) 

###  2. Main functions 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574539165
 ```  
###  3. Code analysis 

  Use RANSAC for global registration. In each RANSAC iteration, ransac_n random points are selected from the source point cloud, and their corresponding points in the target point cloud can be detected by querying the nearest neighbors in the 33-dimensional FPFH feature space. The pruning step requires the use of a fast pruning algorithm to weed out false matches early. The 3 pruning algorithms provided by Open3D are defined as follows: 

###  4. References 

>  [1] Choi S , Zhou Q Y , Koltun V . Robust reconstruction of indoor scenes[C]// IEEE Conference on Computer Vision & Pattern Recognition. IEEE, 2015. 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574539165
 ```  
##  III. Display of results 

![avatar]( b68036fcf47d43d189e165b0a250de72.png) 

 The test data used in this paper: Open3D algorithm test data.rar  

##  IV. Python code 

[1] Open3D RANSAC实现点云粗配准 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

RANSAC rough registration using a custom match search method. 

###  1. Main function 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574592930
 ```  
##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574592930
 ```  
##  III. Display of results 

![avatar]( b68036fcf47d43d189e165b0a250de72.png) 

 The test data used in this paper: Open3D algorithm test data.rar  

##  IV. Relevant links 

[1] Open3D RANSAC实现点云粗配准 [2] 



--------------------------------------------------------------------------------

##  First, the principle of the algorithm 

###  1. Effect preview 

![avatar]( 3318ffef963849808a1aa76ad8101dd8.png) 

###  2. Overview of the principle 

  See: pen3D (C++) Ransac Fitting Planar Segmentation Point Cloud 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574537190
 ```  
##  III. Display of results 

###  1. Primitive point cloud 

![avatar]( a0d3153d22e347cb9336d060a2187628.png) 

###  2. Segmentation results 

![avatar]( 28ea674867534e83931aec5bc2329a28.png) 

###  3. Save the results 

![avatar]( 69e6312168bf47b7aa8d3e18a44c8aa0.png) 



--------------------------------------------------------------------------------

##  I. Overview 

   Read the bin point cloud in the Kitti dataset because there is no other bin format point cloud. 

##  Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574541805
 ```  
##  III. Display of results 

![avatar]( 8e16d06e12d94ed89f861efcb460dffc.png) 



--------------------------------------------------------------------------------

