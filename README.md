![Slide1](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.001.png)

 * **Algebraic modeling is a composition of techniques that can be used to produce geometry.**
 * **The basic idea is that we will start with an _implicit_ shape, like a sphere, then produce a chain of _domain distortions_ that will bend the sphere into a desired shape.**
 * **The end result is a single polynomial that describes the shape we want.**
 
---

![Slide2](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.002.png)

* **For a function _f_ of one real variable _x_ we can plot _f(x) = y_ in Cartesian coordinates**
* **Here, and for the next few slides our _f(x)_ is a gaussian curve.**
* **By rearranging the terms, we can turn our _f(x)_ into a function of 2D space _f(x, y)_.**
* **For all positions _<x, y>_ in the space, the positions with _f(x, y) = 0_ are on the _image_ of the real line.**
* https://en.wikipedia.org/wiki/Implicit_function

---

![Slide3](https://github.com/skye-adaire/AlgebraicModeling/blob/master/media/Algebraic%20Modeling.003.png)

* **Since our function _f(x,y)_ is defined for all positions _<x, y>_, and not just where _f(x, y) = 0_ then we can generalize it's output to be _f(x, y) = level_.**
* **Here, we can see that the _distortion_ caused by _f(x, y)_ affects all of 2D space. We have chosen the gaussian since it _isolates_ its effect to values of _x_ within a distance to _x = 0_.**
* https://en.wikipedia.org/wiki/Level_set
