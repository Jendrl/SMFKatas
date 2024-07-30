# SMF Coding Dojo 08-08-2024 Coding Katas

## Manhattan Distance
Originally Posted At https://kata-log.rocks/manhattan-distance-kata

Manhattan distance is the distance between two points in a grid (like the grid-like street geography of the New York borough of Manhattan) calculated by only taking a vertical and/or horizontal path.

Write a function int manhattanDistance(Point, Point) that returns the Manhattan Distance between the two points.
### Constraints
- The class Point is immutable (its state cannot be changed after instantiation)
- The class Point has no Getters
- The class Point has no public properties (i.e. the internal state cannot be read from outside the class).

## Balanced Parantheses
Originally Posted At https://cyber-dojo.org/creator/choose_problem

Write a program to determine if the parentheses (), the brackets [], and the braces {}, in a string are balanced.

### Constraints
- Single level of indentation
- Short functions, ~ 10 lines

For example:

```
{{)(}} is not balanced because ) comes before (

({)} is not balanced because ) is not balanced between {} and similarly the { is not balanced between ()

[({})] is balanced

{}([]) is balanced

{()}[[{}]] is balanced
```

## LCD Digits
Originally Posted At https://cyber-dojo.org/creator/choose_problem

Your task is to create an LCD string representation of an
integer value using a 3x3 grid of space, underscore, and
pipe characters for each digit. Each digit is shown below
(using a dot instead of a space)

```
._.   ...   ._.   ._.   ...   ._.   ._.   ._.   ._.   ._.
|.|   ..|   ._|   ._|   |_|   |_.   |_.   ..|   |_|   |_|
|_|   ..|   |_.   ._|   ..|   ._|   |_|   ..|   |_|   ..|


Example: 910

._. ... ._.
|_| ..| |.|
..| ..| |_|
```
