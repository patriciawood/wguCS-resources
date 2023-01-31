202301281957
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]], [[ObservableList]], [[TableView]]

# Lecture 13 - ObservableList and TableView III
==I lost my project so just taking notes from here on out. No example to follow :(.==

## Wrapper Classes
- def: object equivalent to [[primitive data type]].
- Used to convert data types.
- valueof() - whatever you pass inside will be converted to data type selected at call. (ie `String.valueOf()` will convert input to String.)
- parseInt() and parseDouble() - convert Strings to int/double.
## ObservableArrayList() Methods
- add() - appends item to the end of ObservableList. Overloaded method.
- clear() - Removes all items in ObservableList.
- set() - Replaces specific item at index
- remove() - overloaded method. Removes specific item. Returns item removed or boolean.
- get() - returns item using index.

## Example - Create and Adding Objects to TableView
- Write the code for creating objects to *save handlers*. 
	- Clicking the save button let’s you save right? :P.
<mark style="background: #ADCCFFA6;">code</mark>
```java
// CreateAnimalMenuController.java
int id = animalIDtxt.getText(); // ID in Create Animal txt field.
```
- Will produce error because int != string. So add a wrapper class.
### Adding [[Wrapper Class]].
<mark style="background: #ADCCFFA6;">code</mark>
```java
// CreateAnimalMenuController.java
int id = Integer.parseInt(animalIDtxt.getText());
```

### Creating conditional statement for Radio Buttons
```Java
// CreateAnimalMenuController.java
if(vaccYesRbtn.isSelected()){
	isVaccinated = true;
else
	isVaccinated = false;
}
```
### Calling DataProvider
```java
// CreateAnimalMenuController.java
DataProvider.addAnimal(new Dog(id, breed, lifespan, behavior, price, vaccinated, special));
```
- Last piece is placing the back to main menu function.
- Without exception it will crash! 
## Searching for Data in TableView
- using [[enhanced for-loop]].
	- def: a loop that is used specifically for lists.
	- advantage we don’t have to know how many items are inside.
	- Step 1: an element variable
		- match type of what list you will be scanning through.
	- Step 2: Use getters to get Animal objects and 
	- Step 3: getter to find ID to compare.
	- Step 4: Add search to Initialize. For this example, search value is hard coded as `search(4)`.
<mark style="background: #ADCCFFA6;">code</mark>
```java
//DisplayAnimalController.java
public boolean search(int id){
	for(Animal dog : DataProvider.getAllAnimals()){ // Step 1 + 2.
		if(dog.getId() == id); // Step 3.
			return true;
		
	} 
	return false; // return false once loop returns true or ends.
}
```

> [!note]
> The logic here is pretty clear. You can use the [[enhanced for-loop]] for searching and filtering and pass the user input data using the `.getText` function for text fields.

## Code Reference
```java
// CreateAnimalMenuController.java
public class CreateAnimalMenuController implements Intitialize{
	int id = Integer.parseInt(animalIDtxt.getText());
	if(vaccYesRbtn.isSelected()){
	isVaccinated = true;
		else
		isVaccinated = false;
	}

	DataProvider.addAnimal(new Dog(id, breed, lifespan, behavior, price, vaccinated, special));
	
}
--
//DisplayAnimalController.java
public boolean search(int id){
	for(Animal dog : DataProvider.getAllAnimals()){ // Step 1 + 2.
		if(dog.getId() == id); // Step 3.
			return true;
		
	} 
	return false; // return false once loop returns true or ends.
}

```
# References
- [[13_Observable_List and_Table Views_III_0_HD_default.mp4]]

