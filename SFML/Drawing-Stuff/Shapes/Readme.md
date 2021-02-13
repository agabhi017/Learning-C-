# Drawing Shapes ( `sf::Shape` )

* The different shape classes are derived from the same base class and hence share some common features and add more specifics on top of them such as radius for a 
circle shape etc.
* Some of the common classes/member functions which might be useful while dealing with shapes are :
  * `sf::Color`
  * `sf::Vertex`
  * `sf::Vector2f`
  * `sf::Shape.setFillColor`
  * `sf::Shape.setOutlineThickness`   (by default, the outline extrudes outwards from the given shape dimensions and hence will increase the overall size of the shape. In order to 
  squeeze the outline in the original dimensions, set the outline thickness to a negative value)
  * `sf::Shape.setOutlineColor`
  * `sf::Shape.setTexture`
  * `sf::Shape.setTextureRect`
* Following shapes can be drawn :
  * Rectangles (`sf::RectangleShape`)
    * `rectangle.setSize(sf::Vector2f(float, float))`
  * Circles (`sf::CircleShape`)   (the constructor for the circle shape takes in two arguments - radius and number of points(optional))
    * `circle.setRadius(float)`   `circle.setPointCount(int)`
  * Polygons (`sf::CircleShape`) (Yes!, the circle is indeed a polygon as one needs to define the number of points in the polygon used to draw the cricle. More number of points
  will result in a smoother circle)
  * Lines with thickness (`sf::RectangleShape`)  (Lines with thickness are simply rectangles)
  * Lines without thickness can be drawn by creating an array of `sf::Vertex`
  * Convex Shapes (`sf::ConvexShape`)
    * `convex.setPointCount(int)`   `convex.setPoint(int point_id, sf::Vector2f(float x, float y))`
  * Custom shape types can be defined by inheriting the `sf::Shape` base class
