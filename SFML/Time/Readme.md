# Time in SFML (sf::Time)


Time - An SFML object to hold time values. Has member functions that allow the conversion of the value stored in the time container to uint/int/floats and then can be used with other c++ objects. Since its just a value, it can be negative too.

* Not a date time class i.e., does not represents current day/date/time etc
* SFML library does not impose any specific time unit, the choice rests with the user
* Represents a time-period or time interval b/w certain events. The interpretation rests with the user

### Member functions
* asMilliseconds() (returns int32 object)
* asMicroseconds() (returns int64 object)
* asSeconds() (returns float object)

### Related functions
* seconds (float) (returns Time object)
* milliseconds (int32) (returns Time object)
* microseconds (int64) (returns Time object)

Mostly will be used in conjuction with the sf::Clock object




