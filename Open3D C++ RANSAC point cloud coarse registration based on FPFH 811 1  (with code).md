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

