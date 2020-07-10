:beginner: **Labs 4**  
:lock: Perform a deep clone  
:lock: Add a User Defined Object and ensure that it is deep cloned.  
:lock: Add an array of wrapper and ensure that it is deep cloned.  

 
```java
package java7.fundamentals;

import java.util.Arrays;

public class ShallowClone {
	public static void main(String[] args) {
		ObjectToBeCloned.cloneTest();
	}
}
class ObjectToBeCloned implements Cloneable {
	// THE INT ARRAY IS SHALLOW CLONED AS ONLY THE ADDRESS IS COPIED AND THE VALUES
	// ARE NOT COPIED
	public int[] numbers;
	public String nameString = "Rambo";
	public float value = 5.5f;
	public Float floatWrapper = 55.55f;
	public static void cloneTest() {

		ObjectToBeCloned originalObject = new ObjectToBeCloned(2);
		originalObject.numbers[0] = 100;

		// The cloning process
		try {
			ObjectToBeCloned clonedObject = (ObjectToBeCloned) originalObject.clone();
			System.out.println("Cloned successfully!");
			System.out.println("Original      " + originalObject);
			System.out.println("Cloned      " + clonedObject);

			clonedObject.nameString = "John";
			clonedObject.floatWrapper = 789.987f;
			originalObject.value = 500.500f;
			clonedObject.numbers[1] = 5000;

			// AFTER CLONING
			System.out.println("Original      " + originalObject);
			System.out.println("Cloned      " + clonedObject);
		} catch (CloneNotSupportedException e) {
			System.out.println("You cannot clone this object!");
		}
	}
	@Override
	public String toString() {
		return "ObjectToBeCloned [numbers=" + Arrays.toString(numbers) + ", nameString=" + nameString + ", value="
				+ value + ", floatWrapper=" + floatWrapper + "]";
	}
	public ObjectToBeCloned(int size) {
		numbers = new int[size];
	}
}


```


:beginner: **Labs 3**  

:lock: modify the code and prove that two instance are created by using multi-theading

```java
package design_patterns;

public class LazyInitializedSingleton {
//WHY?
// SINGLETON
//SINGLE TO N (SINGLE OBJECT WILL BE CREATED FOR AN APPLICATOIN)
//DEVELOPER SHOULD USE ONLY ONE OBJECT
//DEVERLOPER CANNOT CREATE THE INSTANCE ACCIDENTALLY.

	public static void main(String[] args) {
		Singelteon_CoffeVendingMachine1 singelteon_CoffeVendingMachine 
		= Singelteon_CoffeVendingMachine1.getInstance();
		singelteon_CoffeVendingMachine.brewACupOfCoffee();		
		
		//Check if only one instance is created.
		Singelteon_CoffeVendingMachine1 singelteon_CoffeVendingMachine1
		= Singelteon_CoffeVendingMachine1.getInstance();
		
		singelteon_CoffeVendingMachine1.brewACupOfCoffee();	
		System.out.println(singelteon_CoffeVendingMachine);
		System.out.println(singelteon_CoffeVendingMachine1);
		//A developer cannot create an instance
		//Singelteon_CoffeVendingMachine singelteon_CoffeVendingMachine = new Singelteon_CoffeVendingMachine();
	}
	
}

//HOW to construct a singleton
class Singelteon_CoffeVendingMachine1{
	//STEP 1 : create a variable which is 1. private, 2.static,  3. final
	private static Singelteon_CoffeVendingMachine1 INSTANCE_SINGLETON_COFFEE_VENDING_MACHINE;

	//step 2: create a private constructor
	private Singelteon_CoffeVendingMachine1() {
		
	}
	//step 3: create the accessor to access the instance
	public static Singelteon_CoffeVendingMachine1 getInstance() {
		if(INSTANCE_SINGLETON_COFFEE_VENDING_MACHINE == null) {
		INSTANCE_SINGLETON_COFFEE_VENDING_MACHINE = new Singelteon_CoffeVendingMachine1();
		}
		return INSTANCE_SINGLETON_COFFEE_VENDING_MACHINE;
	}
	
	//business methods
	public void brewACupOfCoffee() {
		System.out.println("A hot cup of coffee specially brewed for Automation Engineers!");
	}
}
```


:beginner: **Labs 1**

:lock:
Implement Lambda expression using the Comparator interface.

:lock: analyze the program below and achieve the same results without using stream api.

```java
package java8_streams;

import java.util.ArrayList;
import java.util.List;

public class ParallelStreamPerformanceTest {
	public static void main(String[] args) {
		// create the source list
		List<Integer> productList = new ArrayList<Integer>();
		productList.add(1000);
		for (int i = 0; i < 10; i++) {
			int lastValue = productList.get(i);
			productList.add(lastValue + 1000);
		}

		System.out.println("Input List ---> " + productList);

		long start = System.nanoTime();
		List seralList = new ArrayList();
		// Returns a sequential Stream with this collection as its source.
		// A sequence of elements supporting sequential and parallel aggregate
		// operations.
		// Returns a stream consisting of the elements of this stream that match the
		// given predicate.
		productList.stream().filter(element -> element > 5000).forEach(System.out::println);

	}
}
```

:beginner: **labs 2**

:lock: store the values 1, 5.5f,'a', true in the same array and print them.

:lock: store the values 1, 5.5f,'a', true in a hashmap and print them.

:lock: analyze the program below and apply instance method reference for method (countElementsInstance).

```java
package com.live.java8;

public class CustomFunctionalInterface {
	public static void main(String[] args) {
		Integer[] intArray = { 5, 6, 7, 8 };
		// using a static method reference
		Counter counter = Utils::countElements;
		System.out.println(counter.count(intArray));
	}
}

@FunctionalInterface
interface Counter {
	int count(Object[] objArray);
	// public abstract int count(Object[] objArray);
//	int count(Object[] objArray) {
//		int count = Utils.countElement(objArray);
//		return count;
//	}
}

class Utils {
	public static int countElements(Object[] array) {
		return array.length;
	}

	public int countElementsInstance(Object[] array) {
		return array.length;
	}
}
```

:lock: modify the code to avoid null pointer exceptions using Optional

```java
package com.live.java8;

import java.util.ArrayList;
import java.util.Optional;

public class OptionalDemo {
	static String testString = null;

	public static void main(String[] args) {
		Person person = null;
		ArrayList arrayList = null;
		Integer numbers[] = null;

		if (Math.random() > 0.5) {
			numbers = new Integer[3];
			numbers[0] = 100;
			testString = "Welcome";
			person = new Person();
			arrayList = new ArrayList();
			arrayList.add("smile");
		}

		Optional optionalString = Optional.ofNullable(testString);
		if (optionalString.isPresent()) {
			System.out.println(testString.length());
			int length = optionalString.get().toString().length();
			System.out.println(length);
		} else {
			System.out.println("String may be null!");
		}

	}
}

class Person {
	private String name = "Tester";

	@Override
	public String toString() {
		return "Person [name=" + name + "]";
	}
}
```

:lock: analyze the code

```java
	private static void reduction_operation() {
		//traditonal way of doing the reduction operation....
		int playersSalary1[] = { 70000, 100, 20000 };
		int sum = 0;
		for (int i = 0; i < playersSalary1.length; i++) {
			sum = sum + playersSalary1[i];
		}
		System.out.println(sum);

		//modern way of performing reduction using stream api
//		int sum1 = Arrays.stream(playersSalary1).sum();
//		System.out.println(sum1);
		System.out.println(Arrays.stream(playersSalary1).sum());
		System.out.println(Arrays.stream(playersSalary1).min());
		System.out.println(Arrays.stream(playersSalary1).max());
		System.out.println(Arrays.stream(playersSalary1).count());
	}
```

Why are we getting
OptionalInt[100]
OptionalInt[70000]
for only min and max reduction operations
but 3 for count?
