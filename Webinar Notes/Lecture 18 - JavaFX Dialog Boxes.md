202301301751
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]]


# Lecture 18 - JavaFX Dialog Boxes
## Alert Class
- Used for creating/working w/ Dialog Boxes
- [[Dialog Boxes]] created by [[instantiating]] the [[Alert Class]].
- Uses `AlertType` enum.
### methods
- [[Alert.setTitle()]]
- [[Alert.setContentText()]]
- [[Alert.showAndWait()]]
### box types
- [[error dialog]] - `Alert.AlertType.error` can only hit ok or close.
- [[warning dialog]] - `Alert.AlertType.warning` same as error dialog, just includes graphic.
- [[confirmation dialog]] - `Alert.AlertType.confirmation` has two buttons, like the user can save or cancel etc.
## Dialog Boxes in JavaFX
- modality - you can’t interact with the program with the dialog box active.

## Programming Exercise
### Set Up Error Dialog Box
```java
}catch(ExceptionObject e){
	Alert alert = new Alert(Alert.AlertType.error);
	alert.setTitle("Error Dialog");
	alert.setContentText("Please enter valid value for each text field");
	alert.showAndWait();
}
```

### Warning Dialog Box
- Literally the same, but here’s the code…
```java
}catch(ExceptionObject e){
	Alert alert = new Alert(Alert.AlertType.WARNING);
	alert.setTitle("Error Dialog");
	alert.setContentText("Please enter valid value for each text field");
	alert.showAndWait();
}
```
- The only difference is the warning has a yellow caution sign.

### Confirmation Dialog
- Making the user has a chance to save before they hit back.
- Goes in `back button` event handler.
- Use correct Alert [[overloader]].
```java
Alert alert = new Alert(Alert.AlertType.CONFIRMATION, "This will clear all your work! Do you want to continue?");
```
#### Creating [[Optional Container]]
- Use result to figure out what the user clicked.
```java
Alert alert = new Alert(Alert.AlertType.CONFIRMATION, "This will clear all your work! Do you want to continue?");

Optional<ButtonType> result = alert.showAndWait();
if(result.isPresent() && result.get() == ButtonType.OK){
	// Scene and Stage goes here.
}
```
# References
- [[Lecture 18 video.mp4]]