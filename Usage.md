# General Matrix Operations #

Most matrix operations share a similar format:

**mat4._operation_(**srcMatrix, _otherOperands_, destMatrix _(optional)_**);**

For all functions following this format the operation will be applied to the values in _srcMatrix_ and the result will be written into _destMatrix_, which will also be returned. If _destMatrix_ is not specified the result will be written into _srcMatrix_, if _destMatrix_ is specified _srcMatrix_ will not be altered.

Any 4x4 matrix functions expect sequences at least 16 elements in length as inputs when taking a matrix.

# Examples #

Creating and using a perspective matrix
```
var persp = mat4.create();
mat4.perspective(45, 4/3, 1, 100, persp );

gl.uniformMatrix4fv(perspectiveUniform, false, persp);
```

Performing multiple transforms on a matrix
```
var modelView = mat4.create();

mat4.identity(modelView); // Set to identity
mat4.translate(modelView, [0, 0, -10]); // Translate back 10 units
mat4.rotate(modelView, Math.PI/2, [0, 1, 0]); // Rotate 90 degrees around the Y axis
mat4.scale(modelView, [2, 2, 2]); // Scale by 200%
```

Updating a destination matrix
```
var modelViewPersp = mat4.create();

mat4.multiply(modelView, persp, modelViewPersp); // Sets modelViewPersp to modelView * persp 
```

Tranforming a point
```
var cameraPos = [0, 0, 0];
var newPos = [0, 0, 0];

mat4.multiplyVec3(modelView, cameraPos); // Result is written into cameraPos
mat4.multiplyVec3(modelView, cameraPos, newPos); // Result is written into newPos
```

# Matrix Functions #

**mat4.create()**
> Returns a 16 element array. If WebGL is enabled, array type will be WebGLFloatArray, otherwise it will be a standard javascript Array.

**mat4.set(mat, dest)**
> Copies the contents of _mat_ into _dest_.

**mat4.identity(dest)**
> Set _dest_ to an identity matrix.

**mat4.transpose(mat, dest)**
> Transposes _mat_

**mat4.determinant(mat)**
> Returns the determinant of _mat_. _mat_ is left unchanged.

**mat4.inverse(mat, dest)**
> Inverts _mat_

**mat4.toMat3(mat, dest)**
> Populates dest with the upper 3x3 elements of the matrix. (ie: The rotation matrix). _dest_ is expected to be a sequence of at least 9 elements. If _dest_ is not specified a new 9 element array is created and returned.

**mat4.toInverseMat3(mat, dest)**
> Calculates the inverse of the top 3x3 elements of _mat_. (ie: calculates the normal matrix). _dest_ is expected to be a sequence of at least 9 elements. If _dest_ is not specified a new 9 element array is created and returned.

**mat4.multiply(mat, mat2, dest)**
> Multiplies _mat_ and _mat2_

**mat4.multiplyVec3(mat, vec, dest)**
> Multiplies the the vector _vec_ by _mat_. _vec_ and _dest_ are expected to be sequences of at least 3 elements. If _dest_ is not provided the result is written into _vec_.

**mat4.translate(mat, vec, dest)**
> Translates _mat_ by the vector _vec_.

**mat4.scale(mat, vec, dest)**
> Scales _mat_ by the vector _vec_.

**mat4.rotate(mat, angle, axis, dest)**
> Rotates _mat_ by _angle_ (given in radians) around the axis given by the vector _axis_.

**mat4.frustum(left, right, bottom, top, near, far, dest)**
> Calculates a frustum matrix with the given parameters and writes it into _dest_.

**mat4.perspective(fovy, aspect, near, far, dest)**
> Calculates a perspective matrix with the given parameters and writes it into _dest_.

**mat4.ortho(left, right, bottom, top, near, far, dest)**
> Calculates a orthogonal matrix with the given parameters and writes it into _dest_.