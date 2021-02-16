# Vertex Arrays

* Vertex arrays allows us to make custom shapes in SFML
* If we draw multiple stripes in each iteration of the game loop, the performance will taka a hit as :
  * Each call of `window.draw()` calls `sf::RenderTarget::draw()`
  * Each call of `sf::RenderTarget::draw()` then involves setting a set of OpenGL states, resizing matrices, changing textures etc.
* The performance can be optimized by constructing a vector of vertices first with each of them having a defined texture and then calling the `sf::RenderTarget::draw()`.
* Since modern GPUs are efficient in handling large arrays of information, the performance is much better than setting OpenGL states hundreds of times in a single 
itertaion of the game loop.
* Vertex arrays are used intrnally by all other SFML clases.
* `sf::VertexArray` provides a convenient method to define such vertex vectors and draw custom 2D entities.
* `sf::VertexArray` is a simple wrapper around `sf::Vertex`. It provides the semantics of an array (similar to std::vector) and also stores the primitive type
* A vertex has the following attributes/members :
  * A 2D position  (`sf::Vertex:position()`)
  * Color  (`sf::Vertex:color`)
  * Texture Coordinates  (`sf::Vertex:texCoords`)
* Primitives are the basic 2D shapes that allow to render complex shapes. Some of the pre-defined primitives are :
  * `sf::Points`  (set of unconnected points)
  * `sf::Lines`  (set of unconnected lines)
  * `sf::LineStrip`  (set of connected lines)
  * `sf::Triangles`  (set of unconnected triangles)
  * `sf::TriangleStrip`  (set of connected triangles sharing 2 vertices or 1 edge at a time)
  * `sf::TriangleFan`  (set of triangles connected to a central point)
  * `sf::Quads`  (set of unconnected quadrilaterals. The 4 points must be defined either clockwise or counter-clockwise)
* The vertex array is initialized as `sf::VertexArray my_shape(sf::PrimitiveType, int number_of_points)`
* The color of the vertices are interpolated to fill the primitive and give a gradient look.
* Other ways of creating vertex arrays :
  ```
  std::vector<sf::Vertex> vertices;
  vertices.push_back(sf::Vertex(...));
  ...

  window.draw(&vertices[0], vertices.size(), sf::Triangles);
  ```
  ##################################
  ```
  sf::Vertex vertices[2] =
  {
      sf::Vertex(...),
      sf::Vertex(...)
  };

  window.draw(vertices, 2, sf::Lines);
  ```

* To render a texture with a vertex array, pass the texture pointer separately as an argument in the `window.draw()` call or create an instance of `sf::RenderStates` 
pass it as an attribute to the `window.draw()` after updating the texture member.
* Similarly transformations can either be passed into `window.draw()` either as an `sf::Taansform` object or an `sf::RenderStates`

