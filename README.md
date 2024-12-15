# Dart-journey

# dart#2



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
- `names.add('Mike')` -> ['Raj', 'John', 'Rocky', 'Mike']
- `names.addAll(['Mike', 'Doe'])` -> ['Raj', 'John', 'Rocky', 'Mike', 'Doe']
- `names.insert(2, 'Jane')` -> [Raj, John, Jane, Rocky]
- `names.remove('John')` -> ['Raj', 'Rocky']
- `names.removeAt(2)` -> [Raj, John]

### Set
faster than list!<br>
`Set<String> fruits = { 'Apple', 'Orange', 'Mango', 'Banana' }`
* `fruits.first` -> Apple
* `fruits.last` -> Banana
* `fruits.isEmpty` -> false
* `fruits.isNotEmpty` -> true
* `fruits.contains('Mango')` -> true
* `fruits.add('Lemon')` -> { Apple, Orange, Mango, Banana, Lemon }

### Map
* store as keys and values
```dart
  Map<String, String> countryCapital = {
    'USA' : 'Washington',
    'India' : 'New Delhi',
    'China' : 'Beijing',
  };
```
* `countryCapital.keys` -> (USA, India, China)
* `countryCapital.values` -> (Washington, New Delhi, Beijing)
* Adding item: <br>
  `countryCapital['Thailand'] = 'Bangkok';`
* loop throgh map
  ```dart
  countryCapital.forEach((key, value) => print('$key, $value'));
  ```
  you can notice that `forEach` in Dart and JavaScript is not use the same purpose.
  key differences
  
  Allow | JavaScript | Dart
  --- | --- | --- 
  `break` | ❌ | ❌  
  access to index | ✅ | ❌
  iterator | all iterating over JS | list, set, map only
  callback function | ✅ | ✅


* remove where
  ```dart
  countryCapital.removeWhere((key, value) => value == 'Beijing');
  ```


## User input
General structure
```dart
import 'dart:io';

void main() {
  print("Enter name:");
  String? name = stdin.readLineSync();
  print('The input name is $name.');

}
```

the value you input is always `String`. if you want to use `Integer`, you need to parse it first.
```dart
import 'dart:io';

void main() {
  print("Enter number:");
  int? number = int.parse(stdin.readLineSync()!);  // use '!' to tell the compiler "I am sure this value is not null."
  print(number.runtimeType);
  print('The input number is $number.');
}
```
NOTE: why we use `!` 
* `stdin.readLineSync()` returns a nullable `String?`, meaning it can either be a `String` or `null`.
* but `int.parse` is expected `String`, not `String?`. so we need to tell the compiler that this value is `String`.

## Null Safety
* use `?` at the end of a variable name to declare that properties "can be null" 
```dart
String? firstName; // firstName can be null
```

### null-aware operators
  ![{9A5C8893-9A53-4920-A156-6F6F7893502F}](https://github.com/user-attachments/assets/78def860-44b6-45bf-81fe-d698f6b2afbe)

* `!`: to ensure that the value is non-null
  ```dart
  String? message = "Hello, Dart!";
  String result = message!; // Works because message is not null.
  
  String? message = null;
  String result = message!; // Throws runtime error.

  ```

* `??`: to ensure you always have a non-null value
  ```dart
  String? name = null;
  String greeting = name ?? "Guest"; // "Guest" is used because name is null.

  int? nullableNumber = 42;
  int number = nullableNumber ?? 0; // 42 is used because nullableNumber is not null.
  ```

* `??=`: assigns a value only if the variable is currently null
  ```dart
  int? value;
  value ??= 10; // Assigns 10 because value is null.
  print(value); // Output: 10.
  
  value ??= 20; // Does nothing because value is no longer null.
  print(value); // Output: 10.
  ```
* `?.`: allows you to call a method or access a property only if the object is not null (ใช้สำหรับป้องกันการเรียก method หรือ properties จาก object ที่เป็น null)
  ```dart
  String? message = "Hello, Dart!";
  print(message?.length); // Output: 12 (calls 'length' only if message is not null).
  
  message = null;
  print(message?.length); // Output: null (safe, no runtime error).

  ```
* `?[]`: allows safe access to an element in a collection (List, Map, etc.) only if the collection is not null. (คล้าย `?.` ใช้สำหรับป้องกันการเข้าถึง element ที่เป็น null ใน List, Map, etc.)
  ```dart
  Map<String, String>? mapItems = {"name": "Eiei"};
  print(mapItems?["name"]); // Output: Eiei (accesses the value safely).
  
  mapItems = null;
  print(mapItems?["name"]); // Output: null (safe, no runtime error).
  ```

## Advanced Classes
General structure
```dart
class Children extends ParentClass {
  //...
}
```
