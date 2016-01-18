#The mini Mighty Grid!#

**mini Mighty Grid is 3 grids in one. And all at an overhead of only 1.6k minified without the demo styles! And as low as 323 bytes if you don't need breakpoints!**

- Responsive, 12 column grid
- Responsive, percentage grid based on known percentages
- Responsive, floating point grid with any combination of fractions that total 100%

###Requires###
[Sass](http://sass-lang.com/), CSS extension language.

Note: if you just want the grid with the default breakpoints (480, 768, 960, 1200) and don't want to compile sass, you can grab the mini-mighty-grid.min.css from the css folder and be on your way.

####SCSS Usage####
1. Use SASS to compile `/scss/layout.scss` and export to the css directory. Compiling layout.scss will compile all the mixins and settings into a single css file. You can use whatever method is comfortable for you. The command line might look like `scss --watch layout.scss:../css/layout.css --style compressed`
2. Edit the _site-settings.scss file to suite your needs.

From the `_site-settings.scss` file you can set:
- `$container` Container width for max-width of the grid container
- `$row` Maximum row width (usually 100% of container)
- `$gutter` Gutter width for column based grids. (Can be 0)
- `$breakpoint-map` edit the breakpoints of each screen resolution. (xl should be set to $container width, but can be changed to something else)

The layout.scss file contains some extra settings for responsive breakpoints. If your using sass to compile, you can take advantage of the breakpoint functions that use the breakpoint map. Note: if you are not using sass to compile, then you need to use the standard css @media responsive declarations.
```
@include respond-to(sm) {
    ... small-to-medium styles here...
}
@include respond-to(md) {
    ... medium-to-large styles here...
}
@include respond-to(lg) {
    ... large-to-xlarge styles here...
}
@include respond-to(xl) {
    ... xlarge-and-above styles here...
}
```

####HTML Usage####
**Example of column based layout**

This example would render 1 column for 0 pixels up to medium resolution and 2 columns from medium resolution and above.
```
<div class="content">
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
**Example of percentage based layout**

Unlike the column based grid, the percentage grid doesn't use breakpoints. Instead you must define special classes in your scss/css files and use a special sass function to set teh columns widths.

This example would render a row with the first column 25% width and the second column 75% width.

Note the name of the sass function is colp().

The HTML
```
<div class="content">
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

The sass/css
```
.column-a {
    @include colp(.25);
}
.column-b {
    @include colp(.75);
}
```
**Example of floating point based layout**

The floating point grid works almost exactly like the percentage grid with two exceptions. The widths are expressed in floating point numbers that equal 100% of the total units given and the sass function receives 2 variables. The floating point number and total units.

This example would render a row with the first column 2.4 units out of 7 width and the second column 4.6 units out of 7 width (2.4 + 4.6 = 7 or 100%). You can use any set of units you like as long as the end result is 100% of the 2nd variable.

Note the name of the sass function is colu().

The HTML
```
<div class="content">
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

The sass/css
```
.column-a {
    @include colu(2.4, 7);
}
.column-b {
    @include colu(4.6, 7);
}
```

###100% width layouts###
For 100% width layouts simply use the `.container-fullwidth` style instead of `.container`. This works for all grids.

Example:
```
<div class="content-fullwidth">
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
