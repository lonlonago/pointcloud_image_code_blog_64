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

