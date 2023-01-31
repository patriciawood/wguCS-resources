202301282044
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]]


# Lecture 14 - ObservableList and TableViews IV
## Update Object in TableView
- Using [[set()]] method for [[ObservableArrayList()]].
	- two parameters: ID, Animal Object.
- Step 1: define update function.
- Step 2: Using a counter variable to keep track of index.
- Step 3: Using [[enhanced for-loop]] (can probably be in function b/c similar to search().
- logic: Increment index and, every time an index is incremented, check if the inputted id matches the current dog object’s id. If it does, replace the animal at the index with the inputted vlaues.
- Step 4: Call update() to test it. 
```java
// DisplayAnimalController.java
public boolean update(int id, Animal animal){ // Step 1.

	int index = -1; // IRL, don't hard code this shit. Step 2

	for(Animal dog : DataProvider.getAllAnimals()){ // Step 3.
		index++;
		
		if(dog.getID() == id){
		DataProvider.getAllAnimals().set(index, animal);
		return true;
		}
	}
	return false;
}

if(update(5, new Dog("breed", 13, "Alert"))){ // Step 4.
	System.out.println("Update successful!")
else
	System.out.println("Update failed.")
}
```
## Removing Objects from TableView
- Using remove function. Runs same [[enhanced for-loop]]. If the dog ID matches, remove the dog. 
- <mark style="background: #FF5582A6;">note</mark> I used the `id` variable in a statement outside of the class. Obviously, **this would not work unless id is defined elsewhere**. Decided to do that so the number was not hardcoded in.
```java

// DisplayAnimalController.java
public boolean delete(int id){
	for(Animal dog : DataProvider.getAllAnimals()){
		if(dog.getID() == id){
			return DataProvider.getAllAnimals().remove(dog);
		}
		return false;
	}
}

if(delete(id)){
	System.out.println(id + "Dog deleted!");
else
	System.out.println("Dog not found.")
}
```


# References
- [[14_Observable_List and_Table Views_IV_0_HD_default.mp4]]