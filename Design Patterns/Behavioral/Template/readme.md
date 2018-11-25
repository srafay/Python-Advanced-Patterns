# Template Design Pattern
* Template method design pattern is to define an algorithm as skeleton of operations
    * and leave the details to be implemented by the child classes.
* The overall structure and sequence of the algorithm is preserved by the parent class.
* Template means Preset format like HTML templates which has fixed preset format.
* Similarly in template method pattern,we have a preset structure method called template method which consists of steps.
    * This steps can be abstract method which will be implemented by its subclasses.
* This behavioral design pattern is one of the easiest to understand and implement.
    * This design pattern is used popularly in framework development.
    * This helps to avoid code duplication also.

<p align="center"><img src="https://i.imgur.com/KQ1yNwW.png" alt="Facade Design Pattern"></p>

```python
# template.py

import sys

from abc import ABC, abstractmethod

class AbstractClass(ABC):
#This class inherit from Abstract Base Class to allow the use of the @abstractmethod decorator
    
	def template_method(self):
		"""Ths is the template method that contains a collection of 
		methods to stay the same, to be overriden, and to be overriden optionally.
		"""

		self.__always_do_this()
		self.do_step_1()
		self.do_step_2()
		self.do_this_or()

	def __always_do_this(self):
		#This is a protected method that should not be overriden.

		# Determine the name of the current function
		name = sys._getframe().f_code.co_name
		print('{}.{}'.format(self.__class__.__name__, name))

	@abstractmethod
	def do_step_1(self):
		#This method should be overriden
		pass

	@abstractmethod
	def do_step_2(self):
		#This method should be overriden
		pass

	def do_this_or(self):
		print('You can overide me but you do not have to')

class ConcreteClassA(AbstractClass):
#This class inherits from the Abstract class featuring the template method. 

	def do_step_1(self):
		print('Doing step 1 for ConcreteClassA ...')

	def do_step_2(self):
		print('Doing step 2 for ConcreteClassA ...')

class ConcreteClassB(AbstractClass):
#This class inherits from the Abstract class featuring the template method.

	def do_step_1(self):
		print('Doing step 1 for ConcreteClassB ...')

	def do_step_2(self):
		print('Doing step 2 for ConcreteClassB ...')

	def do_this_or(self):
		print('Doing my own business ...')

def main():
	print('==ConcreteClassA==')
	a = ConcreteClassA()
	a.template_method()

	print('==ConcreteClassB==')
	b = ConcreteClassB()
	b.template_method()

if __name__ == '__main__':
	main()
```