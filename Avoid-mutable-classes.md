# Avoid mutable collections

## Rationale

Returning mutable collections allows the client to modify the output of one operation, reducing traceability and making it harder to reason abou the contents of variables in the application.

## Bad example

`public List<T> DoSomething() {..}`

## Good example

`public IReadOnlyList<T> DoSomething() {..}`
