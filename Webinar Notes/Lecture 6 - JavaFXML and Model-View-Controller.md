202301211653
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]]


# Lecture 6 - JavaFXML and Model-View-Controller
- Overview
	- Understand
	- Create App
	- Create views/controllers
- What is
	- Markup language used to make GUIs.
	- Based off XML.
- Benefits over JavaFX
	- [[JavaFXML]] not complied (thank god)
	- No coding! - Use a GUI to make GUIs :P.
	- Utilizes model-view-controller
	- If it is static UI, JavaFXML pog. If dynamic, JavaFX.
- Model-View-Controller (MVC)
	- programming Design Architevture representing visual components
		- seperate packages
	- model package → contains Classes with data and logic.
	- view → files that markup UI
	- controller → Classes for user interaction with UI (aka [[event handling]]) data flow, transfer, and other controllers.
- Exercise 1
	- The lecture derailed into netbeans so I used [Creating A Java FX Project In IntelliJ (07-22-2022)](https://wgu.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=4187aa88-7e14-4857-8332-aeda00f61fa1). Here is the example/info from that.
	- ![[Pasted image 20230121185317.png]]
		- fxid in SceneBuilder plugin in the view fxml file.
	- ![[Pasted image 20230121185411.png]]
		- Visible in HelloController code.
	- ![[Pasted image 20230121185549.png]]
		- Add println to debug.
	- Workflow
		- Create fxml file in Intellij. 
		- Create controller
		- Add controller to fxml file.
		- Create gui container, label, and button in SceneBuilder.
		- Give action or fxid in code section
		- Go to fxml file, right click and add to the controller.
		- Code the controller.
# References
 [lecture 6](https://wgu.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=a7dcedbe-0731-45e2-b55b-ab4901528593)
 [Creating A Java FX Project In IntelliJ (07-22-2022)](https://wgu.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=4187aa88-7e14-4857-8332-aeda00f61fa1)