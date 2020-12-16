# Proxy Pattern

![Diagram of Proxy Pattern](https://www.tutorialspoint.com/design_pattern/images/proxy_pattern_uml_diagram.jpg)

### Image.java 

```java
public interface Image {
	void display();
}
```

### RealImage.java  

```java
public class RealImage implements Image {

	private String fileName;

	public RealImage(String fileName) {
		this.fileName = fileName;
		loadFromDisk(fileName);
	}

	@Override
	public void display() {
		System.out.println("Displaying " + fileName);
	}

	private void loadFromDisk(String fileName) {
		System.out.println("Loading " + fileName);
	}
}
```

### ProxyImage  

```java
public class ProxyImage implements Image {

	private RealImage realImage;
	private String fileName;

	public ProxyImage(String fileName) {
		this.fileName = fileName;
	}

	@Override
	public void display() {
		if (realImage == null) {
			realImage = new RealImage(fileName);
		}
		realImage.display();
	}
}
```

### ProxyPatternDemo.java 

```java
public class ProxyPatternDemo {
	
	public static void main(String[] args) {
		Image image = new ProxyImage("test_10mb.jpg");

		// Image will be loaded from disk
		image.display(); 
		System.out.println("");
      
		// Image will not be loaded from disk
		image.display(); 	
	}
}
```