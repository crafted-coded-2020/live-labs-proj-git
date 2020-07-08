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
