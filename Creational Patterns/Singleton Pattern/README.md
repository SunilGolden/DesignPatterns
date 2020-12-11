# Singleton Pattern

![Diagram of Singleton Pattern](https://www.tutorialspoint.com/design_pattern/images/singleton_pattern_uml_diagram.jpg)

### SingleObject.java 

```java
public class SingleObject {
	// Create an object of SingleObject
	private static SingleObject instance = new SingleObject();

	// Make the constructor private so that this class cannot be instantiated
	private SingleObject(){}

	// Get the only object available
	public static SingleObject getInstance() {
		return instance;
	}

	public void showMessage() {
		System.out.println("Hello from the one-and-only object.");
	}
}
```

### SingletonPatternDemo.java 

```java
public class SingletonPatternDemo {
	public static void main(String[] args) {

		/*
		* Illegal construct
		* Compile Time Error: The constructor SingleObject() is not visible
		* SingleObject object = new SingleObject();
		*/

		// Get the only object available
		SingleObject object = SingleObject.getInstance();

		// Show the message
		object.showMessage();
	}
}
```