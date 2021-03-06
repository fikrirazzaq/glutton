# Glutton

Flutter shared preferences customized plugin. Secure, Encrypted, Simplified use, Simple key-value pairs storage.

## Getting Started

In your flutter project add the dependency:

```yml
dependencies:
  ...
  glutton: ^1.0.0
```

## Usage
#### Importing package
```
import 'package:glutton/glutton.dart';
```
#### Using Glutton

#### Saving data inside glutton
```
bool isSuccess = await Glutton.eat(key, data);
```
#### Retrieve data inside glutton
```
dynamic data = await Glutton.vomit(key);
```
#### Check if data is exist inside glutton
```
bool isExist = await Glutton.have(key);
```
#### Remove data inside glutton
```
bool isSuccess = await Glutton.digest(key);
```
#### Clear all data inside glutton
```
await Glutton.flush();
```

## Edible data type 
- List
- Set
- Map (can eat json here)
- DateTime
- String
- bool
- int (can eat enum index here)
- double

## Example 
#### [Save & retrieve class](https://github.com/agungnursatria/glutton/blob/master/example/lib/eat_class)

Save:
```
/// 1. Create user object
User user = User(
  name: "Gentleton,,
  age: "21",
  createdAt: DateTime.now(),
);

/// 2. Transform user object to map
Map<String, dynamic> userMap = user.toJson();

/// 3. Save user map inside glutton
bool isSuccess = await Glutton.eat(<UserKey>, userMap);
```

Retrieve
```
/// 1. Retrieve user map inside glutton
Map<String, dynamic> userMap = await Glutton.vomit(<UserKey>);

/// 2. Transform user map to user object
User user = User.fromJson(userMap);
```

#### [Save & retrieve date](https://github.com/agungnursatria/glutton/blob/master/example/lib/eat_date/eat_date_page.dart)

Save:
```
/// 1. Set selected date
DateTime date = await showDatePicker(
  context: context,
  initialDate: _selectedDate,
  firstDate: DateTime(1990),
  lastDate: DateTime(2030),
);

/// 2. Save selected date inside glutton
await Glutton.eat(<DateKey>, date);
```

Retrieve
```
/// 1. Retrieve user map inside glutton
DateTime date = await Glutton.vomit(<DateKey>);
```

#### [Save & retrieve enum](https://github.com/agungnursatria/glutton/blob/master/example/lib/eat_enum)

Save:
```
/// 1. Retrieve index of enum
int index = Season.index;

/// 2. Save index inside glutton
await Glutton.eat(<enumKey>, index);
```

Retrieve
```
/// 1. Retrieve index inside glutton
int index = await Glutton.vomit(<enumKey>);

/// 2. Transform index to enum
Season _season = SeasonManager.fromIndex(index); 
```
You can follow [Season enum](https://github.com/agungnursatria/glutton/blob/master/example/lib/eat_enum/enum_season.dart) for step 2 retrieve enum