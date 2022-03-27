# Generic XKB configuration and definitions

XKB configuration files are made up of what I'm going to call groups and properties (I'll change them out for the proper names if I find something more definitive).

#### Basics
Comments are c style single-line comments, with "//" starting the comment and the end of the line ending it. c style multi-line comments don't work.

Example:
`// this is a comment, but you've probably already figured this out.`

Whitespace is ignored in most places.
Most lines need to be ended with a semicolon.

#### Measurements are in mm
All measurements (most numerical values) are in mm, with an accuracy of .1mm.
A standard keyboard has 19mm (or 0.75 inches) between the center of two regular keys (which is the same as key width + gap between keys).
I reccomend measuring in mm and rounding to multiples/fractions of 19mm if the keyboard is technically in imperial, since 19mm isn't quite 0.75 inches.

#### Groups
Groups are how things are organized.
They consist of a prefix that can usually be ignored, the keyword, a name in quotes that can be anything (except in certain cases that I'll go over later), and the contents in braces ("{" and "}"), all seperated by spaces.
The contents are properties and more groups (in most cases).
You cannot have two gruops with the same keyword and name in the same group.

Example:
```
xkb_geometry "name" {
    example_property=value;
    example_keyword "another name" {
        another_property = value;
    };
};
```

#### Properties
Properties are essentially just variables that apply to, and change something about, the group they are in. Whitespace directly before or after the `=` is ignored.

Example:
`width = 123;`

You can set a default property for all groups with the same keyword:
```
xkb_geometry "name" {
    example_keyword.example_property = 2;

    example_keyword "aoeu" {
        // insert other stuff here.
        // within this group, example_property is 2.
    };

    example_keyword "asdf" {
        // within this group, example_property is still 2.
    };

    different_keyword "arst" {
        // within this group, example_property is the xkb default
    };

    example_keyword "asht" {
        example_property = 3;
        // within this group, example_property is 3.
    };
};  
```

# Geometry specific structure:

The geometry is entirely contained in a group with the keyword `xkb_geometry`.
The prefix and name are used to select which `xkb_geometry` group to use if there's multiple in the same file.

### Properties
`xkb_geometry` needs to have a `width` and a `height` property for xkbprint to work.
I think they need to be correct, but I haven't checked.

The `description` property is used as the name of the keyboard.

### Keywords
#### General ([more info here](keys.md)):
`shape` and `section`.

Shapes are important to both doodads and keys, and there is no default.
Make sure you have the shapes you want.

Actual keyboard keys are stored in `section`s.

#### [Doodads](doodads.md):
`outline`, `solid`, `text`, `indicator`, and `logo`.

Doodads (official name in the xorg protocol), are where the keyboard really gets interesting.
If your keyboard has any leds, text, case, dark space below the keys, pointing device, card reader, built in calculator, laptop attached to it, etc. (anything that isn't a key), use doodads.

# Example using all valid keywords with each keyword's properties used at least once
[Check here](examples/example.xkb)
