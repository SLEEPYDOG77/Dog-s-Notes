# Chapter10: Eigenvectors and Eigenvalues

> "Last time, I asked: 'What does mathematics mean to you?', and some people answered: 'The manipulation of numbers, the manipulation of structures.' And if I had asked what music means to you, would you have answered: 'The manipulation of notes? ' "
>
> —— Serge Lang
>
> “上一次演讲中我问道：‘数学对你来说意味着什么？’有些人回答：‘处理数字，处理结构。’ 那么如果我问音乐对你来说意味着什么，你会回答 ‘处理音符’ 吗？”
>
> —— 塞尔日·兰

<img src="10-1.jpg" />



[TOC]

> "Eigenvectors and eigenvalues" is one of those topics that a lot of students find particularly unintuitive.
>
> Questions like "why are we doing this" and "what does this actually mean" are too often left just floating away in an unanswered sea of computations. 
>
> I suspect that the reason for this is not so much that eigen-things are particularly complicated or poorly explained. In fact, it's comparatively straightforward and I think most books do a fine job explaining it. 
>
> The issue is that it only really make sense if you have a solid visual understanding for many of the topics that precede it. 

<img src="10-2.jpg" />



#### Two dimensional

<img src="10-3.jpg" />

<img src="10-4.jpg" />

> Focus in on what it does to one particular vector and think about the span of that vector, the line passing through its origin and its tip. 

<img src="10-5.jpg" />

> Most vectors are going to get knocked off their span during the transformation. I mean, it would seem pretty coincidental if the place where the vector landed also happens to be somewhere on that line. 

<img src="10-6.jpg" />

> But some special vectors do remain on their own span, meaning the effect that the matrix has on such a vector is just to stretch it or squish it, like a scalar. 

<img src="10-7.jpg" />

<img src="10-8.jpg" />

> And for this transformation, those are all the vectors with this special property of staying on their span. 
>
> Any other vector is going to get rotated somewhat during the transformation, knocked off the line that it spans. 

<img src="10-9.jpg" />

> these special vectors are called the "**eigenvectors**" of the transformation, 
>
> and each eigenvector has associated with it, what's called an "**eigenvalue**", which is just the factor by which it stretched or squashed during the transformation. 

<img src="10-10.jpg" />



#### 3-D Rotation

> For a glimpse of why this might be a useful thing to think about, consider some three-dimensional rotation. 

<img src="10-11.jpg" />

> If you can find an eigenvector for that rotation, a vector that remains on its own span, what you found is the axis of rotation. 

<img src="10-12.jpg" />

> And it's much easier to think about a 3-D rotation in terms of some axis of rotation and an angle by which is rotating, rather than thinking about the full 3-by-3 matrix associated with that transformation. 

<img src="10-13.jpg" />

> In this case, by the way, the corresponding eigenvalue would have to be 1, since rotations never stretch or squish anything, so the length of the vector would remain the same. 



> This pattern shows up a lot in linear algebra. 
>
> With any linear transformation described by a matrix, you could understand what it's doing by reading off the columns of this matrix as the landing spots for basis vectors. 
>
> But often a better way to get at the heart of what the linear transformation actually does, less dependent on your particular coordinate system, is to find the **eigenvectors** and **eigenvalues**. 

<img src="10-14.jpg" />



#### Overview of the computational ideas

<img src="10-15.jpg" />

> - **A** is the matrix representing some transformation, 
> - **v** as the **eigenvector**, 
> - **λ** is a number, namely the corresponding **eigenvalue**. 
>
> What this expression is saying is that the matrix-vector product - A times v - gives the same result as just scaling the eigenvector v by some value λ. 

<img src="10-16.jpg" />

> So finding the eigenvectors and their eigenvalues of a matrix A comes down to finding the values of v and λ that make this expression true. 

<img src="10-17.jpg" />

> It seems like a little difficult because you need to fix different multiplication types. 



> So let's start by rewriting that right hand side as some kind of matrix-vector multiplication, using a matrix, which has the effect of scaling any vector by a factor of λ. 

<img src="10-18.jpg" />

> The columns of such a matrix will represent what happens to each basis vector, and each basis vector is simply times λ, so this matrix will have the number λ down the diagonal with 0's everywhere else. 

<img src="10-19.jpg" />

> The common way to write this guy is to factor that λ out and write it as λ times I, where I is the identity matrix with 1's down the diagonal. 

<img src="10-20.jpg" />

> With both sides looking like matrix-vector multiplication,  we can subtract off that right hand side and factor out the v. 
>
> So what we now have is a new matrix - A minus λ times the identity, 
>
> and we're looking for a vector v, such that this new matrix times v gives the zero vector. 



> Now this will always be true if v itself is the zero vector, but that's boring. What we want is a non-zero eigenvector. 

<img src="10-21.jpg" />

> The only way it's possible for the product of a matrix with a non-zero vector to become zero is if the transformation associated with that matrix squishes space into a lower dimension. 
>
> And that `squishification` corresponds to a zero determinant for the matrix. 

<img src="10-22.jpg" />



> When λ equals 1, the matrix A minus λ times the identity squishes space onto a line. 
>
> That means there's a non-zero vector v, such that A minus λ times the identity times v equals the zero vector. 

<img src="10-23.jpg" />



> And remember, the reason we care about that is because it means A times v equals λ times v, which you can read off as saying that the vector v is an eigenvector of A, staying on its own span during the transformation A.

<img src="10-25.jpg" />

<img src="10-26.jpg" />

<img src="10-27.jpg" />



#### To  Sum Up

> let's revisit the example from the start with the matrix whose columns are (3, 0) and (1, 2). 
>
> To find if a value λ is an eigenvalue,  subtracted from the diagonals of this matrix and compute the determinant. 

<img src="10-28.jpg" />

> Since λ can only be an eigenvalue if this determinant happens to be zero, you can conclude that the only possible eigenvalues are λ equals 2 and λ equals 3. 

<img src="10-29.jpg" />

> To figure out what the eigenvectors are that actually have one of these eigenvalues, say λ equals 2, plug in that value of λ to the matrix and then solve for which vectors this diagonally altered matrix sends to 0. 

<img src="10-31.jpg" />

> If you computed this the way you would any other linear system, you'd see that the solutions are all the vectors on the diagonal line spanned by (-1, 1).
>
> This corresponds to the fact that the unaltered matrix [(3, 0), (1, 2)] has the effect of stretching all those vectors by a factor of 2. 

<img src="10-32.jpg" />



###### There could be no eigenvectors

<img src="10-33.jpg" />



###### A single eigenvalue can have more that a line full of eigenvectors



#### `Eigenbasis`（特征基）

###### What if both basis vectors are eigenvectors? 

> Take a look at what happens if our basis vectors just so happened to be eigenvectors. 

<img src="10-34.jpg" />

> For example, maybe `i-hat` is scaled by -1 and `j-hat` is scaled by 2. 
>
> Writing their new coordinates as the columns of a matrix, notice that those scalar multiples -1 and 2, which are the eigenvalues of `i-hat` and `j-hat`, sit on the diagonal of our matrix and every other entry is a 0. 



###### Diagonal Matrix（对角矩阵）

> Anytime a matrix has 0's everywhere other than the diagonal, it's called, reasonably enough, a **diagonal matrix.**

<img src="10-35.jpg" />



> And the way to interpret this is that all the basis vectors are eigenvectors, with the diagonal entries of this matrix being their eigenvalues. 



> There are a lot of things that make diagonal matrices much nicer to work with. 
>
> One big one is that it's easier to compute what will happen if you multiply this matrix by itself a whole bunch of times. 
>
> Since all one of these matrices does is scale each basis vector by some eigenvalue, applying that matrix many times, say 100 times, it just going to correspond to scaling each basis vector by the 100-th power of the corresponding eigenvalue. 

<img src="10-36.jpg" />

<img src="10-37.jpg" />



> Of course, you will rarely be so lucky as to have your basis vectors also be eigenvectors, but if you transformation has a lot of eigenvectors, like the one from the start of this video, enough so that you can choose a set that spans the full space, then you could change your coordinate system so that these eigenvectors are your basis vectors. 



###### How to express a transformation currently written in our coordinate system into a different system.

> Take the coordinates of the vectors that you want to use as a new basis, 
>
> which, in this case, means are two eigenvectors, that make those coordinates the columns of a matrix, known as the change of basis matrix. 

<img src="10-38.jpg" />

> When you sandwich the original transformation putting the change of basis matrix on it's right and the inverse of the change of basis matrix on its left, the result will be a matrix representing that same transformation, but from the perspective of the new basis vectors coordinate system. 

<img src="10-39.jpg" />

> The whole point of doing this with eigenvectors is that this new matrix is guaranteed to be diagonal with its corresponding eigenvalues down that diagonal. 

<img src="10-40.jpg" />

> This is because it represents working in a coordinate system where what happens to the basis vectors is that they get scaled during the transformation. 



> A set of basis vectors, which are also eigenvectors, is called, reasonably enough, are "`eigenbasis`". 

<img src="10-41.jpg" />



> So if, for example, you needed to compute the 100-th power of this matrix, it would be much easier to change to an eigenbasis, compute the 100-th power in that system, then convert back to our standard system. 



###### Not all matrices can become diagonal

> A shear, for example, doesn't have enough eigenvectors to span the full space. 
>
> But if you can find an eigenbasis, it makes matrix operations really lovely. 



#### Test

<img src="10-42.jpg" />

