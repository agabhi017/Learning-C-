# Texts and Fonts

* Fonts are loaded using `sf::Font` class. They can be loaded either from a file, from memory or from a custom input stream.
* Once fonts are loaded, text can be drawn using `sf::Text` class. Following are the member functions :
  * `text.setFont(sf::Font)`
  * `text.setString(std::string)`
  * `text.setCharacterSize(int)`
  * `text.setFillColor(sf::Color)`
  * `text.setStyle(sf::Text::Bold | sf::Text::Underlined)`
* The contents are then drawn on the window using `window.draw()` in the main loop b/w `window.clear()` and `window.display()`
