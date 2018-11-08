# The mini Mighty Grid! #

**mini Mighty Grid is 4 grids in one. And all at an overhead of only 2.4k, minified, without the demo styles. And only 51 (fifty-one!) bytes if you don't need a columns grid.**

- Simple Grid: Modern, simplified CSS Grid
- Columns Grid: Responsive-columns, float grid
- Percentage Grid: Responsive, percentage-based, float grid
- Floating Point Grid: Responsive, floating point, float grid

**Why four grids?**

Because designers do crazy things. And crazy things don't always fit into a single grid solution. Not only do each of these grids solve a unique problem, but they can all be used together -- even nested!

## Requires ##

[Sass](http://sass-lang.com/), CSS extension language.

Note: If you just want all the grids with the default breakpoints (0, 480, 768, 960, 1200) and don't want to compile sass, you can download the `/css/layout.min.css` file and be on your way. Or if you don't need a columns grid at all you can do the same for `/css/layout-no-cols.min.css`.

## How To Use ##

You have a choice of 4 different grids. As-is, all are enabled. You can use any one, or any combination of grids together. You can even nest different grids.

Just edit the main `/scss/layout.scss` file to include or remove the components you want. Simple Grid, Percentage Grid and Floating Point Grid all work without any additional includes. But the Columns Grid requires the `/scss/_columns-grid-settings.scss` file to be included.


## The Grids ##

### Simple Grid (css grid) ###

A very basic grid for very basic grid needs. Intended to be a modern replacement for float grids. This implementation of a CSS Grid uses only a small portion of the full range of what CSS Grids are capable of. If you need something more you should create your own custom grid or use this as a jumping off point.

To include the Simple Grid, just include the mixin in your html container element.

Example: `.grid-container {@include simple-grid(1fr 1fr 1fr, auto, 5px, 1em, 768px);}`

Simple Grid takes 5 arguements:
- `$cols`    Columns, can be any value 'grid-template-columns' accepts. Default: 1fr
- `$rows`    Rows, can be any value 'grid-auto-rows' allows. Default: auto **NOTE:** 'auto' will cause all cells, in all rows, to be equal height
- `$gutter`  Gutter, can be any value 'gap' allows. Default: 1rem
- `$margin`  Margin, the outer margin of the grid. Can be any value(s) 'margin' accepts. Default: 0
- `$width`   Max-width, can be any value 'max-width' allows. Default: 100%

**HTML Usage**

```
<article class="grid-container">
    <div>
        <p>
            At vero eos et accusam....
        </p>
    </div>
    <div>
        <p>
            Consetetur sadipscing elitr....
        </p>
    </div>
    <div>
        <p>
            Stet clita kasd gubergren...
        </p>
    </div>
</article>
```

### Columns Grid ###

The columns grid is a classic float grid. It uses rows and columns to create a basic grid layout.

To use it you will need to also include the `/scss/_columns-grid-settings.scss`. In the settings file you can create your breakpoints as well as define the number of columns for the grid.



**HTML Usage**

This example would render 1 column for 0 pixels up to medium resolution and 2 columns from medium resolution and above.

```
<div class="container">
    <div class="row">
        <div class="col-sm-12 col-md-6">
            ...content here...
        </div>
        <div class="col-sm-12 col-md-6">
            ...content here...
        </div>
    </div>
</div>
```

### Percentage Grid ###

Unlike the column based grid, the percentage grid doesn't use breakpoints. Instead you must define special classes in your scss/css files and use a special sass function to set the columns widths.

This example would render a row with the first column 25% width and the second column 75% width.

Note the name of the sass function is colp().

**The HTML**
```
<div class="container">
    <div class="row">
        <div class="column-a">
            ...content here...
        </div>
        <div class="column-b">
            ...content here...
        </div>
    </div>
</div>
```

**The sass/css**
```
.column-a {
    @include colp(.25);
}
.column-b {
    @include colp(.75);
}
```

### Floating Point Grid ###

The floating point grid works almost exactly like the percentage grid with two exceptions. The widths are expressed in floating point numbers that equal 100% of the total units given and the sass function receives 2 variables. The floating point number and total units.

This example would render a row with the first column 2.4 units out of 7 units wide and the second column 4.6 units out of 7 units wide (2.4 + 4.6 = 7 or 100%). You can use any set of units you like as long as the end result is 100% of the 2nd variable.

Note the name of the sass function is `colu()`.

**The HTML**
```
<div class="container">
    <div class="row">
        <div class="column-a">
            ...content here...
        </div>
        <div class="column-b">
            ...content here...
        </div>
    </div>
</div>
```

**The sass/css**
```
.column-a {
    @include colu(2.4, 7);
}
.column-b {
    @include colu(4.6, 7);
}
```

Special thanks to [Francisco](https://github.com/dospuntocero) for the percentage and floating point grids!