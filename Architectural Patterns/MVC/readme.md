# Model View Controller (MVC)
* Model View Controller is the most commonly used design pattern. Developers find it easy to implement this design pattern.
* Following is a basic architecture of the Model View Controller

<p align="center"><img src="https://i.imgur.com/TcRtP6U.jpg" alt="MVC Architecture"></p>

## Model
* It consists of pure application logic, which interacts with the database. It includes all the information to represent data to the end user.

## View
* View represents the HTML files, which interact with the end user. It represents the model’s data to user.

## Controller
* It acts as an intermediary between view and model. It listens to the events triggered by view and queries model for the same.

```python
# model.py

import json

class Person:
   def __init__(self, first_name = None, last_name = None):
      self.first_name = first_name
      self.last_name = last_name
   #returns Person name, ex: John Doe
   def name(self):
      return ("%s %s" % (self.first_name,self.last_name))
		
   @classmethod
   #returns all people inside db.txt as list of Person objects
   def getAll(cls):
      database = open('db.txt', 'r')
      result = []
      json_list = json.loads(database.read())
      for item in json_list:
         item = json.loads(item)
         person = Person(item['first_name'], item['last_name'])
         result.append(person)
      return result
```

```python
# view.py

from model import Person

def showAllView(list):
   print 'In our db we have %i users. Here they are:' % len(list)
   for item in list:
      print item.name()
def startView():
   print 'MVC - the simplest example'
   print 'Do you want to see everyone in my db?[y/n]'
def endView():
   print 'Goodbye!'
```

```python
# controller.py

from model import Person
import view

def showAll():
   #gets list of all Person objects
   people_in_db = Person.getAll()
   #calls view
   return view.showAllView(people_in_db)

def start():
   view.startView()
   input = raw_input()
   if input == 'y':
      return showAll()
   else:
      return view.endView()

if __name__ == "__main__":
   #running controller function
   start()
```