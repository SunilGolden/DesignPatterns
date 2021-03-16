# Iterator Pattern

![Diagram of Iterator Pattern](https://www.tutorialspoint.com/design_pattern/images/iterator_pattern_uml_diagram.jpg)

### Iterator.java

```java
public interface Iterator {
	public boolean hasNext();
	public Object next();
}
```

### Container.java

```java
public interface Container {
	public Iterator getIterator();
}
```

### NameRepository.java

```java
public class NameRepository implements Container {
	public String names[] = {"Ram", "Shyam", "Hari", "Krishna"};

	@Override
	public Iterator getIterator() {
		return new NameIterator();
	}

	private class NameIterator implements Iterator {
		int index;

   		@Override
      		public boolean hasNext() {
         		if (index < names.length) {
            			return true;
         		}
         		return false;
		}
      	}

	@Override
	public Object next() {
		if (this.hasNext()) {
		      return names[index++];
		}
		return null;
	}		
}
```

### IteratorPatternDedmo.java

```java
public class IteratorPatternDemo {
	public static void main(String[] args) {
		NameRepository namesRepository = new NameRepository();

		for (Iterator iter = namesRepository.getIterator(); iter.hasNext();) {
			String name = (String) iter.next();
			System.out.println("Name : " + name);
		} 	
	}
}
```
