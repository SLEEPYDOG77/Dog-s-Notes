# Chapter11: Abstract vector spaces

> "Such axioms, together with other unmotivated definitions, serve mathematicians mainly by making it difficult for the uninitiated to master their subject, thereby elevating its authority. "
>
> —— Vladimir Arnold
>
> 这些公理，同其他动机不明的定义一起，让门外汉难以掌握数学。它们主要通过这样的方式协助数学家，从而提升数学的权威性。
>
> —— 弗拉基米尔·阿诺尔德



[TOC]

#### Revisit

> I'd like to revisit a deceptively simple question that I asked in the very first video of this series, "What are vectors? "
>
> Is it a two-dimensional vector, for example, 
>
> - fundamentally an arrow on a flat plane that we can describe with coordinates for convenience? 
> - Or is it fundamentally that pair of real numbers, which is just nicely visualized as an arrow on a flat plane? 
> - Or are both of these just manifestations of something deeper? 

<img src="11-1.jpg" />

> On the one hand, defining vectors as primarily being a list of numbers feels clear-cut and unambiguous. 
>
> It makes things like four-dimensional vectors or one hundred-dimensional vectors sound like real, concrete ideas that you can actually work with. 
>
> When otherwise, an idea like four dimensions is just a vague geometric notion that's difficult do describe without waving your hands a bit. 

（将向量看做一组数，更易于理解，因为现实中难以想象那么多维度的空间。看作数，则可认为是衡量一个事物的不同维度、不同指标、不同参数。）

> But, on the other hand, a common sensation for those who actually work with linear algebra, especially as you get more fluent with changing your basis, is that you're dealing with a space that exists independently from the coordinates that you give it. 
>
> And that coordinates are actually somewhat arbitrary, depending on what you happen to choose as your basis vectors. 



<img src="11-2.jpg" />

> Core topics in linear algebra, like determinants and eigenvectors, seem indifferent to your choice of coordinate systems. 
>
> - The determinant tells you how much a transformation scales areas, 
>
> - and eigenvectors are the ones that stay on their own span during a transformation. 
>
> But both of these properties are inherently spatial, and you can freely change your coordinate system without changing the underlying values of either one. 

<img src="11-3.jpg" />



> But, if vectors are not fundamentally lists of real numbers, and if their underlying essence is something more spatial, that just begs the question of what mathematicians mean when they use a word like "space" or "spatial（空间性）".



#### Functions

> To build up to where this is going, I'd actually like to spend the bulk of this video talking about something which is neither an arrow nor a list of numbers, but also has vector-ish qualities: Functions.



> You see, there's a sense in which functions are actually just another type of vector. 

###### Function Adding

<img src="11-4.jpg" />

> In the same way that you can add two vectors together, there's also a sensible notion for adding two functions - f and g, to get a new function - (f+g). 

<img src="11-5.jpg" />

> The output of this new function at any given input, is the sum of the outputs of f and g when you evaluate them each at that same input.
>
> Or, more generally, the value of the sum function at any given input x is the sum of the values of f(x) + g(x). 

<img src="11-6.jpg" />

> This is pretty similar to adding vectors coordinate by coordinate,
>
> it's just that there are, in a sense, infinitely many coordinates to deal with. 

<img src="11-7.jpg" />



###### Scale a function by a real number

> Similarly, there's a sensible notion for scaling a function by a real number, just scale all of the outputs by that number. 

<img src="11-8.jpg" />

> And again this is analogous to scaling a vector coordinate by coordinate, it just feels like there's infinitely many coordinates. 

<img src="11-9.jpg" />



> Now, given that the only thing vectors can really do is get added together or scaled, it feels like we should be able to take the same useful constructs and problem-solving techniques of linear algebra that were originally thought about in the context of arrows in space, and apply them to functions as well. 

<img src="11-10.jpg" />



###### Linear transformation for functions

> Something that takes in one function and turns it into another. 

<img src="11-11.jpg" />

> One familiar example comes from calculus（微积分） - **the derivative（导数）**
>
> It's something which transforms one function into another function. 

<img src="11-12.jpg" />

> Sometimes, in this context, you'll hear these called "operators（算子）" instead of "transformations",  but the meaning is the same. 



###### Formal definition of linearity

> What does it mean for a transformation of functions to be linear? 

<img src="11-13.jpg" />

> The way you'll often hear this described is that linear transformations preserve the operations of vector addition and scalar multiplication. 



> The idea of grid lines remaining parallel and evenly spaced that I've talked about in the past videos is really just an illustration of what these two properties mean in the specific case of 2-D points in space. 

<img src="11-14.jpg" />



> One of the most important consequences of these properties, which makes matrix-vector multiplication possible, is that a linear transformation is completely described by where it takes the basis vectors. 

<img src="11-15.jpg" />

> Since any vector can be expressed by scaling and adding the basis vectors in some way, finding the transformed version of a vector comes down to scaling and adding the transformed versions of the basis vectors in that same way. 

<img src="11-16.jpg" />



###### Derivative is Linear

<img src="11-17.jpg" />

<img src="11-18.jpg" />



###### Describe the derivative with a matrix

<img src="11-19.jpg" />

> Let's limit ourselves to **polynomials**.
>
> Each of the polynomials in our space will only have finitely many terms, 
>
> but the full space is going to include polynomials with arbitrarily large degree. 



> The first thing we need to do is give coordinates to this space, with requires choosing a basis. 
>
> Since polynomials are already written down as the sum of scaled powers of the variable x, it's pretty natural to just choose pure powers of x as the basis function. 

<img src="11-20.jpg" />

> The role that these basis functions serve will be similar to the roles of `i-hat`, `j-hat` and `k-hat` in the world of vectors as arrows. 

<img src="11-21.jpg" />



> Since our polynomials can have arbitrarily large degree, this set of basis functions is infinite. 

<img src="11-22.jpg" />

> It just mean s that when we treat out polynomial as vectors, they're going to have infinitely many coordinates. 



<img src="11-23.jpg" />



> In general, since every individual polynomial has only finitely many terms, its coordinates will be some finite string of numbers with an infinite tail of zeros. 

<img src="11-24.jpg" />



> In this coordinate system, the **derivative** is described with an infinite matrix, that's mostly full of zeros, but which has the positive integers counting down on this **offset diagonal（次对角线）**. 

<img src="11-25.jpg" />

<img src="11-26.jpg" />

> You could construct this matrix by taking the derivative of each basis function, and putting the coordinates of the results in each column. 



> So surprisingly, matrix-vector multiplication and taking a derivative, which at first seem like completely different animals, are both just really members of the same family. 

<img src="11-27.jpg" />





> So, back to the question of what is a vector.
>
> The point I want to make here is that there are lots of vector-ish things in maths. 
>
> As long as you're dealing with a set of objects where there's a reasonable notion of scaling and adding, whether that's a set of arrows in space, lists of numbers, functions or what other crazy things you choose to define, all of the tools developed in linear algebra regarding vectors, linear transformations and all that stuff, should be able to apply. 

<img src="11-28.jpg" />

<img src="11-29.jpg" />



#### Axioms

###### Rules for vectors addition and scaling

<img src="11-30.jpg" />



> These axioms are not so much fundamental rules of nature, as they are an interface between you, the mathematician discovering results, and other people who might want to apply those results to new sorts of vectors spaces. 

<img src="11-31.jpg" />

> If, for example, someone defines some crazy type of vector space, these axioms are like a checklist of things that they need to verify about their definitions before you can start applying the results of linear algebra. 



> And you as a mathematician, never have to think about all the possible crazy vector spaces people might define. 
>
> You just have to prove your results in terms of these axioms, so anyone whose definitions satisfy those axioms can happily apply you results, even if you never thought about their situation. 



> As a consequence, you tend to phrase all of your results pretty abstractly, which is to say, only in terms of these axioms, rather than focusing on a specific type of vector, like arrows in space or functions. 



> So the mathematicians' answer to "what are vectors" is to just ignore the question. 
>
> In the modern theory, the form that vectors take doesn't really matter - arrows, lists of numbers, functions, Pi creatures, really, it can be anything, so long as there is some notion of adding and scaling vectors that follow these rules. 



<img src="11-32.jpg" />

> So with that, folks, I think I'll call it an end to this "Essence of Linear Algebra" series.
>
> If you've watched and understood the videos, I really do believe that you have a solid foundation in the underlying intuitions of linear algebra. 
>
> This is not the same thing as learning the full topic, of course, that's something that can only really come from working through problems, but the learning you do moving forward can be substantially more efficient if you have all the right intuitions in place. 
>
> So, have fun applying those intuitions and best of luck with your future learning. 



