# Real time inputs (global inputs)

* As opposed to `sf::Events` the real time inputs can be use to query the global state of the keyboard/mouse/joystick
* While events are triggered when any of the key is pressed or cursor moves, real-time inputs can be checking if a certain key is pressed currently or not or where is the 
mouse pointer currently.
* For keyboard inputs, `sf::Keyboard` class can be used with its member function `isKeyPressed(sf::Keyboard::Key)`. As this function reads the state of the keyboard, it may return true even if the 
game window is out of focus.
  * `sf::Keyboard::isKeyPressed(sf::Keyboard::Key)`
* For mouse related inputs, `sf::Mouse` is used. It has member functions which allow to read the state of buttons and get or set the position (globally or w.r.t the window) 
of mouse pointer.
  * `sf::Mouse::isButtonPressed(sf::Mouse::Key)`
  * `sf::Mouse::getPosition(optional - sf::Window)`
  * `sf::Mouse::setPosition(sf::Vector2i(x, y), optional - sf::Window)`
* The `sf::Joystick` class can be used to access the joystcks' states. As joysticks are identified by their id, each function has the id/index as the first argument.
  * `sf::Joystick::isConnected(int)`
  * `sf::Joystick::getButtonCount(int)`
  * `sf::Joystick::hasAxis(int, sf::Joystick::Axis)`
  * `sf::Joystick::isButtonPressed(int id, int button)` (since buttons have no meaning, they are numbered from 0 to 31)
  * `sf::Joystick::getAxisPosition(int, sf::Joystick::Axis)`
