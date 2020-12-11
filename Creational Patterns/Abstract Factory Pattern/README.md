# Abstract Factory Pattern

![Diagram of Abstract Factory Pattern](https://www.tutorialspoint.com/design_pattern/images/abstractfactory_pattern_uml_diagram.jpg)

### Shape.java

```java
public interface Shape {
	void draw();
}
```

### RoundedRectangle.java

```java
public class RoundedRectangle implements Shape {
	@Override
	public void draw() {
		System.out.println("Drawing rounded rectangle ...");
	}
}
```

### RoundedSquare.java 

```java
public class RoundedSquare implements Shape {
	@Override
	public void draw() {
		System.out.println("Drawing rounded square ...");
	}
}
```

### Rectangle.java 

```java
public class Rectangle implements Shape {
	@Override
	public void draw() {
		System.out.println("Inside Rectangle::draw() method.");
	}
}
```

###  AbstractFactory.java

```java
public abstract class AbstractFactory {
	abstract Shape getShape(String shapeType) ;
}
```

### ShapeFactory.java

```java
public class ShapeFactory extends AbstractFactory {
	@Override
	public Shape getShape(String shapeType) {    
		if (shapeType.equalsIgnoreCase("RECTANGLE")) {
			return new Rectangle();         
		}
		else if (shapeType.equalsIgnoreCase("SQUARE")) {
			return new Square();
		}	 
	return null;
	}
}
```

### RoundedShapeFactory.java

```java
public class RoundedShapeFactory extends AbstractFactory {
	@Override
	public Shape getShape(String shapeType) {    
		if (shapeType.equalsIgnoreCase("RECTANGLE")) {
			return new RoundedRectangle();         
		}
		else if (shapeType.equalsIgnoreCase("SQUARE")) {
			return new RoundedSquare();
		}	 
		return null;
	}
}
```

### FactoryProducer.java

```java
public class FactoryProducer {
	public static AbstractFactory getFactory(boolean rounded) {   
		if (rounded) {
			return new RoundedShapeFactory();         
		}
		else {
			return new ShapeFactory();
		}
	}
}
```

### AbstractFactoryPatternDemo.java

```java
public class AbstractFactoryPatternDemo {
	public static void main(String[] args) {
		// Get shape factory
		AbstractFactory shapeFactory = FactoryProducer.getFactory(false);
		// Get an object of Shape Rectangle
		Shape shape1 = shapeFactory.getShape("RECTANGLE");
		// Call draw method of Shape Rectangle
		shape1.draw();
		// Get an object of Shape Square 
		Shape shape2 = shapeFactory.getShape("SQUARE");
		// Call draw method of Shape Square
		shape2.draw();
		
		// Get shape factory
		AbstractFactory shapeFactory1 = FactoryProducer.getFactory(true);
		// Get an object of Shape Rectangle
		Shape shape3 = shapeFactory1.getShape("RECTANGLE");
		// Call draw method of Shape Rectangle
		shape3.draw();
		// Get an object of Shape Square 
		Shape shape4 = shapeFactory1.getShape("SQUARE");
		// Call draw method of Shape Square
		shape4.draw();
	}
}
```