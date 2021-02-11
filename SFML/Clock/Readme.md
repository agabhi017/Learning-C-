# SFML Clock (sf::Clock)

* Clock is a simple class that measures time b/w the events whenever it is triggered. It has 2 simple member functions that return the elapsed time and reset the
clock counter.
* According to SFML docuemntation - sf::Clock is a lightweight class and provides the most precise time that the uinderlying OS can achieve.

### Member Functions:
* getElapsedTime() (returns a Time object)
* restart() (returns a Time object) (also returns the elapsed time and can be used to avoid the slight gap b/w function calls to getElapsedTime() and then reset())



