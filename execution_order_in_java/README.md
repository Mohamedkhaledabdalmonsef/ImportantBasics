🔹 Why static methods cannot access instance variables

   Static method → belongs to the class, not an object (no this).

   Instance variables → belong to objects, created only when you use new.

   Therefore, a static method can only access:

   Static variables directly.

   Instance variables only if you first create or receive an object.

   ✅ Key rule:

   Static → shared across the class.

   Instance → per object, requires object reference.

🔹 Class Loading vs. Object Creation
   A) Class Loading / Initialization (happens once per class)

      JVM loads class into Method Area.

      Static fields allocated (default values first).

      Static field initializers executed.

      Static blocks executed (in order).

      Now static data exists → static methods can run.

      Triggered by (active use):

      Accessing a static field.

      Calling a static method.

      Creating the first object.

      Using reflection (Class.forName).

      Loading a subclass (loads parent first).

  B) Object Creation (new MyClass(), happens every time)

      Memory allocated in Heap.

      Instance fields set to default values.

      Instance field initializers executed.

      Instance initializer blocks executed.

      Constructor executed.

      Object reference returned (ready to use).

🔹 Active vs Passive Use in class loading 

      Active use → class loads (static initialized).

      Static field access, static method call, object creation, reflection, subclass loading.

      Passive use → class not loaded.

      Declaring a reference (Parent p;).

      Creating an array of references (Parent[] arr = new Parent[5];).

      Using instanceof on null.

🔹 Memory Areas in Java

      Method Area (MetaSpace) → class metadata + static fields.

      Heap → objects + instance fields.

      Stack → local variables, method calls, references.



✅ Final Key Takeaways

   Static part → runs once when class is loaded.

   Instance part → runs every time a new object is created.

   Static methods can’t access instance variables directly because no object exists in static context.

   Active vs passive use explains when classes load into memory.

   Memory is divided into Method Area (class-level), Heap (object-level), Stack (execution-level).


Execution Order (detailed):

1-Class loading phase (happens once per class):

    * Static variables are initialized first, in the order they appear.

    * Then static blocks run (in order of appearance).

   ⚡ Both happen before main() runs or before creating any objects.

2-Object creation phase (every new call):

    * Instance variables are initialized first, in the order they appear.

    * Then instance (non-static) blocks run (in order of appearance).

    * Finally, the constructor runs.


 --> Question: If exist static block and non static block inside clase, what first executes?
  In Java, the execution order of blocks inside a class goes like this:
   1. Static blocks
      * Run once, when the class is loaded into memory by the JVM.

      * They execute before any object of the class is created, and even before the main() method (if the class with main  is being loaded).

      * If there are multiple static blocks, they run in the order they appear in the class.
  
   2. Instance (non-static) blocks
      * Run every time an object of the class is created, right before the constructor executes.

      * If there are multiple instance blocks, they also run in the order they appear in the class.

✅ Summary of order:
   * Static variables → Static blocks → main()  : this happens at first load or new object
   * Each new: Instance variables → Instance blocks → Constructor : this happens at every new object
