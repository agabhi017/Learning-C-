## `sf::Transformable`

* `sf::Transformable` is a class that is provided for convenience on top of `sf::Transform` class.
* The `sf::Transform` class defines how the transformations (translations/rotation/scaling/shearing etc) are done to an object. It defines a 3X3 transform matrix.

An example of using `sf::Transform`

```
// define a translation transform
sf::Transform translation;
translation.translate(20, 50);

// define a rotation transform
sf::Transform rotation;
rotation.rotate(45);

// combine them
sf::Transform transform = translation * rotation;

// use the result to transform stuff...
sf::Vector2f point = transform.transformPoint(10, 20);
sf::FloatRect rect = transform.transformRect(sf::FloatRect(0, 0, 10, 100));
```
* Since `sf::Transform` doesnt holds any data about the intermediate steps/transforms, it is cumbersome if we wish to undo any operation and implement the rest. This 
is where `sf::Transformable` cimes into picture. It has private member data varaibles that stores the origin, position, rotation, scale etc.
* Note: In order to render a sf::Drawable object pixel-perfectly, make sure the involved coordinates allow a 1:1 mapping of pixels in the window to 
texels (pixels in the texture).More specifically :
  * No fractional part in object's position, origin and scale
  * Object's and view's rotation are a multiple of 90 degrees
  * No fractional part in view's center and size
