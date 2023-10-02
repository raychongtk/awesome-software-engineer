# Build a complex object
We have talked about the object creation approaches including **Constructors** and **Static Factory Methods** in the last post. But these approaches are more for simple object creation scenarios. 

What if today we need to create a complex object with some optional fields, how do we deal with this use case? Assuming we have 10+ or 20+ fields or we have different combinations. Now, we want to provide a flexible way for developers to create the object.

Under this scenario, the constructor and static factory method are definitely not a good way to build such a complex object or offer good code readability. If you are going to use the constructor or static factory method, probably you need to create different variations with many parameters placed in the method signature or constructor. That sounds not a good way, because it makes people confused when they look at the method signatures or constructors.

So, how do we solve this problem in an engineering way? Not constructor and not static factory method.

You may say we can solve this problem with **Setter**. Yes, you can, but sometimes we want **immutability** for an object. That said, we don’t want developers to mutate the object state after it creates. With this assumption, setter might not be a good choice for us because developers can mutate the object through the setters after it creates.

The setter approach is banned. So, how to solve this problem gracefully? Fortunately, the **builder pattern** comes to the rescue in this use case.

![](../assets/resources/software-design/builder.png)

Builder is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types and representations of an object using the same construction code. (Read more: https://refactoring.guru/design-patterns/builder)

With the builder pattern, we can offer an elegant and flexible way to build a complex object. The developers can choose the fields that they are interested in the object and build the object step by step.

Let us go through an example below to understand more about the builder pattern. (The example is using Java, sorry for non-Java guys)

Builder Pattern Code Snippet:
```java
public class HttpUrl {
    private final String schema;
    private final String host;
    private final String port;
    private final String path;
    private final Map<String, String> queryParams;

    private HttpUrl(Builder builder) {
        this.schema = builder.schema;
        this.host = builder.host;
        this.port = builder.port;
        this.path = builder.path;
        this.queryParams = builder.queryParams;
    }

    // omit implementation

    public static class Builder {
        private String schema;
        private String host;
        private String port;
        private String path;
        private Map<String, String> queryParams = new HashMap<>();

        public Builder(String schema, String host) {
            this.schema = schema;
            this.host = host;
        }

        public Builder port(String port) {
            this.port = port;
            return this;
        }

        public Builder path(String path) {
            this.path = path;
            return this;
        }

        public Builder queryParam(String key, String value) {
            this.queryParams.put(key, value);
            return this;
        }

        public HttpUrl build() {
            return new HttpUrl(this);
        }
    }
}
```

We can put the mandatory fields in the constructor to restrict developers to fill in the fields.
```java
HttpUrl url = new HttpUrl.Builder("https", "awesomesoftwareengineer.com").build();
```

Also, we can build some optional fields if needed.

```java
HttpUrl url = new HttpUrl.Builder("https", "awesomesoftwareengineer.com")
                .port("8080")
                .path("/design-pattern")
                .queryParam("author", "ray")
                .build();
```
Imagine if you don’t use the builder pattern, how many constructors do you need to create for this use case? In this use case, we have only a few attributes but we have many different combinations. What if you are dealing with 10 or 20+ attributes? If we still use constructors, the code will be terrible and out of control.

## The benefit
The builder pattern offers several benefits to us including:

- **Immutability:** The object state cannot be updated after the object creation because we no longer need the setters to help us assign the values to the fields.

- **Flexibility:** When building a complex object with different combinations, the builder patterns can work perfectly because it offers a flexible way for developers to choose the fields that they are interested in and build the object step by step.

- **Readability:** Using the builder pattern, we don’t need to create different constructors to cater to different scenarios. The methods are easy to read and human-friendly. It is almost like reading English.

## The drawback
Increases the overall code complexity after adopting the builder pattern but the cost is acceptable.

## Summary
Any design choice has a cost, it is not a free product. So, use the design pattern only if the price is acceptable and your team is willing to pay the price.


