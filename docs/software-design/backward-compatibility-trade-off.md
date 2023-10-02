# Backward compatibility trade-off
What are the trade-offs of providing backward compatibility? In this post, I will talk about the backward compatibility trade-off.

Okay, let’s get started!

## Increased complexity

Handling backward compatibility requires the developers to design the APIs that are capable of multiple versions. Creating a backward-compatible API will increase the development time, code complexity, testing efforts, and maintenance costs. This will also make the work more challenging to maintain backward compatibility over time.

## Increased technical debt

Creating a backward-compatible API will increase technical debt because we need to support backward compatibility for a long time. If you are working with your internal frontend team, it may not affect you a lot. Because you can communicate with your internal developers to ask them to change their implementation. But if you are a service provider like Google or Amazon, you can not ask people to change their implementation immediately. That said, you might need to support multiple versions of API for a long time. Before that, you might need to think about when to deprecate the API and tell your customers that your old version of API is going to deprecate at what time.