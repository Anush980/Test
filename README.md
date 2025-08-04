## JAVA Program to demonstrate the concept of InterThread Communication

```bash
class MyThread {
    synchronized void demo() {
        try {
            System.out.println("Thread is waiting...");
            wait(); 
            System.out.println("Thread is resumed!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    synchronized void trigger() {
        try {
            Thread.sleep(1000); 
            notify();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

public class InterThreadMini {
    public static void main(String[] args) {
        MyThread obj = new MyThread();

        Thread t1 = new Thread(new Runnable() {
            public void run() {
                obj.demo();
            }
        });

        Thread t2 = new Thread(new Runnable() {
            public void run() {
                obj.trigger();
            }
        });

        t1.start();
        t2.start();
    }
}
```
