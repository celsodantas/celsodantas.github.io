---
layout: post
title: "Quaternions: what and why?"
date: 2014-06-07 20:26
comments: true
categories: ruby code
---

To fully understand about Quaternions, you should first understand what **Complex Numbers** are. I'll
explain what a Quaternion is in a general matter first, and then explain it's basics.

### What is it?

**A Quaternion represents a rotation of a point in 3D space around an axis.** That's it.

The name `Quaternion` has it's name because it's formed by 4 values (quadruple). Don't worry why it uses 4 values now. Just know that each of the values need to be build using _sin_/_cos_ to actually means anything.

If you have a point in space, and you want to rotate it around any axis, you **can** use a Quaternion to do so. You can use other techniques, if you want too. Quaternions are just another option. Depending on your problem, it might better suit your solution.

<!-- more -->

### Why use it?

In 3D programming, if you want to rotate something (like a camera around the character), you can do it using:

  - [Matrix rotation (wikipedia)](http://en.wikipedia.org/wiki/Rotation_matrix#In_three_dimensions)
  - [Euler Angles (wikipedia)](http://en.wikipedia.org/wiki/Euler_angles)
  - Quaternions

Each of them, have pros and cos. I'll list some advantages of each:

##Quaternions

  - **Easy to interpolate between quaternions** - It's usefull for animations or camera movements. You can say: interpolate all values from rotation A to rotationB easily (see SLERP or LERP, for interpolation functions)
  - **Less rounding effects** - Quaternions suffer way less data loss then matrixes. As you keep stacking data on matrixes, some data might lose precision.
  - **No gimbal-lock issue** (like Euler Angles does)
  - **Ocupy less memory then Matrixes** - It's 4 numbers, instead of 16 for a 4x4 matrix.

This is how you rotate 90° on X axis using Quaternions:

```c++
#define GLM_FORCE_RADIANS
#include <glm/glm.hpp>
#include <glm/ext.hpp>
#define PI 3.14f

float angle = PI/2;
quaternion = glm::quat( glm::vec3(angle, 0 ,0) );
glm::mat4 rotationMatrix = glm::toMat4(quaternion);
```

Or:

```c++
#define GLM_FORCE_RADIANS
#include <glm/glm.hpp>
#include <glm/ext.hpp>
#define PI 3.14f

float angle = PI/2.f;
glm::vec3 axis(1, 0, 0);
quaternion = glm::angleAxis(angle, axis);
glm::mat4 rotationMatrix = glm::toMat4(quaternion);
```

##Matrixes

  - **Speed** -  You can stack movements (like translation and scale) in a single matrix and in a single operation, apply it to you 3D object. For Quaternions, you need to translate it to a 4x4 matrix first.

This is how you rotate 90° on X axis using Matrix:

```c++
#define GLM_FORCE_RADIANS
#include <glm/glm.hpp>
#include <glm/ext.hpp>
#define PI 3.14f

glm::mat4 unitMatrix(1.f);
glm::mat4 rotationMatrix = glm::rotate(unitMatrix, PI/2.f, glm::vec3(1, 0, 0));
```

##Euler Angles

  - **Easier to read** - It's more human readable. You basically say the angles in each axis you want to rotate.

This is how you rotate 90° on X axis using Euler Angles:

```c++
#define GLM_FORCE_RADIANS
#include <glm/glm.hpp>
#include <glm/ext.hpp>
#define PI 3.14f

glm::mat4 rotationMatrix = glm::eulerAngleYXZ(0.f, PI/2.f, 0.f);
```

Or use this:

```c++
#define GLM_FORCE_RADIANS
#include <glm/glm.hpp>
#include <glm/ext.hpp>
#define PI 3.14f

glm::mat4 rotationMatrix = glm::yawPitchRoll(0.f, PI/2.f, 0.f);
```


Observations:

 - I'm using `GLM_FORCE_RADIANS` in the examples because the use of degrees is deprecated._
 - I'm adding `<glm/ext.hpp>` for simplification purposes.
 - The end result should always be matrixes, as this is what your video card will read.








