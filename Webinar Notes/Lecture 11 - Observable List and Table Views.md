202301271221
202301191332
Status: #lecturenotes
Tags: [[computer science]], [[java]], [[C482]]


# Lecture 11 - Observable List and Table Views
- Comps
	- ObservableClass observalbeArray List
	- UI input
	- API TableView TableCol
- ObservableList
	- Class that works with [[JavaFX]] [[data structures]]
	- part of javafx.collections, inherits java.util.list
		- basically works like array list
- ObservableArrayList()
	- returns *object*
	- can be reference *by* ObservableList
- K9 UI UML
	- ![[Pasted image 20230127122952.png]]
	- DataProvider - holds our lists and data structures.
	- Animal - [[abstract class]].
	- dashed arrow - dependency
## Practice 7-1
- <mark style="background: #FF5582A6;">ArrayList in UML diagram replaced with ObservableList since it needs to be compatible with TableView.</mark>
-  Animal class
	-  Create constructors and setters and getters based UML.
<mark style="background: #ABF7F7A6;">code</mark>
```java
public abstract class Animal {  
  
    private int id;  
    private String breed;  
    private int lifespan;  
    private String behavior;  
    private double prive;  
    private boolean vaccinated;  
  
    // constructor  
    public Animal(int id, String breed, int lifespan, String behavior, double prive, boolean vaccinated) {  
        this.id = id;  
        this.breed = breed;  
        this.lifespan = lifespan;  
        this.behavior = behavior;  
        this.prive = prive;  
        this.vaccinated = vaccinated;  
    }  
  
    // setters and getters  
  
    public int getId() {  
        return id;  
    }  
  
    public void setId(int id) {  
        this.id = id;  
    }  
  
    public String getBreed() {  
        return breed;  
    }  
  
    public void setBreed(String breed) {  
        this.breed = breed;  
    }  
  
    public int getLifespan() {  
        return lifespan;  
    }  
  
    public void setLifespan(int lifespan) {  
        this.lifespan = lifespan;  
    }  
  
    public String getBehavior() {  
        return behavior;  
    }  
  
    public void setBehavior(String behavior) {  
        this.behavior = behavior;  
    }  
  
    public double getPrive() {  
        return prive;  
    }  
  
    public void setPrive(double prive) {  
        this.prive = prive;  
    }  
  
    public boolean isVaccinated() {  
        return vaccinated;  
    }  
  
    public void setVaccinated(boolean vaccinated) {  
        this.vaccinated = vaccinated;  
    }  
}
```
-  Dog Class
	- extends ANIMAL
	- super command must be at the top and inside b/c Animal has a constructor.
	- Create `String special`.
	- Append to Dog constructor and pass parameter to Dog class special field.
<mark style="background: #ABF7F7A6;">code</mark>
```java
public class Dog extends Animal{  
    private String special;  
  
    // super constructor  
    public Dog(int id, String breed, int lifespan, String behavior, double price, boolean vaccinated, String special) {  
        super(id, breed, lifespan, behavior, price, vaccinated);  
        this.special = special;  
    }  
  
    // setters and getters  
    public String getSpecial() {  
        return special;  
    }  
  
    public void setSpecial(String special) {  
        this.special = special;  
    }  
}
```

- Data Provider
	- I got pretty lost at this part because I don’t understand the array list thing much. here’s the code
<mark style="background: #ABF7F7A6;">code</mark>
```java
public class DataProvider {  
  
    private static ObservableList<Animal> allAnimals = FXCollections.observableArrayList();  
  
    public static void addAnimal(Animal animal){  
        allAnimals.add(animal);  
    }  
  
    public static ObservableList<Animal> getAllAnimals(){  
        return allAnimals;  
    }  
}
```
#needtoreview ObservableLists and ArrayLists.
# References
- [Lecture 11](https://wgu.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=058e6f9d-631b-4f38-9ed9-ab49011c71c4)
