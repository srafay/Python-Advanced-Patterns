# Facade Design Pattern
* Facade design pattern provides a unified interface to a set of interfaces in a subsystem.
* It defines a higher-level interface that any subsystem can use.
* A facade class knows which subsystem is responsible for a request.

<p align="center"><img src="https://i.imgur.com/tB6LJ66.png" alt="Facade Design Pattern"></p>

```python
# facade.py

class SubsystemA:

	def method1(self):
		print('SubsystemA method1 ...')
		
	def method2(self):
		print('SubsystemA method2 ...')

class SubsystemB:
	
	def method1(self):
		print('SubsystemB method1 ...')
		
	def method2(self):
		print('SubsystemB method2 ...')

class Facade:

	def __init__(self):
		self._subsystem_A = SubsystemA()
		self._subsystem_B = SubsystemB()

	def method(self):
		self._subsystem_A.method1()
		self._subsystem_A.method2()
		
		self._subsystem_B.method1()
		self._subsystem_B.method2()

def main():
	facade = Facade()
	facade.method()

if __name__ == "__main__":
	main()
```