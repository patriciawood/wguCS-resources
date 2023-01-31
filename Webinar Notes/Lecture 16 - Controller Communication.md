202301301313
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]]


# Lecture 16 - Controller Communication
## Overview
- More [[FXML Loaders]].
- Transfer Object between Controllers and access Object Data.
### Overview Visual
![[Lecture 16 - Controller Communication 2023-01-30 15.15.13.excalidraw]]
## FXML Loaders
### [[setLocation()]]
- specify path of resource.
- [[instance method]], must create an object.
- Make FXMLloader object → use setLocation()

### [[getControllers]]
- returns instance of Controller and associated [[FXML Doc]]
- getRoot() <mark style="background: #FF5582A6;">fill in</mark>
## Programming Example - Animal Details Screen
- goal: when you select records in DisplayAnimalController shows details of that dog in DetailController.
- step 1: Create FXML object
- step 2: reducing scene to setLocation().
```java
// DisplayAnimalController.java

void OnActionDisplayAnimalDetailsMenu(ActionEvent event) throws IOException {
	// Step 1
	FXMLLoader loader = new FXMLLoader(); 
	// Step 2
	loader.SetLocation(getClass().getResource("view path here")););")
	loader.load();
	// Step 5
	AnimalDetailsController ADController = loader.getController();
	// Step 6
	ADController.sendAnimal(AnimalTableView).getSelectionModel().getSelectedItem();

	/* old
	stage = (Stage) ((Button) event.getSource().getScene().getWindow();)
	scene = FXMLLoader.load(.getClass().getResource("view path here"));
	stage.getScene(new Scene(scene));
	stage.show();

}
```
### Defining Method in Animal Details Controller
- [[Lecture 16 video.mp4#t=12:12.422]]
- Method will accept object that we want to retrieve data from.
	- When it is called, it will recieve passed in reference of dog object. Animal is the [[superclass]] it is the reference type.
- Step 3: Change the labels.
	- References to labels are in DisplayAnimalController already.
- Step 4: Red Flag! We are setting label (which only accepts strings) with an int. Have to cast to change data type.
	- <mark style="background: #ADCCFFA6;">idea:</mark> Instead of copying and pasting for each label, we can make a function.
- Step 5: Create an instance of the controller.
	- recall: we created loader object and told it what view to use. Now we are letting it know what controller to use.
```java
// AnimalDetailsController.java

// Step 3
public void sendAnimal(Animal dog){
// Step 4
	animalIDlbl.setText(string.valueOf(dog.getID()));
}
```
- Step 6: Using select method to return from the TableView which 
	- `sendAnimal()` expecting and *animal* object.
	- In order to find the correct animal which was selected in the TableView, we use getSelectedItem() method.
- Step 7: revive the old code.
	- Call the instance of the FXML loader we created, `loader`.
	- Call [[getRoot()]]
- Step 8: Show and wait
	- All code after show and wait will only be executed when you switch screens or close window. Better practice to use show and wait. Unfortunately this throws an error, so just use `show` lol.
```java
// DisplayAnimalController.java

void OnActionDisplayAnimalDetailsMenu(ActionEvent event) throws IOException {
	// Step 1
	FXMLLoader loader = new FXMLLoader(); 
	// Step 2
	loader.SetLocation(getClass().getResource("view path here")););")
	loader.load();
	// Step 5
	AnimalDetailsController ADController = loader.getController();
	// Step 6
	ADController.sendAnimal(AnimalTableView).getSelectionModel().getSelectedItem();

	
	stage = (Stage) ((Button) event.getSource().getScene().getWindow();)
	// Step 7
	scene = loader.getRoot();
	stage.getScene(new Scene(scene));
	// Step 8
	stage.show();

}
```
- Step 9: Repeat step 4 for the rest of the labels in the Detail controller.
	- <mark style="background: #FF5582A6;">note:</mark> use [[if-statement]] for radio buttons, return yes and no strings.
## Notes on Super/Sub Classes
- Animal is [[superclass]], Dog [[subclass]]. Inheritance does *not* work in reverse.
	- Cannot call setSpecial or getSpecial in Animal class, which is what we use in the Details menu.
	- Solution? [[Casting]].
### Dealing with different types of animals
- ==TS:== [[Lecture 16 video.mp4#t=36:30.068]]
- [[instanceof]] - useful if you have different animal types. Confirms the type of object we are dealing with.
	- exposed the reference as a subclass. 
- Step 1: Gain access to special field for all types of animals using [[instanceof]].
- Step 2: Use casting to gain access to Dog [[subclass]].
	- <mark style="background: #FF5582A6;">useful!</mark> [[Casting]] Logic 
		1. Write subclass casting to.
		2. Type reference.
		3. Wrap both in ().
		4. Subclass methods will be visible.
	- Obviously include other animals as if statements.
```java
// AnimalDetailsController.java
public void sendAnimal(Animal dog){
	..
	if(dog instanceof Dog)
		speciallbl.setText(((Dog) dog).getSpecial()));
		
}
```

# References
- [[Lecture 16 video.mp4]]