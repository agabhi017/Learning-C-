# Drawing Sprites ( `sf::Sprite` )

* Sprite is simply a rectangle filled with a texture.
* A texture defined using the `sf::Texture` is a design/pattern/image filled inside the empty rectangle.
* A texture can either be loaded from :
  * a file using `loadFromFile`  
  * memory using `loadFromMemory`
  * image using `loadFromImage`
  * custom input stream using `loadFromStream`
  * or updated from an array of pixels using `texture.create()` and the using `texture.update(pixels/image/window)`
* We can also specify if we only want to use a certain portion of the texture using `sf::IntRect(int, int, int, int)`. This function takes the top-left point and the size of the 
rectangle as input arguments.
* Operations on textures:
  * `texture.setSmooth(true)` will smoothen the texture boundary (the texture will appear blurred)
  * `texture.setRepeated(true)` will repeat the texture inside the sprite if the size of the rectangle is larger than that of the sprite
* Special attention should be given to the scope of the function which creates/loads a sprite/texture as setting the texture stores a pointer to the texture instance. 
When the texture is destroyed or moved in memory, sprite will have an invalid texture pointer.
* It is recommended to use as few textures as possible as changing texture is an expensive operation for the graphics card.
 
 ### Member functions of `sf::Sprite`
 * `sprite.setTexture(sf::Texture)`
 * `sprite.setTextureRect(sf::IntRect(int, int, int, int))` (will allow us to crop a part of the texture to be displayed in the sprite)
 * `sprite.setColor(sf::Color(int R, int G, int B, int A))`  (color of the sprite and not the texture; A : Alpha :: Transparencey)
 * `sprite.setPosition(sf::Vector2f(float, float))`  (sets the sprite's absolute position w.r.t the window)
 * `sprite.move(sf::Vector2f(float, float))`   (moves the sprite from the current position by the given amount)
 * `sprite.setRotation(float)`   (sets the absolute orientation of the sprite)
 * `sprite.rotate(float)`   (rotates the sprite by the given angle w.r.t the current orientation)
 * `sprite.setScale(sf::Vector2f(float, float))`  (sets the absolute scale of the sprite)
 * `sprite.scale(sf::Vector2f(float, float))`   (scale the sprite by the given factor w.r.t the current scale)
 * `sprite.setOrigin(sf::Vector2f(float, float))`  (sets the origin respect to which the operations will be done on the sprite. The default origin is the top left corner)
<br/> 

 
