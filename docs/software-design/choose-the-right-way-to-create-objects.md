# Choose the right way to create objects

In software development, we need to create different objects in our day-to-day work and it is so common, especially if you are using an object-oriented language. When talking about object creation, the first thing that comes to our mind is Constructor.

You would say it is easy, we can use the constructor and put the required parameters into the constructor, and use the new keyword to instantiate the object. That’s it.

Yes, it is right in some sense. But what if you have different variations in the object? Some parameters are optional. How do you solve it?

Now, you would say we can create different constructors to cater to different behaviors.

Yes, it could be the solution. But, is this approach clean enough when people read your code?

Let’s take C# TimeSpan as an example:
```csharp
var duration1 = new TimeSpan(5);
var duration2 = new TimeSpan(0, 0, 5);
var duration3 = new TimeSpan(5, 0, 0);
var duration4 = new TimeSpan(5, 0, 0, 0, 0);
```

The above objects are created using the constructor. What is the problem here? Can you tell what is the meaning of the “5” in the 4 objects? Probably not, right? When using a constructor to instantiate different object variations, it basically hides the actual behavior and the meaning of the object itself. Everything becomes vague now, without comments we can’t really understand what is happening here. The readability is not good because people need to think about the meaning of "5" or maybe need to dive into the source code of TimeSpan.

If we don’t use the constructor to instantiate the objects, what else can we choose? 

![](../assets/resources/software-design/object-creation-1.png)

Personally, I will choose the **Static Factory Method** for the less complicated objects like this case. With the static factory method, we can create different static methods in the object with a meaningful name. The static methods will help us construct the object and return the object to us. Using this, we hide the implementation details and shift the complexity to another place, the code readability gets improved like the following code snippet.

```csharp
var duration1 = TimeSpan.FromTicks(5);
var duration2 = TimeSpan.FromSeconds(5);
var duration3 = TimeSpan.FromHours(5);
var duration4 = TimeSpan.FromDays(5);
```

Now, we can know the meaning of “5” in different objects and we don’t need to put comments on different objects to explain what it is. Everything is quite obvious by using the static factory method.

>Sandi Metz: Design is thus about picking the right abstractions. If you choose well, your code will be expressive, understandable, and flexible, and everyone will love both it and you. However, if you get the abstractions wrong, your code will be convoluted, confusing, and costly, and your programming peers will hate you.