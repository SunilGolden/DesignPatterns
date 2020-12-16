# Bridge Pattern

![Diagram of Bridge Pattern](https://www.tutorialspoint.com/design_pattern/images/bridge_pattern_uml_diagram.jpg)

### DrawAPI.java  

```java
public interface DrawAPI {
	public void drawCircle(int radius, int x, int y);
}
```

### RedCircle.java  

```java
public class RedCircle implements DrawAPI {
	@Override
	public void drawCircle(int radius, int x, int y) {
		System.out.println("Drawing Circle[ color: red, radius: " + radius + ", x: " + x + ", " + y + "]");
	}
}
```

### GreenCircle.java  

```java
public class GreenCircle implements DrawAPI {
	@Override
	public void drawCircle(int radius, int x, int y) {
		System.out.println("Drawing Circle[ color: green, radius: " + radius + ", x: " + x + ", " + y + "]");
	}
}
```

### Shape.java  

```java
public abstract class Shape {
	protected DrawAPI drawAPI;
   
	protected Shape(DrawAPI drawAPI) {
		this.drawAPI = drawAPI;
	}

	public abstract void draw();	
}
```

### Circle.java  

```java
public class Circle extends Shape {
	private int x, y, radius;

	public Circle(int x, int y, int radius, DrawAPI drawAPI) {
		super(drawAPI);
		this.x = x;  
		this.y = y;  
		this.radius = radius;
	}

	public void draw() {
		drawAPI.drawCircle(radius,x,y);
	}
}
```

### BridgePatternDemo.java  

```java
public class BridgePatternDemo {
	public static void main(String[] args) {
		Shape redCircle = new Circle(100,100, 10, new RedCircle());
		Shape greenCircle = new Circle(100,100, 10, new GreenCircle());

		redCircle.draw();
		greenCircle.draw();
	}
}
```