## Chapter 7: Dot Products and Duality（点积和对偶性）

> Calvin: You know, I don't think math is a science, I think it's a religion. 
>
> Hobbes: A religion? 
>
> Calvin: Yeah. All these equations are like miracles. You take two numbers and when you add them, they magically become one NEW number! No one can say how it happens. You either believe it or you don't. 
>
> 卡尔文：你知道吗，我觉得数学不是一门科学，而是一种宗教。
>
> 霍布斯：一种宗教？
>
> 卡尔文：是啊。这些公式就像奇迹一般。你取出两个数，把它们相加时，它们神奇地成为了一个全新的数！没人能说清这到底是怎么发生的。你要么完全相信，要么完全不信。
>
> —— 《卡尔文与霍布斯》连载四格漫画，1991/03/06



> Only with transformations can we truly understand. 





#### Dot Products

###### Numerically

<img src="7-1.jpg" />

> Numerically, if you have two vectors of the same dimension, two lists of numbers with the same lengths, taking their **dot product**, means: 
>
> - pairing up all of the coordinates, 
> - multiplying those pairs together 
> - and adding the result. 



###### Geometric Interpretation

> Luckily, this computation has a really nice geometric interpretation: 
>
> To think about the dot product between two vectors - v and w,
>
> imagine projecting w onto the line that passes through the origin and the tip of v, 
>
> multiplying the length of this **projection（投影）** by the length of v, 
>
> you have the dot product - v dot w. 

<img src="7-2.jpg" />

<img src="7-3.jpg" />



###### Similar directions

<img src="7-4.jpg" />

###### Perpendicular

<img src="7-5.jpg" />

###### Opposing directions

<img src="7-6.jpg" />



###### Order doesn't matter

<img src="7-7.jpg" />

<img src="7-8.jpg" />

> **Q:** Why order doesn't matter?
>
> **A: ** If v and w happened to have the same length, we could leverage some **symmetry**. 
>
> Since projecting w onto v then multiplying the length of that projection by the length of v is a complete mirror image of projecting v onto w then multiplying the length of that projection by the length of w. 

<img src="7-9.jpg" />

> Now, if you scale one of them, say v, by some constant, like 2, so they don't have equal length, **the symmetry is broken.** 
>
> If you think of w as getting projected onto v, then the dot product, 2v dot w, will be exactly twice the dot product, v dot w. 
>
> This is because when you scale v by 2, it doesn't change the length of the projection of w, but it doubles the length of the vector that you are projecting onto. 

<img src="7-10.jpg" />

<img src="7-11.jpg" />



#### Duality（对偶性）

###### Number Line（数轴）

<img src="7-12.jpg" />



###### Linear Transformation

> These are functions that take in a 2-D vector and spit out some number. 
>
> But linear transformations are, of course, much more restricted than you run of the mill function with a 2-D input and a 1-D output. 
>
> Linear functions are quite special. 

<img src="7-13.jpg" />



> If you take a line of evenly spaced dots and apply a transformation, a linear transformation will keep those dots evenly spaced once they land in the output space, which is the number line. 

<img src="7-14.jpg" />

<img src="7-15.jpg" />



> One of these linear transformations is completely determined by where it takes `i-hat` and `j-hat`, but this time each one of those basis vectors just lands on a number. 
>
> So when we record where they land as the columns of a matrix, each of those columns just has a single number. 

<img src="7-16.jpg" />



###### Example

<img src="7-17.jpg" />

<img src="7-18.jpg" />

<img src="7-19.jpg" />

<img src="7-20.jpg" />

> Now, this numerical operation of multiplying a 1-by-2 matrix by a vector feels just like taking the dot product of two vectors. 
>
> Doesn't that 1-by-2 matrix just look like a vector that we tipped on its side? 



###### 1-by-2 Matrices（1x2 矩阵） vs. 2-D vectors（二维向量）

> There's a nice association between 1-by-2 matrices and 2-D vectors, defined by tilting the numerical representation of a vector on its side to get the associated matrix, or to tip the matrix back up to get the associated vector. 

<img src="7-21.jpg" />

<img src="7-22.jpg" />



> This suggests something that's truly awesome from the geometric view. 
>
> There's some kind of connection between linear transformations that take vectors to numbers and vectors themselves. 

<img src="7-23.jpg" />



#### Example

###### 1. Unit Vector

<img src="7-24.jpg" />

<img src="7-25.jpg" />

<img src="7-26.jpg" />

<img src="7-27.jpg" />

<img src="7-28.jpg" />

<img src="7-29.jpg" />

> So the entries of the 1-by-2 matrix describing the projection transformation are going to be the coordinates of `u-hat`. 
>
> And computing this projection transformation for arbitrary vectors in space, which requires multiplying that matrix by those vectors, is computationally identical to taking a dot product with `u-hat`. 

<img src="7-30.jpg" />

<img src="7-31.jpg" />

> This is why taking a dot product with a unit vector can be interpreted as projecting a vector onto the span of that unit vector and taking the length. 



###### 2. Non-unit Vectors

<img src="7-32.jpg" />

<img src="7-33.jpg" />

<img src="7-34.jpg" />



> We had a linear transformation from 2-D space to the number line, which was not defined in terms of numerical vectors or numerical dot products, it was just defined by projecting space onto a diagonal copy of the number line. 
>
> But because the transformation is linear, it was necessarily described by some 1-by-2 matrix. 
>
> And since multiplying a 1-by-2 matrix by a 2-D vector is the same as turning that matrix on its side and taking a dot product, this transformation was inescapably related to some 2-D vector. 

> The lesson here is that anytime you have one of these linear transformations, whose output space is the number line, no matter how it was defined, there is going to be some unique vector v corresponding to that transformation, in the sense that applying the transformation is the same thing as taking a dot product with that vector. 

<img src="7-35.jpg" />

> You'd say that **dual of a vector** is the linear transformation that it encodes,
>
> **the dual of a linear transformation** from some space to one dimension is a certain vector in that space. 



#### To Sum Up

> On the surface, the dot product is a very useful geometric tool for understanding projections. 
>
> And for testing whether or not vectors tend to point in the same direction. And that's probably the most important thing for you to remember thing for you to remember about the dot product. 
>
> But at a deeper level, **dotting two vectors together is a way to translate one of them into the world of transformations.** 
>
> Again, numerically this might seem like a silly point to emphasize. It's just two computations that happen to look similar. 
>
> But the reason I find this so important is that throughout math when you are dealing with a vector, once you really get to know its personality, sometimes you realize that it's easier to understand it not as an arrow in space, but as the physical embodiment of a linear transformation. 
>
> It's as if the vector is really just a conceptual shorthand for a certain trans formation, since it's easier for us to think about arrows in space rather than moving all of that space to the number line. 

