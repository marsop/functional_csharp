# Avoid projections of enumerables

Instead use operations acting on single items and map those by using Linq

# Example

## Don't

```csharp

public IEnumerable<OutType> MapInput(IEnumerable<InType> ins) {
  foreach (var input in ins) {
    var output = // do something with input
    yield output
  }
}

```

## Do

```csharp
public OutType MapInput(InType input) {
  var output = // do something with input
  return output;
}

ins.Select(MapInput);
```
