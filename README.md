# Learning Flutter

## Sound Null Safety
Null is not a value, it specifies that a variable or constant may not have a value. In the first versions of dart, null safety wasn’t supported but this got added along the line.

### Making a type nullable
Any variable maybe nullable by adding a question mark (❓) to the datatype e.g
`String? name = null`
A list can be made null, however, if a list is null and the contents are null without null safety there will be an error. To mitigate this, we have to make both the list and it’s content nullable

`List<String?> names = ['foo', 'bar', null ] // The contents can be null`
`List<String>? names = ['foo', 'bar', 'baz' ] // The list can be null`

### Selecting non-null values
Using the ?? Operator instead of using if statements to check if an object or type is null, we would use the ?? Operator. this operator is a null aware operator that picks either the LHS or RHS depending on which one is not null e.g.
```
const String? firstName = null
const String? middleName = null
const String? lastName = 'Baz'

final firstNonNullValue = firstName ?? lastName ?? lastName
```

The results are always nullable 

### Null-aware assignment Operator (??=)
This operator checks the value on the left-side. If it’s null it will assign a value to it and if It’s not null it won’t assign any value. This is very similar to the code below

```
String? firstName = null
String? lastName = Baz
String? name = ''

if (firstName != null ){
    name = firstName;
}
else if (lastName != null){
    name = lastName;
}
print(name)
The above if statements can be summarized as follows:

name ??= firstName;
name ??= lastName;
print(name)
```

### Conditional Invocation (?.)
Using the ?. Syntax, you can conditionally invoke a method or property. In other programming languages invoking a function of an optional property will require writing lengthy if statements as shown below:

```
void testing(List<String>? names){
    int length = 0
    if (names != null){
        length = names.length;
    }
}
```
Accessing the lengths property of a nullable list of names, requires that we check if the list is not null. In dart, conditional invocation can solve this problem. The code above is a type promotion. After the list has been verified not to be null, it can be promoted to non null list the process of checking if a property or method is not null and doing some work on it is called type promotion.

```
The code able can be summarized as follows:
void testing(List<String>? names){
    int length = 0
    length = names?.lenghth ??= 0
}
```
## Enumerations
Enumeration is making a string written programmatically to become an entity. It can be defined as a named list of related property. Unlike variables and constants enumerations capitalize all the first letters of every word. E.g. enums are similar to sets in flutter but can take multiple datatypes and support the `(.)` operator to access the properties

An enumeration makes sure a value has a name so it can be programmatically referred to. You can categorize related items so you can relate to them later.

```
enum PersonalProperties { firstName, lastName, age}
PersonalProperties.firstName
```

Switch Statements
A switch statement is very similar to if-else statements but if-else statements are used to choose between two options, while the switch case statement is used to choose between numerous options. Switch statements are the same in dart as in other programming languages. 
E.g 
```
switch (PersonalProps) {
case PersonalProps.firstName:
//block of code
break;

case identifier2:
//block of code
break;

case identifier3:
//block of code
break;

case identifierN:
//block of code
break;
}
```
