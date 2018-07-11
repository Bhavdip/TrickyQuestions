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

What is reflection and what its used?

Does the finally execute in Java?
System crash, System.exit() such case not.


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
