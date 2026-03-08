# {{PROBLEM}} Multi-Class Planned Design Recipe

## 1. Describe the Problem

_User Stories: Easy Mode_

>As a Maker
So that I can let people know what I am doing
I want to post a message (peep) to chitter

>As a maker
So that I can see what others are saying
I want to see all peeps in reverse chronological order

>As a Maker
So that I can better appreciate the context of a peep
I want to see the time at which it was made


Clarifying notes:

- I need to be able to create peep which includes date and time
- I need to see all peeps in newest first order
- I need to able to see date and time for every peep

_User Stories: Hard Mode_

>As a Maker
So that I can post messages on Chitter as me
I want to sign up for Chitter

>As a Maker
So that only I can post messages on Chitter as me
I want to log in to Chitter

>As a Maker
So that I can avoid others posting messages on Chitter as me
I want to log out of Chitter

_User Stories: Advanced Mode_

>As a Maker
So that I can stay constantly tapped in to the shouty box of Chitter
I want to receive an email if I am tagged in a Peep

## 2. Design the Class System

_Consider diagramming out the classes and their relationships. Take care to
focus on the details you see as important, not everything. The diagram below
uses asciiflow.com but you could also use excalidraw.com, draw.io, or miro.com_

```
┌────────────────────────────┐
│ PeepRepository             │
│                            │
│ - create(peep)             │
│ - fetch_all()              │
└───────────┬────────────────┘
            │
            │ owns a list of
            ▼
┌─────────────────────────┐
│ Peep(id, content, created_at)
│                         │
│ - id.                   │
| - content               |
| - created_at            |
│ - format()              │
│   => "Peep by Maker"    │
└─────────────────────────┘
```

_Also design the interface of each class in more detail._

```python
class PeepRepository:
    """
    Responsible for storing and retrieving Peeps from the database.
    """

    def __init__(self):
        pass  # No code here yet

    def create(self, peep):
        """
        Parameters:
            peep: an instance of Peep

        Behaviour:
            Inserts the peep into the database.

        SQL behaviour (conceptual):
            INSERT INTO peeps (content, created_at) VALUES ($1, $2);
        """
        pass  # No code here yet


    def all(self):
        """
        Parameters:
            None

        Returns:
            A list of Peep objects.

        Behaviour:
            Retrieves all peeps from the database in reverse
            chronological order (newest first).

        SQL behaviour (conceptual):
            SELECT id, content, created_at
            FROM peeps
            ORDER BY created_at DESC;
        """
        pass  # No code here yet


class Peep:
    # User-facing properties:
    #   id: string
    #   content: string
    #   created_at: string


    def __init__(self, id, content, created_at):
        # Parameters:
        #   id: int
        #   content: string
        #   created_at: tiemstamp
        # Side-effects:
        #   Sets the peep properties
        pass # No code here yet

    def format(self):
        """"""
        # Returns:
        #   A string of the form "Peep by Maker"
        pass # No code here yet

```
============= Worked Upto Here =============
## 3. Create Examples as Integration Tests

_Create examples of the classes being used together in different situations and
combinations that reflect the ways in which the system will be used._

```python
# EXAMPLE

"""
Given a library
When we add two tracks
We see those tracks reflected in the tracks list
"""
library = MusicLibrary()
track_1 = Track("Carte Blanche", "Veracocha")
track_2 = Track("Synaesthesia", "The Thrillseekers")
library.add(track_1)
library.add(track_2)
library.tracks # => [track_1, track_2]
```

## 4. Create Examples as Unit Tests

_Create examples, where appropriate, of the behaviour of each relevant class at
a more granular level of detail._

```python
# EXAMPLE

"""
Given a track with a title and an artist
We see the title reflected in the title property
"""
track = Track("Carte Blanche", "Veracocha")
track.title # => "Carte Blanche"
```

_Encode each example as a test. You can add to the above list as you go._

## 5. Implement the Behaviour

_After each test you write, follow the test-driving process of red, green,
refactor to implement the behaviour._