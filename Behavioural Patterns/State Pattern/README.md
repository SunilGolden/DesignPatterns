# State Pattern

![Diagram of State Pattern](https://www.tutorialspoint.com/design_pattern/images/state_pattern_uml_diagram.jpg)

### State.java 

```java
public interface State {
	public void doAction(Context context);
}
```

### StartState.java 

```java
public class StartState implements State {

	public void doAction(Context context) {
		System.out.println("Player is in start state");
		context.setState(this);	
	}

	public String toString() {
		return "Start State";
	}
}
```

###  StopState.java 

```java
public class StopState implements State {

	public void doAction(Context context) {
		System.out.println("Player is in stop state");
		context.setState(this);	
	}

	public String toString() {
		return "Stop State";
	}
}
```

###  Context.java 

```java
public class Context {
	private State state;

	public Context() {
		state = null;
	}

	public void setState(State state) {
		this.state = state;		
	}

	public State getState() {
 		return state;
   	}
}
```

### StatePatternDemo.java 

```java
public class StatePatternDemo {
	public static void main(String[] args) {
		Context context = new Context();

		StartState startState = new StartState();
		startState.doAction(context);

		System.out.println(context.getState().toString());

		StopState stopState = new StopState();
		stopState.doAction(context);

		System.out.println(context.getState().toString());
   	}
}
```
