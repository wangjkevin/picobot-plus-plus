# Welcome to Picobot++! 🤏👾

Picobot++ is an improved version of [Picobot](https://www.cs.hmc.edu/picobot/) from Harvey Mudd College, adding functionality for so-called _hashtag commands_.
Hashtag commands enable programmatic control of Picobot's environment, eliminating the need for manual clicks on each cell.

## New and Improved Features

### Hashtag Commands

#### The Basics 🧱

➡️ To add a `Wall` cell at row `X` and column `Y`, use the following command:
```
# add (X,Y)
```
➡️ To delete a `Wall` cell at row `X` and column `Y`, use the following command:
```
# sub (X,Y)
```
➡️ To draw a range of cells, use a _dash_:
```
# add (A-B, C-D)
```
This command draws the cells in rows `A` to `B` from columns `C` to `D`.

#### Star Commands 💫

There are also special _star_ commands, a subset of the hashtag commands. These commands allow you to draw and delete entire lines on the grid.

⭐ To add a line of `Wall` cells on row `X`, use the following command:
```
# add (X,*)
```
To delete a line on row `X`, use the same command, replacing `add` with `sub`.

⭐ To add a line of `Wall` cells on column `Y`, use the following command:
```
# add (*,Y)
```
To delete a line on column `Y`, use the same command, replacing `add` with `sub`.

_(You can think of the `*` as "anything", taking inspiration from RegExes :))_

On that note, you can fill the whole grid like this:
```
# add (*,*)
```
Or delete the whole grid with this:
```
# sub (*,*)
```

#### Dyna Commands 💣

In addition to star commands, there are also _dyna_ commands! Dyna commands allow for _dynamic_ walls.

💥 The `DYNA` keyword appended to the end of a hashtag command turns it into a _dyna_ command. To add a dynamic cell on row `X`, column `Y` to Picobot's world, use the following command:
```
# add (X,Y) DYNA
```

💥 However, you can also alter the duration that the cell appears and disappears by using certain flags, in addition to when the cell shows up. If you want to set the duration to be `A` and the offset to be `B`, use the following command:
```
# add (X,Y) DYNA d=A o=B
```
The duration and offset inputs are based on _rules_, meaning that the cell will toggle on and off every `A` rules, with an offset of `B` rules at the very beginning of Picobot's traversal.
_(Note that the default duration is `25` rules, and the default offset is `0` rules.)_

💥 Dyna commands also work with lines and grids.

💥 `sub` commands work just like the dyna `add` commands, but are inverted. For example, the command
```
# sub (X,*) DYNA d=40
```
will initially turn the line on row `X` _off_ for `40` rule executions, but then toggle the line back on for `40` rule executions, toggle the line off for `40` rule executions, etc.

💥 Dyna commands also work with lines and grids.

#### Examples 🏋🏼

###### Example 1:
```
# add (2-5, 8-9) DYNA d=40 o=3
```
creates a _dynamic_ rectangle of length `4` and width `2` with its top-right corner at row `2`, column `8`. It will stay on the grid for `3` rule executions, and then begin its toggling on/off process, starting by staying on for `40` rule executions, then toggling off, etc.

###### Example 2:
```
# sub (2-5, *)
```
deletes rows `2` through `5`.

###### Example 3:
```
# sub (10-23, *) DYNA
```
creates a _dynamic_ wall that spans rows `10` through `23`. Since there are no flags after the keyword `DYNA`, the default settings are used, meaning that the duration is `25` rules and the offset is `0` rules. The wall will initially be off for `25` rule executions, and then toggle back on again for another `25` rule executions, and so on and so forth.

### Wrap-Around Functionality

Picobot no longer needs any walls at the beginning of every traversal, as it now wraps around once it hits the boundaries of the grid.

## How to Run

To run Picobot++, simply clone the repository using `git clone` and open up the `html` file. We hope you'll have fun guiding Picobot through even weirder, more bizarre worlds! 🎉

_🙌 Many thanks to Prof. Zachary Dodds and many others for the original implementation of Picobot! 🙌_
