# Facade Pattern

![Diagram of Facade Pattern](https://www.tutorialspoint.com/design_pattern/images/facade_pattern_uml_diagram.jpg)

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
		System.out.println("Drawing Rectangle ...");
	}
}
```

### Square.java 

```java
public class Square implements Shape {
	@Override
	public void draw() {
		System.out.println("Drawing Square ...");
	}
}
```

### Circle.java 

```java
public class Circle implements Shape {
	@Override
	public void draw() {
		System.out.println("Drawing Circle ...");
	}
}
```

### ShapeMaker.java 

```java
public class ShapeMaker {
	private Shape circle;
	private Shape rectangle;
	private Shape square;

	public ShapeMaker() {
		circle = new Circle();
		rectangle = new Rectangle();
		square = new Square();
	}

	public void drawCircle() {
		circle.draw();
	}

	public void drawRectangle() {
		rectangle.draw();
	}
   
	public void drawSquare() {
		square.draw();
	}
}
```

### FacadePatternDemo.java

```java
public class FacadePatternDemo {
	public static void main(String[] args) {
		ShapeMaker shapeMaker = new ShapeMaker();

		shapeMaker.drawCircle();
		shapeMaker.drawRectangle();
		shapeMaker.drawSquare();		
	}
}
```