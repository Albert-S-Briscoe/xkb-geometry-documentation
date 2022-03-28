# Generic XKB configuration and definitions

XKB configuration files are made up of what seem to be called elements and variables.

#### Basics
Comments are C style single-line comments, with "//" at the start and a newline at the end. C style multi-line comments don't work.

All whitespace is treated the same outside of strings.

Statements need to be ended with a semicolon.

Element types and variable names are **case insensitive**.

You can use C code highlighting.

#### Measurements are in mm
All measurements (most numerical values) are in mm, with an accuracy of .1mm.
A standard keyboard has 19mm (or 0.75 inches) between the center of two regular keys (which is the same as key width + gap between keys).
I reccomend measuring in mm and rounding to multiples/fractions of 19mm if the keyboard is technically in imperial, since 19mm isn't quite 0.75 inches.

#### Elements
Elements are how things are organized.
They consist of a prefix that can usually be ignored, the element type, a name in quotes that can be anything (except in certain cases that I'll go over later), and the contents in braces ("{" and "}"), all seperated by spaces.
They contain more elements and variables (in most cases).
You cannot have two elements with the same type and name in the same parent element.

Example:
```c
xkb_geometry "name" {
    example_variable=value;
    example_element "another name" {
        another_variable = value;
    };
};
```

#### Variables
Variables apply to, and change something about, the element they are in. Whitespace directly before or after the `=` is ignored.

Example:
`width = 123;`

You can set a default variable for all elements with the same type:
```c
xkb_geometry "name" {
    example_element.example_variable = 2;

    example_element "aoeu" {
        // insert other stuff here.
        // within this element, example_variable is 2.
    };

    example_element "asdf" {
        // within this element, example_variable is still 2.
    };

    different_element_type "arst" {
        // within this element, example_variable is the xkb default
    };

    example_element "asht" {
        example_variable = 3;
        // within this element, example_variable is 3.
    };
};
```

# Geometry specific structure:

The geometry is entirely contained in a element with the element type `xkb_geometry`.
The prefix and name are used to select which `xkb_geometry` element to use if there's multiple in the same file.

### Properties
`xkb_geometry` needs to have a `width` and a `height` variable for xkbprint to work.
I think they need to be correct, but I haven't checked.

The `description` variable is used as the name of the keyboard.

`base_color`
`label_color`
`label_font`

### Element types
#### General ([more info here](keys.md)):
`shape` and `section`.

Shapes are important to both doodads and keys, and there is no default.
Make sure you have the shapes you want.

Actual keyboard keys are stored in `section`s.

#### [Doodads](doodads.md):
`outline`, `solid`, `text`, `indicator`, and `logo`.

Doodads (official name in the xorg protocol), are where the configuration really gets interesting.
If your keyboard has anything that isnt a key like leds, text, a case, dark space below the keys, pointing device, card reader, built in calculator, laptop attached to it, etc., use doodads.

# Example using all valid element types with each type's properties used at least once
[Check here](examples/example.xkb)
