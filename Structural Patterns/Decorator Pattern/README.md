# Decorator Pattern

![Diagram of Decorator Pattern](https://www.tutorialspoint.com/design_pattern/images/decorator_pattern_uml_diagram.jpg)

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

### Circle.java  

```java
public class Circle implements Shape {
	@Override
	public void draw() {
		System.out.println("Drawing Circle ...");
	}
}
```

### ShapeDecorator.java  

```java
public abstract class ShapeDecorator implements Shape {
	protected Shape decoratedShape;

	public ShapeDecorator(Shape decoratedShape) {
		this.decoratedShape = decoratedShape;
	}

	public void draw() {
		decoratedShape.draw();
	}	
}
```

### RedShapeDecorator.java  

```java
public class RedShapeDecorator extends ShapeDecorator {
	public RedShapeDecorator(Shape decoratedShape) {
		super(decoratedShape);		
	}

	@Override
	public void draw() {
		decoratedShape.draw();	       
		setRedBorder(decoratedShape);
	}

	private void setRedBorder(Shape decoratedShape) {
		System.out.println("Border Color: Red");
	}
}
```

### DecoratorPatternDemo.java  

```java
public class DecoratorPatternDemo {
	public static void main(String[] args) {

		Shape circle = new Circle();

		Shape redCircle = new RedShapeDecorator(new Circle());

		Shape redRectangle = new RedShapeDecorator(new Rectangle());
		System.out.println("Circle with normal border");
		circle.draw();

		System.out.println("\nCircle of red border");
		redCircle.draw();

		System.out.println("\nRectangle of red border");
		redRectangle.draw();
	}
}
```