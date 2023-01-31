202301301729
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]]


# Lecture 17 - Exceptions and Exception Handling
## Exceptions
- def: An error or unexpected event.
- it is an [[Object]]. 
### Handling
- def: detects errors and prevents them from crashing program.
- [[try block]] - throws exception.
- [[catch block]] = code that handles exception
	- As many catch block / try block
## Example
### Prevent Crashing on Empty Fields in Create Menu
- Step 1: Check your [[Debugger]] to find what exception is being thrown.
- Step 2: Find what method is throwing the exception.
- Step 3: Encasing with [[try block]]. ==Timestamp:== [[Lecture 17 video.mp4#t=08:01.166]]
```java
try
{
..// code block
}catch(){

}
```
- step 4: Catch statement
	- Indicate which [[Exception Object]] you are catching. (copy and paste exception from debugger).
	- Create [[parameter variable]] which will be a [[Reference]] to this [[Exception Object]].
		- typically `e`
```java
try
{
..// code block
}catch(ExceptionObject e){

}
```
- step 5: Decrypt
	- Replacing cryptic error codes with normal words.
	- We know that the error is caused from not putting text into the fields. So, we tell the user.
```java
}catch(ExceptionObject e){
	System.out.println("Please enter valid values in text fields.")
}
```
### Getting Info About the Exception
- ==Timestamp:== [[Lecture 17 video.mp4#t=14:22.764]]
- Let us know what the exception object says.
- [[Exception Object]] has different methods which can be used to clarify error message.
```java
}catch(ExceptionObject e){
	System.out.println("Please enter valid values in text fields.")
	System.out.println("Exception: " + e);
	System.out.println("Exception: ") + e.getMessage());
}
```

## Note on Logical Errors
- Exceptions are different than logical errors. Exceptions will break your program, logical errors will not.
# References
- [[Lecture 17 video.mp4]]
