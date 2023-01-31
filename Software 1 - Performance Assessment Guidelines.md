status: #PA
bucket: [[school]], [[computer science]]
tags: [[java]], [[0000 Zettlekasten/C482]]
# Requirements

***IDE***: Netbeans 11.1 (or exported to Netbeans 11.1)
***Software***: 
- JDK (v. LTS)
- JavaFX SDK or Module (v. LTS) – *for netbeans*
- Scene Builder
***Submission***:
- .zip file
- Folder w/ Javadoc comments in the .java files.
- Project file + folder structure intact.
- *zip from netbeans* – external zip will make file too large.
***Attachments:*** 
- [[Software 1 GUI Mockup.pdf]]
- [[Part.java]]
- [[UML Class Diagram-1.pdf]]

# Tasks

# I. UI
## GUI
> Create JavaFX app with GUI based on the mock-up. Use either FXML in JavaFX or Scene Builder. Do not use Swing.

### Include
- [ ] UI Components from Mock Up
- [ ] Each GUI mock up form
	- [ ] Main
	- [ ] Add Part
	- [ ] Modify Part
	- [ ] Add Product
	- [ ] Modify Product
- <mark style="background: #FF5582A6;">note:</mark> use 1 FXML file for forms with same UI comp. struct. Can use single window or new window.

## Comments
>Java doc comments for each classmember in code.

- Include 
	- [ ] Each class member - *start comments with RUNTIME ERROR or FUTURE ENHANCEMENT*
	- [ ] detailed description in comments
		- [ ] logic/runtime error that was corrected and how.
		- [ ] future enhancement that would extend functionality.
- <mark style="background: #FF5582A6;">note:</mark> Add logical + runtime error comments to method header declaration comments where error occured. Enhancement comments in comments of main class

# II. Application
## [[Mapping Classes]]
>create classes that map to UML class diagram. Include supplied Part class (part.java) without changing. 

- Classes include
	- [ ] inheritance
	- [ ] abstract and concrete classes
	- [ ] instance and static variables
	- [ ] instance and static methods

## Main Form – Feature Summary
- **Parts Pane**
	- [ ] Add
	- [ ] Modify
	- [ ] Delete
	- [ ] Full and partial search
	- [ ] Search empty == table repopulate
- **Product Pane**
	- [ ] Add
	- [ ] Modify
	- [ ] Delete
	- [ ] Full and partial search
	- [ ] Search empty == table repopulate
- **Exit Button**
	- [ ] Exits program

## [[Main Form]] Details
### [[Parts pane]]
- [ ] [[Add button]] => [[Add Part form]].
- [ ] [[Modify button]] => [[Modify Part form]].
- [ ] [[Delete button]] under the [[Parts TableView]] 
	- [ ] **Part Deleted** => deletes the selected part from the [[Parts TableView]]
	- [ ] [[Error Handling]] =>displays a descriptive error message in the UI or in a dialog box.
- [ ] [[Search Function]]
	- [ ] user searches for parts  
		- [ ] ID
		- [ ] name – partial or full 
		- [ ] Show results in [[Parts TableView]]
		- [ ] Including a search button is optional.
	- [ ] **Parts are found** => highlight a single part *or* filters multiple parts.
	- [ ] [[Error Handling]] => displays an error message in the UI or in a dialog box if part not found.
	- [ ] **Search field Empty** => table repopulates with all parts

### [[Products Pane]]
- [ ] [[Add button]] => [[Add Product Form]]
- [ ] [[Modify button]] => [[Modify Product Form]]
- [ ] [[Delete button]]
	- [ ] Deletes correct product from [[Product TableView]]
	- [ ] [[Error Handling]] => descriptive error message in UI or dialog box.
- [ ] [[Search Function]]
	- [ ] ID
	- [ ] name – partial or full
	- [ ] Search button - *optional*
	- [ ] Returns/Filters found products from [[Product TableView]].
	- [ ] [[Error Handling]] if product not found
	- [ ] Empty => table repopulates with products.

<mark style="background: #FF5582A6;">note:</mark>  Product’s associated parts *can exist* independent of currenty inventory. You do not need to provide sample data.

### [[Exit button]]
- [ ] [[Exit Button]] => closes program.

## [[Add Part Form]]
- [ ] [[In-House radio button]], [[Outsource Radio Button]] => switch bottom label
	- [ ] [[Machine ID]] label
	- [ ] [[Company Name]] label
- [ ] Auto-Generated [[unique part ids]]
	- [ ] [[part id text field]] disabled
- [ ] [[User Fields]]
	- [ ] part name
	- [ ] inventory level/stock
	- [ ] price
	- [ ] max/min values
	- [ ] company name/machine ID value
- [ ] After save => redirect to [[Main form]]
- [ ] Exit => redirect to [[Main Form]]

## [[Modify Part form]]
- [ ] [[text fields]] => populate data of chosen part.
- [ ] [[In-House radio button]], [[Outsource Radio Button]] => switch bottom label
- [ ] When new objects need to be created after the Save button is clicked, the part ID should be retained.
- [ ] The user can modify data values in the text fields sent from the Main form except the part ID. 
- [ ] After save => redirect to [[Main form]]
- [ ] Exit => redirect to [[Main Form]]

## [[Add Product Form]]
- [ ] [[In-House radio button]], [[Outsource Radio Button]] => switch bottom label
	- [ ] [[Machine ID]] label
	- [ ] [[Company Name]] label
- [ ] Auto-Generated [[unique part ids]]
	- [ ] [[part id text field]] disabled
- [ ] [[User Fields]]
	- [ ] Product name
	- [ ] inventory level/stock
	- [ ] price
	- [ ] max/min values
- [ ] [[Top Table]]
	- [ ] [[Part Search]]
		- [ ] by ID or name
		- [ ] found => highlightssingle part or filters multiple.
		- [ ] [[error handling]] => part not found, gives error.
		- [ ] empty => all parts shown
	- [ ] Same as [[Parts TableView]]
	- [ ] User Selects, then [[Add button]] => part copied to bottom table
- [ ] [[Bottom Table]] => associates part with product.
- [ ] [[Remove Associated Part Button]] => removes part from [[Bottom Table]]
- [ ] After save => redirect to [[Main form]]
- [ ] Exit => redirect to [[Main Form]]

_<mark style="background: #FF5582A6;">Note:</mark> When a product is deleted, so can its associated parts without affecting the part inventory. The Remove Associated Part button removes a selected part from the bottom table. (This dissociates or removes a part from a product.)_  

## [[Modify Product form]]
- [ ] [[text fields]] => populate data of chosen part.
- [ ] [[Top Table]]
	- [ ] [[Part Search]]
		- [ ] by ID or name
		- [ ] found => highlightssingle part or filters multiple.
		- [ ] [[error handling]] => part not found, gives error.
		- [ ] empty => all parts shown
	- [ ] Same as [[Parts TableView]]
	- [ ] User Selects, then [[Add button]] => part copied to bottom table
	- [ ] Assoc. 0, 1 or more parts w/ product
	- [ ] May remove part from product.
- [ ] [[Bottom Table]] => associates part with product.
- [ ] When new objects need to be created after the Save button is clicked, the part ID should be retained.
- [ ] The user can modify data values in the text fields sent from the Main form except the product ID. 
- [ ] After save => redirect to [[Main form]]
- [ ] Exit => redirect to [[Main Form]]

<mark style="background: #FF5582A6;">Note:</mark> The Remove Associated Part button removes a selected part from the bottom table. (This dissociates or removes a part from a product.)

## General [[Error Handling]]
- [ ] Descriptive error handling for input validation/logic checks
	- [ ] Min ≤ Inventory ≤ Max
	- [ ] Product != Delete if contains any part assoc.
	- [ ] Confirm delete and remove actions
	- [ ] No crash on bad data input, instead error messages
- [ ] Provide folder contain [[Javadoc]] files from IDE or command prompt made from [[Software 1 - Performance Assessment Guidelines#Mapping Classes]]