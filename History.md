# Version History #

**Version 0.9.5 (1.0 RC2)** _(02/27/2011)_
  * <sup>Issue 24</sup> Fixed bug in mat4.lookat (Thanks to Drew Whitehouse)
  * <sup>Issue 29</sup> Fixed bug in mat4.scale (Thanks to jeroom)
  * <sup>Issue 30</sup> Flipped mat4.ortho to match the glOrtho implementation (Thanks to orphansandoligarchs)
  * <sup>Issue 32</sup> Added vec3.lerp and quat4.slerp functions (Thanks to Denis Rangel)
  * <sup>Issue 33</sup> Fixed a (really stupid) bug in mat4.multiplyVec4 (Thanks to Jeremy Mlazarus)
  * <sup>Issue 36</sup> Added mat3.transpose at the suggestion of shooskx

**Version 0.9.4 (1.0 RC1)** _(07/02/2010)_
  * Added documentation comments to all functions
  * Added `mat3.identity`
  * Added `quat4.str`
  * Some minor whitespace formatting to be more consistent across the file
  * Updated `mat4.frustum`, `mat4.perspective`, `mat4.ortho`, and `mat4.lookat` to all return new matricies if dest is not specified
  * Updated parameter names on `quat4.multiply` for consistency
  * <sup>Issue 1</sup> Changed default array type to `Float32Array`. `WebGLFloatArray` and `Array` still used as fallbacks.
  * <sup>Issue 16</sup> changed `q[x] = -q[x]` to `q[x] *= -1` in `quat4.inverse`
  * <sup>Issue 17</sup> changed `x = x / y` to `x /= y`
  * <sup>Issue 18</sup> started reusing len variables instead of creating new vars for inverse length
  * <sup>Issue 23</sup> (In Progress) Added unit test folder, need to expand test suite. (Thanks to Drew Whitehouse)
  * <sup>Issue 24</sup> in `mat4.lookat` changed `mat4.identity()` to `mat4.identity(dest)`, added `quat4.create`
  * <sup>Issue 25</sup> added dest parameter to `quat4.normalize`

**Version 0.9.3** _(06/14/2010)_
  * <sup>Issue 14</sup> Removed bitshifiting optimization when it was pointed out that this method fails for non-integers

**Version 0.9.2** _(06/12/2010)_
  * Probably the last release before 1.0, syntax may still change.
  * **mat4.inverse3x3 renamed to mat4.toInverseMat3 for consistency**
  * Added `mat4.toMat3`
  * Added `mat3.toMat4`
  * Added Quaternion functions
  * Started appending version numbers to the file name
  * <sup>Issue 10</sup> Minimized version now generated with Google's Closure Compiler
  * <sup>Issue 5</sup> Changed instances of `var == 0` to `!var`
  * <sup>Issue 12</sup> Corrected issue with `vec3.cross` crossing the first vector with itself
  * <sup>Issue 13</sup> Optimized `mat4.lookAt`
  * <sup>Issue 7</sup> Replaced some multiplies with bit-shifts

**Version 0.9** _(06/05/2010)_
  * Added a packed version (glMatrix-min.js)
  * Merged `(!dest)` and `(dest == src)` checks where possible, and changed the inner code of these scenarios to write directly to the source matrix (saves one assignment and speeds up the check)
  * Added earlier returns wherever possible
  * Re-implemented `inverse()`, which now re-uses several calculations and can run much faster
  * Rearranged some of the logic of `inverse3x3()` to prevent unnecessary assignments and calculations
  * Corrected issue with `multiplyVec3()` multiplying against a transposed matrix.
  * Added `multiplyVec4()`.
  * Broke special case rotation (rotation along the X, Y, or Z axis) optimizations out into their own functions: `rotateX()`, '`rotateY()`, and `rotateZ()`. This speeds up both the special cases and the general case rotation. `rotate()` will no longer optimize the special case rotations.
  * While reordering rotation code also discovered a few more minor optimizations that could be applied.
  * Added `mat4.lookAt()` (Unoptimized)
  * Added `mat4.str()` for debugging use.
  * Added `vec3.direction()`.

**Version 0.8**
  * Initial Release (Because no-one wants to use a 0.1 product!)