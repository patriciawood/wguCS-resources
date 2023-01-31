202301211615
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]]


# Lecture 5 - JavaFX Basics
- Overview
	- Understand JavaFX
	- Explore [[JavaFX]] lifecycle
- What is JavaFX
	- library used to make GUI. 
	- Supports FXML (similar to XML
	- JDK 7
	- and Model view)
- JFX Packages
	- elements in packages
	- start with javafx prefix.
- Stage and Scene Classes
	- Stage is container for scene
	- Scene container for JaFX UI controls (buttons, layouts etc.)
	- Must have at least one stage and one scene
- Nodes and Scene graphs
	- Node → element of a scene. Like a button.
		- Can have Group of node, child node, etc.
	- Node w/o children -0> leaf.
	- Root node - top level node. Only one doesn’t have parent.
	- Node diagram
		- ![[Pasted image 20230121161911.png]]
- Layouts
	- Used to arrange screen elements.
	- class examples AnchorPane, FlowPane, GridPane.
	- in javafx.scene.layout package
- Application Class and Life Cycle Method
	- <mark style="background: #FF5582A6;">important</mark>
		- Every java fx app is subclass of Application class.
	- Application class lives in javafx.application.
	- Application class defines 2 lifecycle methods
		- init()
			- Called when app is first launched.
			- intialize variables or set up default data.
			- Cannot be used to create stage or scene
			- Override
			- Does not need to be declared because already one created by default
			- <mark style="background: #FFB86CA6;">look into a bit more</mark>
		- start()
			- Called after init().
			- references Stage object as parameter. Stage is provided at runtime.
			- abstract method so must be overriden
		- stop()
			- Called when java app is closed. 
			- Use for cleanups
			- Optional declaration, does not have to be overriden.
	- Launching Jfx App
		- Launch() method
			- calls init() and start()
		- launch() returns when stop() is called
- Examples
	- ![[Pasted image 20230121164621.png]]
		- JavaFX template creates all the GUI stuff, just shows example of how to override the init() method.

# References
