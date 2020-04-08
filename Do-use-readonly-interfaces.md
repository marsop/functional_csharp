**Avoid** exposing any kind of mutable collection in interface properties. Instead, use [IReadOnlyCollection\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlycollection-1?view=netcore-3.0), [IReadOnlyList\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlylist-1?view=netcore-3.0) and [IReadOnlyDictionary\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlydictionary-2?view=netcore-3.0) in order to expose the elements of the collection.

## Rationale

Allowing external callers to change the state of the class where the collection is stored is an anti-pattern because it breaks the encapsulation. Strive to provide functions that do not modify the collections, but instead create copies of them. Use mutable collections sparingly.

## Don't

```csharp
public interface IPerson {
   IList<IPerson> Kids { get; }
}
```

This allows the user to modify the state of any `IPerson` by just accessing the property and modifying it:

```csharp
IPerson father = ...
father.Kids.Add(father);
```

## Do

```csharp
public interface IPerson {
   IReadOnlyList<IPerson> Kids { get; }
}
```

Here, the class implementing `IPerson` (let's call this class `Citizen`) does expose a collection that can be read, but not modified by any external class. 

## Links

* [IReadOnlyCollection\<T\> ](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlycollection-1?view=netcore-3.0)
* [IReadOnlyList\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlylist-1?view=netcore-3.0) 
* [IReadOnlyDictionary\<T\>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ireadonlydictionary-2?view=netcore-3.0)
