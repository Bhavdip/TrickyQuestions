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
    s.getScore();
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
