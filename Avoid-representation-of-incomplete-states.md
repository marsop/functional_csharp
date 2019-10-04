## Rationale

When creating objects, avoid giving the option to instantiate an object without all relevant information. If absolutely necessary it is ok to allow the change in some fields as long as the state of the object instance remains valid.

## Bad example

```csharp

class Person {
  public string Name {get; set;}

  public Person() {}
}

```

This is incorrect because it allows us to create a person without a name. Even though this could be a "valid" state for some newborns, it is usually not what we want to represent (and anyway anybody that is old enough to program should have a name 😄)

```csharp
Person programmer = new Person();
programmer.Name = "Alberto";
```

## Good Example

```csharp

class Person {
  public string Name { get; }

  public Person(string name) {
    Name = name ?? throw new ArgumentNullException(nameof(Name));
  }
}

```

This constructor is much better since using it, it would not be possible to create a `Person` without a `Name`. This way of constructing objects has also the benefit of disabling the [[reassignation of properties|Avoid mutable classes]], which is usually correct (although based on Business requirements this can be wrong - for example for a game character which can dynamically change names)

## See also

* (Immutability)[Avoid-mutable-classes.md]
* [[Validity|Do validate in constructor]]
