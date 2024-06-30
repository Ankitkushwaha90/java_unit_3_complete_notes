### 1. Functional Interfaces
Functional interfaces are interfaces with a single abstract method. They can be implemented using lambda expressions.

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void myMethod();
}

public class FunctionalInterfaceExample {
    public static void main(String[] args) {
        MyFunctionalInterface fi = () -> System.out.println("Functional Interface Example");
        fi.myMethod();
    }
}
```
### 2. Lambda Expressions
Lambda expressions provide a clear and concise way to represent a functional interface using an expression.

```java
import java.util.Arrays;
import java.util.List;

public class LambdaExpressionExample {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("one", "two", "three");
        list.forEach(s -> System.out.println(s));
    }
}
```
### 3. Method References
Method references are a shorthand notation of a lambda expression to call a method.

```java
import java.util.Arrays;
import java.util.List;

public class MethodReferenceExample {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("one", "two", "three");
        list.forEach(System.out::println);
    }
}
```
### 4. Stream API
Stream API is used to process collections of objects in a functional style.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamAPIExample {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("one", "two", "three", "four");
        List<String> filteredList = list.stream()
                                        .filter(s -> s.startsWith("t"))
                                        .collect(Collectors.toList());
        filteredList.forEach(System.out::println);
    }
}
```
### 5. Default Methods
Default methods allow adding new methods to interfaces without breaking the implementing classes.

```java
interface MyInterface {
    default void myDefaultMethod() {
        System.out.println("Default Method");
    }
}

public class DefaultMethodExample implements MyInterface {
    public static void main(String[] args) {
        DefaultMethodExample example = new DefaultMethodExample();
        example.myDefaultMethod();
    }
}
```
### 6. Static Methods
Static methods in interfaces allow defining utility methods.

```java
interface MyInterface {
    static void myStaticMethod() {
        System.out.println("Static Method");
    }
}

public class StaticMethodExample {
    public static void main(String[] args) {
        MyInterface.myStaticMethod();
    }
}
```
### 7. Base64 Encode and Decode
Java provides built-in methods for Base64 encoding and decoding.

```java
import java.util.Base64;

public class Base64Example {
    public static void main(String[] args) {
        String original = "Hello, World!";
        String encoded = Base64.getEncoder().encodeToString(original.getBytes());
        String decoded = new String(Base64.getDecoder().decode(encoded));

        System.out.println("Original: " + original);
        System.out.println("Encoded: " + encoded);
        System.out.println("Decoded: " + decoded);
    }
}
```
### 8. ForEach Method
The forEach method in Java 8 is used to iterate over collections.

```java
import java.util.Arrays;
import java.util.List;

public class ForEachMethodExample {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("one", "two", "three");
        list.forEach(System.out::println);
    }
}
```
### 9. Try-with-resources
The try-with-resources statement ensures that each resource is closed at the end of the statement.

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class TryWithResourcesExample {
    public static void main(String[] args) {
        try (BufferedReader br = new BufferedReader(new FileReader("test.txt"))) {
            String line;
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
### 10. Type Annotations
Type annotations can be used to annotate any use of a type.

```java
import java.lang.annotation.ElementType;
import java.lang.annotation.Target;

@Target(ElementType.TYPE_USE)
@interface NonNull {}

public class TypeAnnotationsExample {
    public static void main(String[] args) {
        @NonNull String str = "Type Annotations Example";
        System.out.println(str);
    }
}
```
### 11. Repeating Annotations
Repeating annotations allow applying the same annotation multiple times to a declaration.

```java
import java.lang.annotation.Repeatable;

@Repeatable(MyAnnotations.class)
@interface MyAnnotation {
    String value();
}

@interface MyAnnotations {
    MyAnnotation[] value();
}

@MyAnnotation("First")
@MyAnnotation("Second")
public class RepeatingAnnotationsExample {
    public static void main(String[] args) {
        MyAnnotation[] annotations = RepeatingAnnotationsExample.class.getAnnotationsByType(MyAnnotation.class);
        for (MyAnnotation annotation : annotations) {
            System.out.println(annotation.value());
        }
    }
}
```
### 12. Java Module System
The Java Module System (introduced in Java 9) allows you to group related packages together.

```java
// module-info.java
module mymodule {
    exports com.example.mymodule;
}
```
```java
// src/com/example/mymodule/HelloModule.java
package com.example.mymodule;

public class HelloModule {
    public static void main(String[] args) {
        System.out.println("Hello, Module!");
    }
}
```
### 13. Diamond Syntax with Inner Anonymous Class
The diamond syntax can be used with anonymous inner classes.

```java
import java.util.ArrayList;
import java.util.List;

public class DiamondSyntaxExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>() {
            {
                add("one");
                add("two");
                add("three");
            }
        };
        list.forEach(System.out::println);
    }
}
```
### 14. Local Variable Type Inference
Local variable type inference allows the compiler to infer the type of the variable from the context.

```java
public class LocalVariableTypeInferenceExample {
    public static void main(String[] args) {
        var str = "Local Variable Type Inference";
        System.out.println(str);
    }
}
```
### 15. Switch Expressions
Switch expressions simplify switch statements and allow returning values.

```java
public class SwitchExpressionsExample {
    public static void main(String[] args) {
        int day = 2;
        String dayName = switch (day) {
            case 1 -> "Sunday";
            case 2 -> "Monday";
            case 3 -> "Tuesday";
            case 4 -> "Wednesday";
            case 5 -> "Thursday";
            case 6 -> "Friday";
            case 7 -> "Saturday";
            default -> "Invalid day";
        };
        System.out.println(dayName);
    }
}
```
### 16. Yield Keyword
The yield keyword is used in switch expressions to return a value.

```java
public class YieldKeywordExample {
    public static void main(String[] args) {
        int day = 2;
        String dayName = switch (day) {
            case 1 -> "Sunday";
            case 2 -> "Monday";
            case 3 -> "Tuesday";
            case 4 -> "Wednesday";
            case 5 -> "Thursday";
            case 6 -> "Friday";
            case 7 -> "Saturday";
            default -> {
                yield "Invalid day";
            }
        };
        System.out.println(dayName);
    }
}
```
### 17. Text Blocks
Text blocks allow multiline strings more easily.

```java
public class TextBlocksExample {
    public static void main(String[] args) {
        String textBlock = """
                This is a text block.
                It allows multiline strings.
                """;
        System.out.println(textBlock);
    }
}
```
### 18. Records
Records provide a compact syntax for declaring data classes.

```java
public record Person(String name, int age) {}

public class RecordsExample {
    public static void main(String[] args) {
        Person person = new Person("John", 30);
        System.out.println(person.name());
        System.out.println(person.age());
    }
}
```
### 19. Sealed Classes
Sealed classes restrict which other classes or interfaces may extend or implement them.

```java
public abstract sealed class Shape permits Circle, Rectangle {}

final class Circle extends Shape {
    double radius;
}

final class Rectangle extends Shape {
    double length, width;
}

public class SealedClassesExample {
    public static void main(String[] args) {
        Circle circle = new Circle();
        Rectangle rectangle = new Rectangle();
        System.out.println("Circle and Rectangle created successfully.");
    }
}
```
These examples cover various new features in recent versions of Java. Let me know if you need more detailed explanations or additional examples!
