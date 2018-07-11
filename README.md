# TrickyQuestions

Can two Java methods have same name with different return types?

```Java
class Student{

    int getScore(int studentId){

    }

    String getScore(int ClassId){

    }
}

public static void main(String arg[]){
    Student s = new Student();
    s.getScore(10);
}
```
If both methods has different parameter types (so, they have different signature), then it is possible. It is called overloading.


```Java
class Student{

    int getScore(int studentId){

    }

    String getScore(String ClassId){

    }
}

public static void main(String arg[]){
    Student s = new Student();
    s.getScore(10); //this works!
}
```

**What is reflection and what its used?**

**Does the finally execute in Java?**
> System crash, System.exit() such case not.


```Java
public class Application {
    public static void main(String[] args) {
        
        final class Constants {
            public static String name = "PI";
        }
        
        Thread thread = new Thread(new Runnable() {

            @Override
            public void run() {
                System.out.println(Constants.name);
            }
            
        });
        
        thread.start();
    }
}
```
> Application.java:5: error: Illegal static declaration in inner class Constants
            public static String name = "PI";
                                 ^
  modifier 'static' is only allowed in constant variable declarations
1 error


```Java
class Fruit {
    protected static String name = "Sue";
}

class Apple extends Fruit {
    
}

public class Application {
    public static void main(String[] args) {
        System.out.println(Apple.name);
    }
}
```

**What is the volatile keyword? How and why would you use it?**

In Java, each thread has its own stack, including its own copy of variables it can access. When the thread is created, it copies the value of all accessible variables into its own stack. The volatile keyword basically says to the JVM “Warning, this variable may be modified in another Thread”.

In all versions of Java, the volatile keyword guarantees global ordering on reads and writes to a variable. This implies that every thread accessing a volatile field will read the variable’s current value instead of (potentially) using a cached value.

In Java 5 or later, volatile reads and writes establish a happens-before relationship, much like acquiring and releasing a mutex.

Using volatile may be faster than a lock, but it will not work in some situations. The range of situations in which volatile is effective was expanded in Java 5; in particular, double-checked locking now works correctly.

The volatile keyword is also useful for 64-bit types like long and double since they are written in two operations. Without the volatile keyword you risk stale or invalid values.
One common example for using volatile is for a flag to terminate a thread. If you’ve started a thread, and you want to be able to safely interrupt it from a different thread, you can have the thread periodically check a flag (i.e., to stop it, set the flag to true). By making the flag volatile, you can ensure that the thread that is checking its value will see that it has been set to true without even having to use a synchronized block. For example:

```Java
public class Foo extends Thread {
    private volatile boolean close = false;
    public void run() {
        while(!close) {
            // do work
        }
    }
    public void close() {
        close = true;
        // interrupt here if needed
    }
}
```
**What is the difference between String s = "Test" and String s = new String("Test")? Which is better and why?**
In general, String s = "Test" is more efficient to use than String s = new String("Test").

In the case of String s = "Test", a String with the value “Test” will be created in the String pool. If another String with the same value is then created (e.g., String s2 = "Test"), it will reference this same object in the String pool.

However, if you use String s = new String("Test"), in addition to creating a String with the value “Test” in the String pool, that String object will then be passed to the constructor of the String Object (i.e., new String("Test")) and will create another String object (not in the String pool) with that value. Each such call will therefore create an additional String object (e.g., String s2 = new String("Test") would create an addition String object, rather than just reusing the same String object from the String pool).


