# SFML Window ( `sf::Window` )

The Window class just handles the window in which the user can draw/create stuff.

* It takes 2 main arguments and 2 optional arguments, the 2nd main is kinda optional too. 
* The first argument is the size of the window and is set by using `sf::VideoMode(a,b)`.
* The second argument is the title/name of the window that will appear on the screen.
* The next is an optional `Style` argument. It allows to make changes to the window such as resizing/titlebar/full screen mode etc.
* The last optional argument defines OpenGL specific options.
* `Never use both setVerticalSyncEnabled and setFramerateLimit at the same time! They would badly mix and make things worse.`

### Key member functions
* `window.pollEvent(sf::Event event)` (boolean, returns true if any event is pending to be processed)
* `window.isOpen()`
* `window.Close()`
* `window.setPosition(sf::Vector2i(a, b))`
* `window.setSize(sf::Vector2u(a, b))`
* `window.getSize()` (returns a `sf::Vector2u`)
* `window.setTitle()`
