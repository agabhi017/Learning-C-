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
