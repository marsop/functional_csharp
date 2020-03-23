# Avoid downcasting

## Rationale

The method signature should always use the most specific type possible when returning and the less specific type possible when accepting parameters. This does not mean to use types that do not represent the structure that we need for the operation. Strive to provide explicit signatures that allow for a clear transmission of requirements while still allowing for different types.

## Bad example

```csharp
public List<Person> GetPeople(object schools) {
  var schoolList = (List<School>)schools;
  
  //..
  
  return people;
}
```

## Good example

```csharp
public IReadOnlyList<Person> GetPeople(IEnumerable<School> schools) {..}
```
