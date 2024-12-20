# Toca Loca 🐠🍹🌴

Your favorite website for local shoping has turned into a new app, with a new twist 🐠🍹🌴


<details>
<summary> Assignment 7 </summary>
  
### 1. Explain what are stateless widgets and stateful widgets, and explain the difference between them.
**Stateless Widgets**:
- Stateless widgets are immutable, meaning their properties cannot change once they are built. They are suitable for UI components that do not require any updates or changes after their creation.
- Examples include static text, icons, and simple layouts.

**Stateful Widgets**:
- Stateful widgets are mutable and can change their state during the lifetime of the widget. They maintain a state object that holds data that can be updated, causing the widget to rebuild when necessary.
- Examples include interactive components like checkboxes, text fields, or any widget that responds to user input.

**Key Difference**:
- The primary difference is that stateless widgets cannot change their state or re-render based on user actions, whereas stateful widgets can change and reflect those changes in the UI.

### 2. Mention the widgets that you have used for this project and its uses.
In your project, the following widgets have been used:

- **Scaffold**: Provides a structure for the visual interface, including an AppBar and a body area.
- **AppBar**: Displays a material design app bar at the top of the screen with a title.
- **Column**: Lays out its children in a vertical array, allowing for a stacked layout of widgets.
- **Row**: Arranges its children horizontally, which is used for displaying info cards side by side.
- **InfoCard**: A custom stateless widget used to display static information (NPM, Name, Class).
- **GridView**: Displays a grid of items that scrolls vertically, used for displaying the list of actions (product list, add product, logout).
- **Card**: Provides a material design card layout for the `InfoCard` widget to give it a raised effect.
- **InkWell**: A material design widget that responds to touch events, used for creating tappable areas in `ItemCard`.
- **SnackBar**: A lightweight message at the bottom of the screen that shows feedback when an action occurs (like pressing a button).
  
### 3. What is the use-case for `setState()`? Explain the variable that can be affected by `setState()`.
In this project, the use of `setState()` isn't explicitly present because your `MyHomePage` class is stateless. However, in a stateful widget context, `setState()` is used to notify the Flutter framework that the internal state of a widget has changed, and the framework should rebuild the widget.

**Use Case**:
- When a user interacts with the app (for instance, pressing a button that changes some data), `setState()` would be called to update the UI with the new state.

**Affected Variables**:
- Any variable defined in the state class of a stateful widget can be affected by `setState()`. For example, if you had a `bool isLoading` variable to indicate loading status, you would update this variable inside `setState()` whenever the loading state changes.

### 4. Explain the difference between `const` and `final` keyword.
- **const**:
  - `const` is used for compile-time constants. When you declare a variable with `const`, it is immutable, and its value is determined at compile time. 
  - Example: `const Text('Hello World')` creates a text widget that never changes.

- **final**:
  - `final` is used for variables that can only be assigned once but can be set at runtime. The value can be determined when the variable is initialized and can be any expression that resolves to a single value.
  - Example: `final String greeting = 'Hello World';` means that `greeting` can be assigned a value once, but that value can be determined at runtime.
In summary, use `const` when you want a constant value known at compile time, and use `final` when you want a variable whose value is set once at runtime but can be calculated based on other factors.

## 5. Implementing To Do List

Sure! Here’s a simplified summary of the project reorganization and widget creation steps:

### Reorganizing the Project Structure

1. **Create `menu.dart`:**
   - Create a new file named `menu.dart` in the `lib` directory.
   - Add the import statement:  
     ```dart
     import 'package:flutter/material.dart';
     ```

2. **Move Classes to `menu.dart`:**
   - Cut `MyHomePage` and `_MyHomePageState` classes from `main.dart` and paste them into `menu.dart`.

3. **Fix Import in `main.dart`:**
   - Add this import at the top of `main.dart` to resolve errors:
     ```dart
     import 'package:mental_health_tracker/menu.dart';
     ```

4. **Run the Application:**
   - Run the project to ensure everything works correctly.

### Creating a Simple Widget in Flutter

**Step 1: Change Application Theme Color**
- In `main.dart`, update the theme color:
  ```
  colorScheme: ColorScheme.fromSwatch(
      primarySwatch: Colors.deepPurple,
  ).copyWith(secondary: Colors.deepPurple[400]),
  ```

**Step 2: Convert `MyHomePage` to Stateless**
- In `main.dart`, change:
  ```
  home: MyHomePage(title: 'Flutter Demo Home Page'),
  ```
  to:
  ```
  home: MyHomePage(),
  ```

- In `menu.dart`, change `MyHomePage` to a stateless widget:
  ```
  class MyHomePage extends StatelessWidget {
      MyHomePage({super.key});
      ...
  }
  ```

**Step 3: Create InfoCard Class**
- Declare variables in `MyHomePage`:
  ```
  final String npm = '5000000000'; // NPM
  final String name = 'Gedagedi Gedagedago'; // Name
  final String className = 'PBP S'; // Class
  ```

- Create `InfoCard` class:
  ```
  class InfoCard extends StatelessWidget {
      final String title;
      final String content;
      const InfoCard({super.key, required this.title, required this.content});
      ...
  }
  ```

**Step 4: Create ItemHomepage Class and ItemCard**
- Create `ItemHomepage` class:
  ```
  class ItemHomepage {
      final String name;
      final IconData icon;
      ItemHomepage(this.name, this.icon);
  }
  ```

- Define a list of items:
  ```
  final List<ItemHomepage> items = [
      ItemHomepage("View Mood", Icons.mood),
      ItemHomepage("Add Mood", Icons.add),
      ItemHomepage("Logout", Icons.logout),
  ];
  ```

- Create `ItemCard` class:
  ```
  class ItemCard extends StatelessWidget {
      final ItemHomepage item;
      const ItemCard(this.item, {super.key});
      ...
  }
  ```

**Step 5: Integrate InfoCard and ItemCard**
- Update the `build` method in `MyHomePage` to display `InfoCard` and `ItemCard`:
  ```
  @override
  Widget build(BuildContext context) {
      return Scaffold(
          appBar: AppBar(title: const Text('Mental Health Tracker')),
          body: Padding(
              padding: const EdgeInsets.all(16.0),
              child: Column(
                  children: [
                      Row(
                          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                          children: [
                              InfoCard(title: 'NPM', content: npm),
                              InfoCard(title: 'Name', content: name),
                              InfoCard(title: 'Class', content: className),
                          ],
                      ),
                      GridView.count(
                          crossAxisCount: 3,
                          shrinkWrap: true,
                          children: items.map((item) => ItemCard(item)).toList(),
                      ),
                  ],
              ),
          ),
      );
  }
  ```

**Final Step: Analyze the Project
- Run the command in the terminal to check for issues:
  ```bash
  flutter analyze
  ```


</details>
