# Builder Pattern

![Diagram of Builder Pattern](https://www.tutorialspoint.com/design_pattern/images/builder_pattern_uml_diagram.jpg)

### Item.java

```java
public interface Item {
	public String name();
	public Packing packing();
	public float price();	
}
```

### Packing.java

```java
public interface Packing {
	public String pack();
}
```

### Wrapper.java 

```java
public class Wrapper implements Packing {
	@Override
	public String pack() {
		return "Wrapper";
	}
}
```

### Bottle.java

```java
public class Bottle implements Packing {
	@Override
	public String pack() {
		return "Bottle";
	}
}
```

### Burger.java 

```java
public abstract class Burger implements Item {
	@Override
	public Packing packing() {
		return new Wrapper();
	}

	@Override
	public abstract float price();
}
```

### ColdDrink.java 

```java
public abstract class ColdDrink implements Item {
	@Override
	public Packing packing() {
		return new Bottle();
	}

	@Override
	public abstract float price();
}
```

### VegBurger.java 

```java
public class VegBurger extends Burger {
	@Override
	public float price() {
		return 25.0f;
	}

	@Override
	public String name() {
		return "Veg Burger";
	}
}
```

### ChickenBurger.java 

```java
public class ChickenBurger extends Burger {
	@Override
	public float price() {
		return 50.5f;
	}

	@Override
	public String name() {
		return "Chicken Burger";
	}
}
```

### Coke.java 

```java
public class Coke extends ColdDrink {
	@Override
	public float price() {
		return 30.0f;
	}

	@Override
	public String name() {
		return "Coke";
	}
}
```

### Pepsi.java 

```java
public class Pepsi extends ColdDrink {
	@Override
	public float price() {
		return 35.0f;
	}

	@Override
	public String name() {
		return "Pepsi";
	}
}
```

### Meal.java 

```java
import java.util.ArrayList;
import java.util.List;

public class Meal {
	private List<Item> items = new ArrayList<Item>();	

	public void addItem(Item item) {
		items.add(item);
	}

	public float getCost() {
		float cost = 0.0f;      
		for (Item item : items) {
			cost += item.price();
		}		
		return cost;
	}

	public void showItems() {
		for (Item item : items) {
			System.out.print("Item : " + item.name());
			System.out.print(", Packing : " + item.packing().pack());
			System.out.println(", Price : " + item.price());
		}		
	}	
}
```

### MealBuilder.java 

```java
public class MealBuilder {
	public Meal prepareVegMeal() {
		Meal meal = new Meal();
		meal.addItem(new VegBurger());
		meal.addItem(new Coke());
		return meal;
	}   

	public Meal prepareNonVegMeal() {
		Meal meal = new Meal();
		meal.addItem(new ChickenBurger());
		meal.addItem(new Pepsi());
		return meal;
	}
}
```

### BuilderPatternDemo.java 

```java
public class BuilderPatternDemo {
	public static void main(String[] args) {
		MealBuilder mealBuilder = new MealBuilder();

		Meal vegMeal = mealBuilder.prepareVegMeal();
		System.out.println("Veg Meal");
		vegMeal.showItems();
		System.out.println("Total Cost: " + vegMeal.getCost());

		Meal nonVegMeal = mealBuilder.prepareNonVegMeal();
		System.out.println("\n\nNon-Veg Meal");
		nonVegMeal.showItems();
		System.out.println("Total Cost: " + nonVegMeal.getCost());
	}
}
```