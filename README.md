![Slide1](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.001.png)

 * **Algebraic modeling is a composition of techniques that can be used to produce geometry.**
 * **The basic idea is that we will start with an _implicit_ shape, like a sphere, then produce a chain of _domain distortions_ that will bend the sphere into a desired shape.**
 * **The end result is a single polynomial that describes the shape we want.**
 
<br><br>
---
<br><br><br>

![Slide2](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.002.png)

* **For a function _f_ of one real variable _x_ we can plot _f(x) = y_ in Cartesian coordinates**
* **Here, and for the next few slides our _f(x)_ is a gaussian curve.**
* **By rearranging the terms, we can turn our _f(x)_ into a function of 2D space _f(x, y)_.**
* **For all positions _<x, y>_ in the space, the positions with _f(x, y) = 0_ are on the _image_ of the real line.**
* https://en.wikipedia.org/wiki/Implicit_function

<br><br>
---
<br><br><br>

![Slide3](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.003.png)

* **Since our function _f(x,y)_ is defined for all positions _<x, y>_, and not just where _f(x, y) = 0_ then we can generalize it's output to be _f(x, y) = level_.**
* **Here, we can see that the _distortion_ caused by _f(x, y)_ affects all of 2D space. We have chosen the gaussian since it _isolates_ its effect to values of _x_ within a range of _x = 0_.**
* https://www.shadertoy.com/view/WscSRr
* https://en.wikipedia.org/wiki/Level_set

<br><br>
---
<br><br><br>

![Slide4](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.004.png)

* **We define the _domain distortion d(<x, y>)_ which takes a position, and outputs a position. The output is related to the input by our _distortion functiton f(x)_. We are still using the same _f(x)_ from the first slide.**
* https://www.iquilezles.org/www/articles/warp/warp.htm

<br><br>
---
<br><br><br>

![Slide5](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.005.png)

* **We define the _image function i(x, y)_ as the body we want to distort. So far, we have been distorting the real line _y = 0_.**
* **For 2D the _image function i_ is any picture or function we can render on the plane. For 3D, it is any implicit or volumetric function that can be rendered in a volume, like a sphere or mandlebulb fractal.**

<br><br>
---
<br><br><br>

![Slide6](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.006.png)

* **This is a slightly different image function, where we have not restricted shading to the real line, but instead shade the whole negative half plane. If the image of a distorted position is negative, we shade it. The color used is based on the gradient of the function.**

<br><br>
---
<br><br><br>

![Slide7](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.007.png)
![Slide8](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.008.png)

* **While the real line and half plane images are _open_ or _unbounded_ here we see that the superellipse is _bounded_.**
* **We will continue to use bounded image functions, and can consider this the _body_ in traditional modeling terms.**
* **This body is only shaded near the surface as an artistic decision, but it could be filled and have any texture on it, and that would be distorted as well.**
* https://www.shadertoy.com/view/Wd3Szr

<br><br>
---
<br><br><br>

![Slide9](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.009.png)

* **So far, our distortion function _f(x)_ has been fixed to the conventional form real line, centered at <0, 0> and horizontal with the view.**
* **Our distortion function _f(x)_ can be thought of as _relative_ to this line, but we could also make it relative to any other line.**
* **We can generalize this relationship to any number of dimensions by thinking of distortions as being relative to _hyperplanes_.**
* **Just as a line is a hyperplane in 2D, what we usually call a "plane" is a hyperplane in 3D.**
* **We can construct hyperplanes by defining them as having an origin and normal.**
* **This is really just a way of thinking. We will be using the idea of hyperplanes implicitly. We won't need any data structures or intersection routines for the planes.**
* https://en.wikipedia.org/wiki/Hyperplane

<br><br>
---
<br><br><br>

![Slide10](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.010.png)

* **Instead we will use _homogeneous model matrix transformations_ which are very well known in graphics.**
* **It is helpful to think of the _default hyperplane_ that the matrix will transform, and that our distortion function _f(x)_ will be relative to.**
* **In 2D, our default hyperplane is the real line _y = 0_, which can be thought of as centered at <0, 0> with normal <0, 1>. In 3D, it can be thought of as centered at <0, 0, 0> with normal <0, 0, 1>.**
1. **Choose a model matrix with the desired origin, and rotation.**
2. **Use the inverse of the model matrix to pull the _global-relative_ position _<x, y>_ into the model space, so that it is relative to our desired hyperplane.**
3. **Apply the _domain distortion d(<x, y>)_ in the _hyperplane-relative_ space.**
4. **Transform the distorted position back to _global-relative_ using the model matrix.**
* https://en.wikipedia.org/wiki/Transformation_matrix

<br><br>
---
<br><br><br>

![Slide11](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.011.png)

* **We can think of the image function as being defined in global space.**

<br><br>
---
<br><br><br>

![Slide12](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.012.png)
![Slide13](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.013.png)

* **The hyperplane is shown in yellow, the level curves are colored by floating point fractional, and the surface of the body is colored by normal.**
* https://www.shadertoy.com/view/3stSRr

<br><br>
---
<br><br><br>

![Slide14](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.014.png)
* **If we want to restrict the distortion region, we can define an _isolation function  iso(x, y), _0 <= iso(x, y) <= 1_. This is used in the hyperplane-relative space.**
* **We can then _isolate_ the distortion by multiplying the isolation output onto the distortion function, so our domain distortion _d(<x, y>) = <x, y - iso(x, y) * f(x)>_**
* https://www.shadertoy.com/view/3dtXRr

<br><br>
---
<br><br><br>

![Slide15](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.015.png)
* **Some choices of isolation function can create _holes_.**
* **There may be a cleaner way to make holes precisely, but I've not formulated it yet.**
* https://www.shadertoy.com/view/WsdSRr

<br><br>
---
<br><br><br>

![Slide16](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.016.png)
![Slide17](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.017.png)

* **So far, we have only used one distortion, but we can have any number of distortions, and the user can produce them in a sequence.**
* **If the image function is algebraic, the distortion function is analytic, and the domain distortion uses linear algebra, then all of this can be expanded into a single polynomial in variables x, y for 2D or x, y, z for 3D.**
* **This expansion should be simplified using a Computer Algebra System (CAS) to improve performance.**
* **Here is a video demonstrating this technique in 3D, with three distortions:**

[![](http://img.youtube.com/vi/Usenu_oLqL4/0.jpg)](http://www.youtube.com/watch?v=Usenu_oLqL4 "3D Algebraic Modeling Demo by Skye Adaire")
