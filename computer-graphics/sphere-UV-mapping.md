# UV mapping a sphere (for finding texture coordinates)
> 13/10/2017

```c++
glm::vec3 n = glm::normalize(sphere_surface_point - sphere_center);
GLfloat u = atan2(n.x, n.z) / (2 * PI) + 0.5;
GLfloat v = n.y * 0.5 + 0.5;
```
[[source]](https://gamedev.stackexchange.com/a/114416)
