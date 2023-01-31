202301271257
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]], [[ObservableList]], [[TableView]]


# Lecture 12 - ObservableList and TableViews II
- TableView and TableColumn
	- [[TableView]] - matrix, grid, spreadsheet. Just a basic table
		- work with ObservableList
		- [[TableColumn]] cells are assigned data from [[Object]] within ObservableList.
- [[TableView]] [[method]]
	- [[setItems()]]
		- tells the TableView where it is getting its data from.
		- Reference ObservableList it’s working with
	- [[setCellValueFactory()]]
		- called by [[TableColumn]] reference to assign Cell a value from the [[Object]] withing the [[ObservableList]]
		- accepts [[PropertyValueFactory< >()]] argument 
			- Call getters in [[Object]] that that [[TableView]] references.
## Programming Exercise 7-2
goal: prepopulate data in dog view.
- Dog Class
	- constructor data is what is going into TableView.
	- <mark style="background: #FFF3A3A6;">important</mark> <mark style="background: #D2B3FFA6;">excalidraw</mark> When we create a Dog [[Object]] we’re going to add that Dog Object to the `allAnimals` [[ObservableList]]. Then connect [[TableView]] with allAnimals [[ObservableList]].
- TableView and TableColumn references
	- [[Reference type]] cannot be [[primitive data type]], must be object.
syntax
```java
TableColumn<Data Class, Reference Type> colName;
```

<mark style="background: #ADCCFFA6;">code</mark>
```java
//DisplayAnimalsController.java
@FXML  
private TableView<Animal> animalTableView;

@FXML  
private TableColumn<Animal, Integer> PriceCol;  
  
@FXML  
private TableColumn<Animal, Integer> animalIdCol;  
  
@FXML  
private TableColumn<Animal, String> breedCol;  
  
@FXML  
private TableColumn<Animal, Integer> lifespanCol;
```
- [[initialize method]]
	- runs everytime scene is pulled.
	- Should exist in every controller to prevent memory leaks.
	- Goal: tell this TableView which [[ObservableList]] it is working with.
	- Animal Class as getter which will return ObservableList.
	- Call getAllAnimals() inside setItems() return ObservableList of Animal Objects. TableView will populate with that.
<mark style="background: #ADCCFFA6;">code</mark>
```java
// DisplayAnimalsController.java
animalTableView.setItems(DataProvider.getAllAnimals());
```
- animalTableView - Defined in `TableView<Animal> animalTableView;` in this Controller. 
- setItems() - called from [[TableView]].
- Arguments for setItems - `getAllAnimals()` called from [[DataProvider class]].
- Logic: our [[ObservableList]] is in the [[DataProvider class]]. In that class, there is a static [[getter]] which will return that ObservableList.
- Columns getting their data
	- Logic: getters and setters in animal class
		- we need to work with [[setCellValueFactory()]] and [[PropertyValueFactory< >()]]
<mark style="background: #ADCCFFA6;">code</mark>
```java
animalIdCol.setCellValueFactory(new PropertyValueFactory<>());
```
- (“id”) - whatever your field name is in the Animal getter must be passed into [[PropertyValueFactory< >()]]. So this statement is doing that.
- Entire Line: Gets the ID of Dog object and populate the cell.
- repeat for the rest of the columns.
<mark style="background: #ADCCFFA6;">code</mark>
```java
//Inside init method.
animalTableView.setItems(DataProvider.getAllAnimals());  
animalIdCol.setCellValueFactory(new PropertyValueFactory<>("id"));  
PriceCol.setCellValueFactory(new PropertyValueFactory<>("price"));  
breedCol.setCellValueFactory(new PropertyValueFactory<>("breed"));  
lifespanCol.setCellValueFactory(new PropertyValueFactory<>("lifespan"));
```
<mark style="background: #FFB86CA6;">question</mark>: why is the animalIDCol not change? Cause he dun fucked up lol. 

### Create Dog Objects and Populate them.
- where is the best place to put startupdata?
	- A method which only runs one time. I.E Main.
- Put test data in main
<mark style="background: #ADCCFFA6;">code</mark>
```java
//AnimalProgramApplication.java
Dog dog1 = new Dog(1, "Siberian Huskey", 15, "crafty", 599.99, true, "whistles");  
Dog dog2 = new Dog(2, "Saint Bernard", 12, "slow", 999.97, false, "cooks dinners with family");  
Dog dog3 = new Dog(3, "Dalmatian", 12, "energetic", 200.22, true, "Shoots lightning bolts through eyeballs." );  
Dog dog4 = new Dog(4, "Doge", 9999, "doge", 9999.99, false, "eternal god of internet memes.");  
Dog dog5 = new Dog(5, "Aussie", 13, "smarter than you probably", 450.08, true, "Will speak with Aussie accent, mate.");
```
- call DataProvider to add animals to TableView.
<mark style="background: #ADCCFFA6;">code</mark>
```java
// AnimalProgramApplication.java
DataProvider.addAnimal(dog1);
```

# References
