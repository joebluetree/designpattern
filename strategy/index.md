# Strategy Pattern
<p>
In this pattern the object creation logic is separated from the user interface. The consumer or the client code will not have the object creation code. Object creation code is moved into another class and the client uses this class whenever an object need to be created.
</p>

## Implementation

<p>
<img src="image1.png"> </img>
</p>


```

public interface Shape {
   void draw();
}
public class Rectangle implements Shape {
   public void draw() {
      System.out.println("Inside Rectangle::draw() method.");
   }
}
public class Square implements Shape {
   public void draw() {
      System.out.println("Inside Square::draw() method.");
   }
}
public class Circle implements Shape {
   public void draw() {
      System.out.println("Inside Circle::draw() method.");
   }
}

//Factory Class
public class ShapeFactory {
   //use getShape method to get object of type shape 
   public Shape getShape(String shapeType){
      if(shapeType == null){
         return null;
      }		
      if(shapeType.equalsIgnoreCase("CIRCLE")){
         return new Circle();
      } else if(shapeType.equalsIgnoreCase("RECTANGLE")){
         return new Rectangle();
      } else if(shapeType.equalsIgnoreCase("SQUARE")){
         return new Square();
      }
      return null;
   }
}

//Client Code
public class FactoryPatternDemo {
   public static void main(String[] args) {
      ShapeFactory shapeFactory = new ShapeFactory();
      //get an object of Circle and call its draw method.
      Shape shape1 = shapeFactory.getShape("CIRCLE");
      //call draw method of Circle
      shape1.draw();
      //get an object of Rectangle and call its draw method.
      Shape shape2 = shapeFactory.getShape("RECTANGLE");
      //call draw method of Rectangle
      shape2.draw();
      //get an object of Square and call its draw method.
      Shape shape3 = shapeFactory.getShape("SQUARE");
      //call draw method of square
      shape3.draw();
   }
}


Output
Inside Circle::draw() method.
Inside Rectangle::draw() method.
Inside Square::draw() method.

```