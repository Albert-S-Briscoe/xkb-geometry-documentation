# WIP
Not complete.

# How do I add keys?

Keys are stored in `row`s, which are stored in `section`s.

Example:
```
xkb_geometry "foo" {
    height=123;
    width=234;
    description="name";
    
    shape "bar" // whatever shape gets defined as
    
    section "baz" {
        top = 12;
        left = 34;
        row {
            top = 1; // not required
            left = 2;
            keys {
                <FK01>, <FK02>//, ...
            };
        };
    };
};
```

### Sections

From https://www.x.org/releases/X11R7.7/doc/kbproto/xkbproto.html#Sections:
> Each section has its own coordinate system — if a section is rotated, the coordinates of any components within the section are interpreted relative to the edges that were on the top and left before rotation. The components that make up a section include:
>
> - A list of *rows*. A row is a list of horizontally or vertically adjacent keys. Horizontal rows parallel the (pre-rotation) top of the section and vertical rows parallel the (pre-rotation) left of the section. All keys in a horizontal row share a common top coordinate; all keys in a vertical row share a left coordinate.
>
> - A key description consists of a key *name*, a *shape*, a key *color*, and a *gap*. The key *name* should correspond to one of the keys named in the keyboard names description, the *shape* specifies the appearance of the key, and the key *color* specifies the color of the key (not the label on the key). Keys are normally drawn immediately adjacent to one another from left-to-right (or top-to-bottom) within a row. The *gap* field specifies the distance between a key and its predecessor.
>
> - An optional list of doodads; any type of doodad can be enclosed within a section. Position and angle of rotation are relative to the origin and angle of rotation of the sections that contain them. Priority is relative to the other components of the section, not to the keyboard as a whole.
>
> - An optional list of *overlay keys*. Each overlay key definition indicates a key that can yield multiple scan codes and consists of a field named *under*, which specifies the primary name of the key and a field named *over*, which specifies the name for the key when the overlay keycode is selected. The key specified in *under* must be a member of the section that contains the overlay key definition, while the key specified in over must not. 
