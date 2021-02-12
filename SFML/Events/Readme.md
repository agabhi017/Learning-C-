# Events ( `sf::Event` )

* The event object captures any event (or user input) while the game window is open.
* The `sf::Event` is a `union` and hence only one of its members hold a valid value at a time and for correct usage one must refer to the appropraite members/functions of 
the given event type.
* The instances are filled by either the `pollEvent`or `waitEvent` function of the `sf::Window` class.

There can be following type of events :
* Window events :
  * `sf::Event::Closed` (if the user has attempted to close the game window)
  * `sf::Event::Resized`
    * `event.size.width`  `event.size.height`
  * `sf::Event::LostFocus` ()if the current window went out of focus i.e., the user moved to a different application window without closing the sfml window)
  * `sf::Event::GainedFocus`
<br/>

* Keyboard Events :
  * `sf::Event::TextEntered` (used when we need to capture the user input from a text box)
    * `event.text.unicode`
  * `sf::Event::KeyPressed` (should be avoided in case the objective is to read text input from the user)
    * `event.key.code`  (e.g. `sf::Keyboard::Escape`)
    * `event.key.control`  `event.key.alt`  `event.key.shift`  `event.key.system`
  * `sf::Event::KeyReleased` (to implement smooth movement in the case of long key presses, instead of relying on the OS to provide a delayed stream of inputs, once can use a boolean responding to keypressed and keyreleased events. That is start applying the action onc the key is pressed and stop applying it once it is released)
<br/>

* Mouse Events:
  * `sf::Event::MouseWheelMoved` (deprecated)
  * `sf::Event::MouseWheelScrolled`
    * `event.mouseWheelScroll.wheel` (orientation of the wheel (vertical/horizontal))
    * `event.mouseWheelScroll.delta` (the number of ticks the wheel has moved)
    * `event.mouseWheelScroll.x`  `event.mouseWheelScroll.y`  (current x & y of the mouse pointer)
  * `sf::Event::MouseButtonPressed`
    * `event.mouseButton.button` (e.g. `sf::Mouse::Right`)
    * `event.mouseButton.x`  `event.mouseButton.y`  (current x & y of the mouse pointer)
  * `sf::Event::MouseButtonReleased`
  * `sf::Event::MouseMoved`  (triggered when the mouse moves within the window; triggered even if the window isn't focused. However, it is triggered only when the mouse moves within the inner area of the window, not when it moves over the title bar or borders.)
    * `event.mouseMove.x`  `event.mouseMove.y`  (current x & y of the mouse pointer)
  * `sf::Event::MouseEntered`
  * `sf::Event::MouseLeft`  (triggered when the mouse cursor enters/leaves the window)
<br/>

* Joystick Events :
  * `sf::Event::JoystickButtonPressed` 
    * `event.joystickButton.joystickId`  `event.joystickButton.button`
  * `sf::Event::JoystickButtonReleased`
  * `sf::Event::JoystickMoved`
    * `event.joystickMove.axis`  `event.joystickMove.joystickId`  `event.joystickMove.position`
  * `sf::Event::JoystickConnected`
    * `event.joystickConnect.joystickId`
  * `sf::Event::JoystickDisconnected`
