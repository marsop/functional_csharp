# Avoid mutable classes

## Rationale

Allowing the client to modify the internals of a class breaks encapsulation. Use methods to modify internal state and use `private` setters by default.

## Bad example

```csharp
public class Person {
  public string Name {get; set;}
}
```

## Good example

```csharp
public class Person {
  public string Name {get; private set;}
  
  public void ChangeName(string name) {
    // perform validation on input string
    // ...
    
    Name = name;
  }
}
```
