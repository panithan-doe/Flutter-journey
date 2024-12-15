# Dart-journey

# dart#2

* use `?` at the end of a variable name to declare that properties "can be null" 
```dart
String? firstName; // firstName can be null
```

## Enum
* print `enum`
  ```dart
  enum days { Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday }
  
  void main() {
    var today = days.Friday;
    print(today);  // days.Friday
  }
  ```
* access all `enum`
  ```dart
  for (days day in days.values) {
    print(day);
  }
  ```
  result:
  ```
  days.Friday
  days.Sunday
  days.Monday
  days.Tuesday
  days.Wednesday
  days.Thursday
  days.Friday
  days.Saturday
  ```

#### Characteristics of `enum` <br>
* declared outside the class.
* use when you need to store a large number of constant values.
* etc.

## Collections

### List
* Fixed length list -> use `filled`
  ```dart
  void main() {
    var list = List<int>.filled(5, 0);
    print(list);  // [0, 0, 0, 0, 0]
  }
  ```
  
  NOTE: in dart it need to initialized the value. if you do not want it, use `null` instead of `0`. 

* Growable list (mostly used)
  ```dart
  void main() {
    var list = [210, 21, 43, 45, 23];
    print(list);  // [210, 21, 43, 45, 23]
  }
  ```
`List<String> names = ['Raj', 'John', 'Rocky'];`    
- `names.add('Mike');  // ['Raj', 'John', 'Rocky', 'Mike']`
- `names.addAll(['Mike', 'Doe']);  // ['Raj', 'John', 'Rocky', 'Mike', 'Doe']`
- `names.insert(2, 'Jane');  // [Raj, John, Jane, Rocky]`
- `names.remove('John')  // ['Raj', 'Rocky']`
- `names.removeAt(2)  // [Raj, John]`

### Set
faster than list!<br>
`Set<String> fruits = { 'Apple', 'Orange', 'Mango', 'Banana' }`
* `fruits.first  // Apple`
* `fruits.last  // Banana`
* `fruits.isEmpty  // false`
* `fruits.isNotEmpty  // true`
* `fruits.contains('Mango')  // true`
* `fruits.add('Lemon')  // { Apple, Orange, Mango, Banana, Lemon }`

