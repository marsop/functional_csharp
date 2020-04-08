# Avoid downcasting

## Rationale

The method signature should always use the most specific type possible when returning and the less specific type possible when accepting parameters. This does not mean to use types that do not represent the structure that we need for the operation. Strive to provide explicit signatures that allow for a clear transmission of requirements while still allowing for different types.

## Don't

```csharp
public List<Person> GetPeople(object oSchool) {
  var school = (School)oSchool;
  
  // ..
  
  return people;
}
```

## Do

```csharp
public IReadOnlyList<Person> GetPeople(School school) {

  // ..
  
  return people;
}
```
