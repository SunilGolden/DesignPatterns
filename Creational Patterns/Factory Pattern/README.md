# Factory Pattern

![Diagram of Factory Pattern](https://www.tutorialspoint.com/design_pattern/images/factory_pattern_uml_diagram.jpg)

### Shape.java

```java
public interface Shape {
	void draw();
}
```

### Rectangle.java

```java
public class Rectangle implements Shape {

	@Override
	public void draw() {
		System.out.println("Drawing rectangle ...");
	}
}
```

### Square.java 

```java
public class Square implements Shape {

	@Override
	public void draw() {
		System.out.println("Drawing square ...");
	}
}
```

### Circle.java 

```java
public class Circle implements Shape {

	@Override
	public void draw() {
		System.out.println("Drawing circle ...");
	}
}
```

### ShapeFactory.java

```java
public class ShapeFactory {
	
	public Shape getShape(String shapeType) {
		if (shapeType == null){
			return null;
		}		
		if (shapeType.equalsIgnoreCase("CIRCLE")) {
			return new Circle(); 
		}
		else if shapeType.equalsIgnoreCase("RECTANGLE")) {
			return new Rectangle(); 
		}
		else if shapeType.equalsIgnoreCase("SQUARE")) {
			return new Square();
		}
		
		return null;
	}
}
```

### FactoryPatternDemo.java

```java
public class FactoryPatternDemo {

	public static void main(String[] args) {
    	ShapeFactory shapeFactory = new ShapeFactory();

    	// Get an object of Circle and call its draw method.
    	Shape shape1 = shapeFactory.getShape("CIRCLE");

    	// Call draw method of Circle
      	shape1.draw();

      	// Get an object of Rectangle and call its draw method.
      	Shape shape2 = shapeFactory.getShape("RECTANGLE");

      	// Call draw method of Rectangle
      	shape2.draw();

      	// Get an object of Square and call its draw method.
      	Shape shape3 = shapeFactory.getShape("SQUARE");

      	// Call draw method of square
      	shape3.draw();
	}
}
```