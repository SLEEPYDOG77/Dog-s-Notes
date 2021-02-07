# Chapter12: Cramer's rule

> Jerry: Ah, you're crazy! 
>
> Kramer: Am I? Or am I so sane that you just blew your mind? 
>
> Jerry: It's impossible!
>
> Kramer: Is it?! Or is it so possible your head is spinning like a top? 
>
> Jerry: 天哪，你真是疯了！
>
> Kramer：真的吗？或者也许，我是理智的，而你的脑子已经乱得快爆炸了？
>
> Jerry：这不可能！
>
> Kramer：哦真的吗？或者也许是你晕乎乎得正像陀螺一样旋转呢？



[TOC]

> In the previous video, I've talked about linear systems of equations, and I sort of brushed aside the discussion of actually computing solutions to these systems. 
>
> And while it's true that number-crunching is typically something we leave to the computers, digging into some of these computational methods is a good litmus test  for whether or note you actually understand what's going on, since that's really where the rubber meets the road. 
>
> Here I want to describe the geometry behind a certain method for computing solutions to these systems, known as Cramer's rule. 

<img src="12-1.jpg" />



#### Prerequisites

> - Determinant
> - Dot products Duality
> - Inverse matrices, rank and null space



> This **Cramer's rule** is not actually the best way for computing solutions to linear systems of equations. 
>
> **Gaussian elimination（高斯消元法）**, for example, will always be faster. 



###### Why learn it? 

> Think of this as a sort of cultural excursion. 
>
> It's a helpful exercise in deepening your knowledge of the theory behind these systems. 
>
> Wrapping your mind around this concept is gonna help consolidate ideas from linear algebra, like the determinant and linear systems, by seeing how they relate to each other. 
>
> Also, from a purely artistic standpoint, the ultimate result is just really pretty to think about, way more so that Gaussian elimination. 



#### Cramer's rule

> So the setup here will be some linear system of equations, say with two unknowns, x and y, and two equations. 
>
> In principle, everything we're talking about will also **work for systems with a larger number of unknowns, and the same number of equations.**

<img src="12-2.jpg" />

> But for simplicity, a smaller example is just nicer to hold in our heads. 



<img src="12-3.jpg" />

> You can think of this setup geometrically as a certain known matrix transforming an unknown vector, [x, y], where you know what the output is going to be, in this case [-4, -2]. 

<img src="12-4.jpg" />

> So what we have is a sort of puzzle, which input vector [x, y], is going to land on this output [-4, -2]? 



> One way to think about our little puzzle here is that we know the given output vector is some linear combination of the columns of the matrix, but we want is to figure out what exactly that linear combination should be. 

<img src="12-5.jpg" />

> Remember, the type of answer you get here can depend on whether or not the transformation squishes all of space into a lower dimension. 
>
> That is if it has zero determinant. 
>
> In that case, either none of the inputs land on our given output or there's a whole bunch of inputs landing on that output. 

<img src="12-6.jpg" />

<img src="12-7.jpg" />

> But for this video we'll limit our view to the case of a non-zero determinant, meaning the outputs of this transformation still span the full n-dimensional space that it started in. 
>
> every input lands on one and only one output, and every output has one and only one input. 

<img src="12-8.jpg" />



#### What's next is wrong, but helpful

<img src="12-9.jpg" />

> So maybe you hope that after the transformation, the dot products with the transformed version of the mystery vector with the transformed versions of the basis vectors will also be these coordinates x and y. 
>
> That'd be fantastic because we know what the transformed versions of each of these vectors are. 

<img src="12-10.jpg" />

> But it's not at all true.

<img src="12-11.jpg" />

> For most linear transformations, the dot product before and after the transformation will be very different. 

###### For example

<img src="12-12.jpg" />

<img src="12-13.jpg" />

> or

<img src="12-14.jpg" />

<img src="12-15.jpg" />

> And, looking at the example I just show, dot products certainly aren't preserved. 
>
> They tend to get bigger since most vectors are getting stretched out. 



#### Orthonormal Transformation（正交变换）

> In fact, transformations which do preserve dot products are special enough to have their own name - **Orthonormal Transformations.**

<img src="12-16.jpg" />

> These are the ones that leave all the basis vectors perpendicular to each other and still with unit lengths. 
>
> You often think of these as rotation matrices. 
>
> They correspond to rigid motion, with no stretching, squishing or morphing. 

<img src="12-17.jpg" />



#### Right way

>  Solving a linear system with an orthonormal matrix is actually super easy: Because dot products are preserved, taking the dot product between the output vector and all the columns of your matrix will be the same as taking the dot products between the mystery input vector and all the basis vectors, which is the same as just finding the coordinates of that mystery input. 

<img src="12-18.jpg" />

<img src="12-19.jpg" />

> So, in that very special case, x would be the dot product of the first column with the output vector, and y would be the dot product of the second column with the output vector. 

<img src="12-20.jpg" />



###### Two dimensional

> Why am I bringing this up when this idea breaks down for almost all linear systems, well, it points us in the direction of something to look for: 
>
> Is there an alternate geometric understanding for the coordinates of our input vector that remains unchanged after the transformation? 

> If your mind has been mulling over determinants, you might think of the following clever idea: 
>
> Take the parallelogram defined by the first basis vector, `i-hat` , and the mystery input vector [x; y]. 

<img src="12-21.jpg" />

> The area of this parallelogram is the base, 1, times the height perpendicular to that base, which is the y-coordinate of that input vector. 
>
> So, the area of that parallelogram is a sort of a screwy roundabout way to describe the vector's y-coordinate; 

<img src="12-22.jpg" />



> And symmetrically, if you look at the parallelogram spanned by our mystery input vector and the second basis, `j-hat`, its area is gonna be the x-coordinate of that mystery vector. 

<img src="12-23.jpg" />



###### Three dimensional

> Consider the parallelepiped it creates with the other two basis vectors, `i-hat` and `j-hat`. 

<img src="12-24.jpg" />

> If you think of the square  with area 1 spanned by `i-hat` as the base of this whole shape, then it's volume is the same as its height, which is the third coordinate of our vector. 

<img src="12-25.jpg" />

<img src="12-26.jpg" />

<img src="12-27.jpg" />



###### Why think of coordinates as areas and volumes like this?

> As you apply some sort of matrix transformation, the areas of the parallelograms, they don't stay the same, they might get scaled up or down. 
>
> But, and this is a key idea of determinants, all of the areas get scaled by the same amount. Namely, the determinant of our transformation matrix. 

<img src="12-28.jpg" />



###### For example

> If you look the parallelogram spanned by the vector where your first basis vector lands, which is the first column of the matrix, and the transformed version of [x; y], what is its area? 

<img src="12-29.jpg" />

> Well, this is the transformed version of that parallelogram we were looking at earlier, 
>
> the one whose area was the y-coordinate of the mystery input vector. 

<img src="12-30.jpg" />

> So its area is just gonna be the determinant of the transformation multiplied by that y-coordinate. 

<img src="12-31.jpg" />

> So that means we can solve for y by taking the area of this new parallelogram in the output space, divided by the determinant of the full transformation. 

> And how do you get that area? 
>
> We know the coordinates for where the mystery input vector lands, that's the whole point of a linear system of equations. 
>
> So what you might do is create a matrix whose first column is the same as that of our matrix, but whose second column is the output vector, and then you take its determinant. 

<img src="12-32.jpg" />

> So look at that, just using data from the output of the transformation, namely the columns of the matrix and the coordinates of our output vector, 
>
> we can recover the y-coordinate of the mystery input vector, which is halfway to solve the system.
>
> Likewise, the same idea can get us the x-coordinate. 

 <img src="12-33.jpg" />



> This formula for finding the solutions to a linear system of equations is known as **Cramer's rule.** 

<img src="12-34.jpg" />

