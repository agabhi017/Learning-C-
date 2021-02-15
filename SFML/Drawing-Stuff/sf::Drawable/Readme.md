## `sf::Drawable` 

* It is a very simple base class that allows to create inherited/derived classes to render objects to a target(window etc.)
* While `object.draw(window)` can be used directly to render objects, using `sf::Drawable` allows us to render objects using `window.draw(object)` and maintain the consistency
* It only contains virtual functions that need to be modified in the derived classes to draw the required object (virtual constructor and destructor)
* The constructor takes two arguments `sf::RenderTarget` and `sf::RenderStates`
  * `sf::RenderTarget` is the base class for `sf::RenderTexture` and `sf::RenderWindow`
  * `sf::RenderTexture` has similar functionality to that of `sf::RenderWindow`, the difference is that the result is stored in an off-screen texture rather than 
  being shown in a window.
  * Rendering to a texture can be useful in situation such as :
    * pre-computing complex textures
    * applying post-effects to the screen, etc
  * [`sf::RenderStates`](https://github.com/agabhi017/Learning-Cpp/tree/main/SFML/Drawing-Stuff/sf::RenderStates)
* It is the base class for multiple commonly used classes such as `sf::Sprite`, `sf::Shape`, `sf::Text`, `sf::VertexBuffer` etc


An example : (SFML documentation)
```
class MyDrawable : public sf::Drawable
{
public:
   ...
private:
    virtual void draw(sf::RenderTarget& target, sf::RenderStates states) const
    {
        // You can draw other high-level objects
        target.draw(m_sprite, states);
        // ... or use the low-level API
        states.texture = &m_texture;
        target.draw(m_vertices, states);
        // ... or draw with OpenGL directly
        glBegin(GL_QUADS);
        ...
        glEnd();
    }
    sf::Sprite m_sprite;
    sf::Texture m_texture;
    sf::VertexArray m_vertices;
};
```
* Calling `window.draw(MyDrawable object)` will be executed in the following manner :
  * Call to `sf::RenderTarget::draw` from the main game loop
  * Call to `drawable.draw` from the definition of `sf::RenderTarget::draw`. This will call the virtual function in the user defined class 
  dervied from the `sf::Drawable`
  * Call to `sf::RenderTarget::draw(const Vertex* vertices, ..)` from the virtual function definition
