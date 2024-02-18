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

