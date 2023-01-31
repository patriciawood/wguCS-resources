202301231401
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]], [[event handling]]
# Lecture 9 - JavaFXML Event Handling I


- FXIDs
	- unique identifier. referencing ui control in Controller
	- assign value in SceneBuilder or in FXML markup
- @FXML
	- Ensures following field matches the FXID.
	- Includes
		- private access specifider
		- UI control reference type
		- reference variable
- Project: Create IDs
	- Open ```createanimals.fxml
	- Set IDs in code section of text fields.
		- EX: animal field given ``animalIDTxt
		- ![[Pasted image 20230123140707.png]]
	- Continue on to ``animalDetailsMenu.fxml
		- Interactive or non-static elements will get ids. So, in this menu, the labels which will populate with information about certain animals.
	- <mark style="background: #FF5582A6;">note:</mark> naming convention is camelCase with data type at the end ie ``animalIdTxt
	- Finish the last menus
- Project: Adding FXML annotations
	- Start with controllers
	- ![[Pasted image 20230123141739.png]]
		- Go into scenebuilder and copy and paste controller skeleton into ``CreateAnimalMenuController.java
			- Import classes from ``CreateAnimalMenu-view.FXML
			- ![[Pasted image 20230123142016.png]]
- Event Handling
	- [[Event Source]] -> ui controls, radio buttons, buttons, etc.
	- [[Event Object]] -> contains info *about* the event. Created when event is triggered.
	- [[Listeners]] -> a *class* contains one or more methods that respond to events.
	- [[Event Handler]] -> method that executes when event occurs.
- Project: Adding events to Main Menu.
	- Open ``mainMenu.fxml`` in SceneBuilder.
	- ![[Pasted image 20230123143222.png]]
		- naming convension: eventHandlerMethodCalled
	- Copy skeleton into controller again.
		- ![[Pasted image 20230123143417.png]]
	- Repeat for others button in project.
- Project: testing
	- Created a testing class with a print function
		- ![[Pasted image 20230123145720.png]]
	- Then extended this class to all the controllers
		- ![[Pasted image 20230123145742.png]]
	- Ran the `testPrint()` function in each onAction function
		- ![[Pasted image 20230123145832.png]]
	- This way I can change `testPrint()` to check any variables I need later on. I'd like to make it dynmaically fill as well, but that's a bit beyond me atm ^^;.
	- Result
		- ![[Pasted image 20230123150017.png]]
		- Returns confirmation to the console.
# References
