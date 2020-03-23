**Avoid** exposing any kind of mutable collection in interfaces. Instead, use [IReadOnlyCollection\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlycollection-1?view=netcore-3.0), [IReadOnlyList\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlylist-1?view=netcore-3.0) and [IReadOnlyDictionary\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlydictionary-2?view=netcore-3.0) in order to expose the elements of the collection.

## Rationale

Allowing external callers to change the state of the class is an anti-pattern because it breaks the encapsulation and should be avoided.

## Bad example

```chsarp
public interface IPerson {
   IList<IPerson> Kids { get; }
}
```

This allows the user to modify the state of any `IPerson` by just accessing the property and modifying it:

```csharp
IPerson father = ...
father.Kids.Add(father);
```

## Good Example

```chsarp
public interface IPerson {
   IReadOnlyList<IPerson> Kids { get; }
}
```

Here, the class implementing `IPerson` (let's call this class `Citizen`) does expose a collection that can be read, but not modified by any external class. 

## Links

* [IReadOnlyCollection\<T\> ](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlycollection-1?view=netcore-3.0)
* [IReadOnlyList\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlylist-1?view=netcore-3.0) 
* [IReadOnlyDictionary\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlydictionary-2?view=netcore-3.0)
