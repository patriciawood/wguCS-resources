202301211513
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[0000 Zettlekasten/C482]]


# Lecture 4: Methods + Object Oriented programming II
- The ```this``` and super keywords
	- this → instance of a class, used to access instance members.
	- both can access protected/public members of *superclass* within subclass.
	- <mark style="background: #FF5582A6;">note:</mark> super keyword is not super().
	- this
		- handles shadowing
			- shadowing: parameter variable name matches name of instance variable.
		- this cannot be applied to class variables or static members.
		- Programming exercise.
	- Super
- Programming Exercise
	- ![[Pasted image 20230121152152.png]]
		super allows calling setBreed() from Animal class (the superclass).
	- ![[InkedPasted image 20230121152309 1.jpg]]
	- this allows change field.
- Overloading
	- Create methods/constructors, same name dif signatures.
	- ex: One setSound(), one setSound(String sound). Have different parameters
- Abstract Classes
	- Cannot be [[instantiation]] (create objects). 
	- Can only *inherit* protected and public members.
	- Marked by abstract
	- UML: italics
	- Program Exercise 2
		- ![[Pasted image 20230121152916.png]]
- [[Casting]]
	
- Static Member
	- Belongs to class
	- can be shared by Instance members
	- Objects share the data, but static members belongs to class only.
	- Rules
		- Can only call static members
		- can only be called within static body **check on this**
- Instance Member
	- Non-static member
	- Only belongs to objects
	- cannot be shared
	- Can call static or instance members
	- can be called within instance or static members
	- To call instance member must have an object to call it
- UML: Static is underlined, instance is not underlined.
- Exercise 
	- ![[Pasted image 20230121160418.png]]
	-  ![[Pasted image 20230121160505.png]]   
		- Go to main, clear everything out.
	- ![[Pasted image 20230121161130.png]]
		- Because getSeller() is a static field in the Animal superclass, it is able to be called by Animal.getSeller() or by the object dog1 with dog1.getSeller().

# References
