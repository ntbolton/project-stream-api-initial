# Java Streams API Tutorial Starter Code

1. Navigate to the following template in GitHub - https://github.com/UltimateSandbox/project-stream-api-initial
2. Fork the repo into your account.
3. In IntelliJ, clone the repo you just forked from *your* account.  (File -> New -> Project From Version Control)
4. Follow the instructions in the README.md file (this file) to complete the assignment.
5. Turn in your assignment by the due date.

### Tutorial Instructions
[Java 8 Stream API Tutorial](https://winterbe.com/posts/2014/07/31/java8-stream-tutorial-examples/)
1. Navigate to the tutorial page below.
2. Read the instructions/comments in the tutorial.
3. As you come across code in the tutorial, copy/paste the code into the StreamAPITutorial class' main method.
4. Complete the following sections of the tutorial to get full credit for this project:
* How streams work
* Different kind of streams
* Processing Order
* Why Order Matters
* Reusing Streams
5. For EXTRA CREDIT on this assignment, complete the following sections in addition to the sections listed above:
* Advanced Operations
* Collect
* FlatMap
* Reduce
* Parallel Streams

### Important Notes on the Tutorial
As with all tutorials, there are a few issues with this one you need to be aware of for it to run properly.  These are listed below.
1. In the section on reusing streams, there is a line that is marked as throwing an exception.  Once you paste this and see the exception thrown, you'll need to comment out this line to be able to get your code to continue to work after that point.  The line in question looks like this:
```java
    stream.noneMatch(s -> true);   // exception
```
- Comment out that line once you run it to get any of the following code to work.
2. In the section labeled FlatMap, you'll see a code example with 2 classes in it.  Those classes should be reversed in order so it matches the example below.  Class Foo references class Bar and must be listed first to avoid an error.
```java
        class Bar {
            String name;

            Bar(String name) {
                this.name = name;
            }
        }

        class Foo {
            String name;
            List<Bar> bars = new ArrayList<>();

            Foo(String name) {
                this.name = name;
            }
        }
```
3. In the section labeled FlatMap, one of the sections of code which looks like this
```java
    IntStream.range(1, 4)
        .mapToObj(i -> new Foo("Foo" + i))
        .peek(f -> IntStream.range(1, 4)
        .mapToObj(i -> new Bar("Bar" + i + " <- " f.name))
        .forEach(f.bars::add))
        .flatMap(f -> f.bars.stream())
        .forEach(b -> System.out.println(b.name));
```
should look like this
```java
    IntStream.range(1, 4)
        .mapToObj(i -> new Foo("Foo" + i))
        .peek(f -> IntStream.range(1, 4)
        .mapToObj(i -> new Bar("Bar" + i + " <- " + f.name))
        .forEach(f.bars::add))
        .flatMap(f -> f.bars.stream())
        .forEach(b -> System.out.println(b.name));
```
There is a typo in it - can you find it?
4. In the section labeled FlatMap, you'll see a code example with 3 classes in it.  Those classes should be reversed in order so it matches the example below.
```java
        class Inner {
            String foo;
        }
        
        class Nested {
            Inner inner;
        }
        
        class Outer {
            Nested nested;
        }
```
5. In the advanced section, you'll see a couple examples where they are reusing the same variable name more than once.  This will cause a comple error so you'll need to rename these variables to avoid this.  For example, ageSum and persons are reused and the instances of reuse will need to be changed to a name of your choice.