202301301101
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]]


# Lecture 15 - ObservableList and TableView V
## [[TableView]] Members
- [[getSelectionModel()]] - returns selection model object. Single and Multi.
- [[getSelectedIndex()]] - returns index of whatever row is selected in TableView.
- select() - selects row in TableView
## Selecting + Filtering Items in TableView
- [[lecture 15 video.mp4#t=04:16.315]]
### Returning ID 
- [[lecture 15 video.mp4#t=05:11.240]]
- <mark style="background: #ADCCFFA6;">idea</mark>: Again looking very similar to previous [[enhanced for-loop]]. fIND THE ID, RETURN OBJECT OR RETURN NULL.
```java
public Animal selectAnimal(int id){
	for(Animal dog : DataProvider.getAllAnimals()){
		if(dog.getId() == id)
			return dog;
	}
	return null; //This is the only difference...
}
```
### Using select methods
[[lecture 15 video.mp4#t=08:41.616]]
```java
animalTableView.getSelectionmodel().select(selectAnimal(id)); //Selects one by default.
```

![[Lecture 15 - ObservableList and TableView V 2023-01-30 11.48.46.excalidraw]]
- Useful for searching IDs, but can cause problems if too many arguments.
### Filtering
- Go into DataProvider create an ObservableList which holds filtered objects.
	- <mark style="background: #ADCCFFA6;">idea</mark>: Again, this may be a situation where the ObservableList could be a method, called by `allAnimals` and `filteredAnimals`. Same for getter.
[[lecture 15 video.mp4#t=14:39.895]]
```java
// DataProvider.java
private static ObservableList<Animal> allAnimals = FXCollections.obse
private static ObservableList<Animal> filteredAnimals = FXCollections.observableArrayList();

// getter
public static ObservableList<Animal> getFilteredAnimals(){ 
	return filteredAnimals;
}
```
#### Adding Filter method
- [[lecture 15 video.mp4#t=18:06.385]]
	- <mark style="background: #FFB86CA6;">logic</mark>:Pass in string, scan through the *original* list of dogs. Check to see if any breed names match the text placed here.
- [[Contains method]]: string method that checks if a string contains a sub string.

```java
// DisplayAnimalController.java
public ObservableList<Animal> filter (String breed){
	for(Animal dog : DataProvider.getAllAnimals()){
		if(dog.getBreed().contains(breed)){
			DataProvider.getAllFilteredAnimals().add(dog);
		}
	}
	return DataProvider.getAllFilteredAnimals();
}
```

#### Visual BreakDown
![[Lecture 15 - ObservableList and TableView V 2023-01-30 12.36.25.excalidraw]]

#### Where to call filter
- Recall animalTableView used the [[setItems()]] method to include objects in TableView. Now, we are going to use our filter method instead.
	- [[lecture 15 video.mp4#t=23:47.538]]
- User input variable should not be hardcoded tbh.
```java
// DataProvider.java
animalTableView.setItems(filter("User Input Variable"))
```
- From here, we’ll get repeated data! We have to include a if statement to clear the filter using [[ifEmpty()]] and [[clear()]] methods.
```java
// DisplayAnimalController.java
public ObservableList<Animal> filter (String breed){
	if(!(DataProvider.getAllFilteredAnimals().isEmpty())){ // Checks if filter table is empty
		DataProvider.getAllFilteredAnimals().clear();
	} // If-statement which clears the filter.
	
	for(Animal dog : DataProvider.getAllAnimals()){
		if(dog.getBreed().contains(breed)){
			DataProvider.getAllFilteredAnimals().add(dog);
		}
	}
	
	return DataProvider.getAllFilteredAnimals();
}
```
### Switching Between Filter and Original Table
- [[lecture 15 video.mp4#t=32:12.703]]
- if animal does not exist, return the entire table.
```java
// DisplayAnimalController.java
public ObservableList<Animal> filter (String breed){
	if(!(DataProvider.getAllFilteredAnimals().isEmpty())){
		DataProvider.getAllFilteredAnimals().clear();
	} 
	
	for(Animal dog : DataProvider.getAllAnimals()){
		if(dog.getBreed().contains(breed)){
			DataProvider.getAllFilteredAnimals().add(dog);
		}
	}
// Alter return statement to return full table if filter returns nothing.
	if(DataProvider.getAllFilteredAnimals().isEmpty()) 
		return DataProvider.getAllAnimals();
	else 
		return DataProvider.getAllFilteredAnimals();
}
```
# References
- [[lecture 15 video.mp4]]