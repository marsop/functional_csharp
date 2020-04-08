# Avoid projections of enumerables

Instead use operations acting on single items and map those by using Linq

# Example

## Don't

```csharp

public IEnumerable<OutType> MapInputs(IEnumerable<InType> inputs) {
  foreach (var input in inputs) {
    var output = // do something with input
    yield output
  }
}

var outputs = MapInputs(inputs);

```

## Do

```csharp
public OutType MapInput(InType input) {
  var output = // do something with input
  return output;
}

var outputs = inputs.Select(MapInput);
```
