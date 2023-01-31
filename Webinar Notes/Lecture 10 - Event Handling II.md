202301241428
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]]


# Lecture 10: Event Handling II
- [[Toggle Groups]]
	- Only one raido button can be selected at a time.
	- Can be done in ``properties `` section in team builder.
- Project: Create Animal Menu Radio 
	- ![[Pasted image 20230124143218.png]]
		- Select both radio buttons
		- Navigate to properties
		- Name toggle group `vacTG`
- FXMLLoader
	- [[class]] provides [[members]] for working with [[Views]] and [[Controllers]].
	- [[load() method]] loads resources from proj. directory to app.
		- Overloaded method with variation that can accept name of FXML doc as string.
	- [[Casting]] used to determine [[datatype]] of [[Event Object]] when event is triggered.
		- Enables [[Event Object]] members be accessed in [[Event Handler]].
		- Basically, tells the [[Event Handler]] what kind of button is being pushed and where.
		- [thoughts:: Casting used a lot when working in widgets]
## Project: Working on Navigation
- Add stage and scene to `MainMenuController.java`
```java
Stage stage;
Scene scene;
```
- <mark style="background: #FFF3A3A6;">recall:</mark> stage and scene are containers which hold your fxml document.
- <mark style="background: #BBFABBA6;">logic:</mark> We want two pieces of information for [[casting]]. 
	1. [[Event Source]] that caused the event.
	2. Where is the button located.
		- We are adding a new scene to the stage.
<mark style="background: #ABF7F7A6;">code</mark>
```java
@FXML  
void onActionCreateAnimal(ActionEvent event) {  
  
    stage = ((Button)event.getSource())
```
- Let’s break it down
	- `onActionCreateAnimal()` is our create animal button. 
	- It takes the [[argument]] event which is of the `ActionEvent` [[datatype.]]
	- `stage` is defined as the `Stage` [[datatype]] in our [[class]] `MainMenuController`.
	- We are casting stage to the Button datatype w/ `(Button)`
	- `event.getSource()` is called from the `ActionEvent` class.
	- This is all encapsulated in outer parentheses.
- <mark style="background: #FF5582A6;">tldr;</mark> let’s [[Event Handler]] knows that the component that caused this event was a `Button`.
<mark style="background: #ABF7F7A6;">code: where is the button from?</mark>
```java
@FXML  
void onActionCreateAnimal(ActionEvent event) {  
  
    stage = ((Button)event.getSource()).getScene().getWindow();
```
- `getScene()` and `getWindow` from the `Button` class allow us to get the node or container where this element is from.
	- However, it’ll red flag because the [[Event Handler]] does not know that it is a `Stage` where this button came from.
	- Solution? Cast the entire statement into a stage.
<mark style="background: #ABF7F7A6;">code: casting back to stage</mark>
```java
stage = (Stage)((Button)event.getSource()).getScene().getWindow();
```
- #question is there a name for casting and then casting something back?
![[Casting in FXML Ecalidraw.png]]

## Project: Load Method
- loading the FXML document that creates the screen.
1. Write the `load()` function for the scene. Goes directly underneath `stage`.
```java 
scene = FXMLLoader.load();

```
- incomplete, still requires resource as [[argument]].
2. Two methods required. `getClass()` and `getResource()`. getClass() grabs our project while getResource() pulls the FXML document we need.
<mark style="background: #ABF7F7A6;">code: getClass</mark>
```java
scene = FXMLLoader.load(getClass().getResource(// FXML doc path goes here));
```
- Throws exception, which will be handled with clause.
- Use the lightbulb to create the i/o clause.
3. Now add scene to stage
<mark style="background: #ABF7F7A6;">code: add scene to stage</mark>
```java
stage.setScene(new Scene(scene));
```
- `stage` is an object created in the [[Stage Class]]. Of the class, there is a method called `setScene()` in which a new scene object can be defined. This scene object is our field `scene` which was defined above
4. Now to show the scene
<mark style="background: #ABF7F7A6;">code: show scene</mark>
```java
stage.show();
```

## Entire MainMenu Controller Codeblock 
```java
public class MainMenuController extends testingPrint {  
    Stage stage;  
    Parent scene;  
    @FXML  
    void onActionCreateAnimal(ActionEvent event) throws IOException {  
  
        stage = (Stage) ((Button)event.getSource()).getScene().getWindow();  
        scene = FXMLLoader.load(getClass().getResource("/mainMenu-view.fxml"));  
        stage.setScene(new Scene(scene));  
        stage.show();  
  
        // testPrint("OnActionCreateAnimal");  
    }
```

```ad-important
title: Best Practice
collapse: open
Best Practice: Place this into a method which accepts a string, the path for the FXML doc.

```

## After Creating onButtonPress Class
```java
// onButtonPress.
package pdugger.animalprogram;  

// Imports
import javafx.event.ActionEvent;  
import javafx.fxml.FXML;  
import javafx.fxml.FXMLLoader;  
import javafx.scene.Parent;  
import javafx.scene.Scene;  
import javafx.scene.control.Button;  
import javafx.stage.Stage;  
  
import java.io.IOException;  
  
public class onButtonPress {  
  
    ActionEvent event;  
    
  //Setter.
    public void setEvent(ActionEvent event){  
        this.event = event;  
    }  
	//showStage takes fxmlDoc path as argument.
    public void showStage(String fxmlDoc) throws IOException {  
        Parent scene;  
        Stage stage;  
  
        stage = (Stage) ((Button)this.event.getSource()).getScene().getWindow();  
  
    scene = FXMLLoader.load(getClass().getResource(fxmlDoc));  
        stage.setScene(new Scene(scene));  
        stage.show();  
    }  
}
```
- MainMenuController
```java
@FXML  
void onActionCreateAnimal(ActionEvent event) throws IOException {  
  
    String fxmlDoc = "CreateAnimalMenu-view.fxml";  
  
    setEvent(event);  
    showStage(fxmlDoc);  

}
```
# References
