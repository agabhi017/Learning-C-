# Drawing 2D stuff using SFML

* `sf::RenderWindow` class is used for drawing entities in a window. This class is derived from the `sf::Window` class and inherits all its functions and has other 
high level functions to ease out the drawing porcedure. 
* The typical drawing cycle consists of `clear`, `draw` and `display` steps. 
* `clear` is used to clear out the stuff displayed on the window in the previous frame and fill it with a certain colour (for example `window.clear(sf::Color::Black)`)
* `clear` is recommended to avoid any overlap or undesired behavior due to the interference of graphics from 2 consecutive frames.
* `draw` function is used for drawing stuff on the window. The stuff is not drawn directly on the window but on a buffer.
* The `display()` function is used to display the contents of the buffer on the window. This is called double buffering.
