# Welcome to Picobot++! 🤏👾

Picobot++ is an improved version of [Picobot](https://www.cs.hmc.edu/picobot/) from Harvey Mudd College, adding functionality for so-called _hashtag commands_.
Hashtag commands allow for programmatic control of Picobot's environment without having to manually click on each cell.

## New and Improved Features

### Hashtag Commands

➡️ To add a `Wall` cell at row `X` and column `Y`, use the following command:
```
# add (X,Y)
```
➡️ To delete a `Wall` cell at row `X` and column `Y`, use the following command:
```
# sub (X,Y)
```

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

### Wrap-Around Functionality

Picobot no longer needs any walls at the beginning of every traversal, as it now wraps around once it hits the boundaries of the grid.

## How to Run

To run Picobot++, simply clone the respository using `git clone` and open up the `html` file. We hope you'll have fun guiding Picobot through even weirder, more bizarre worlds! 🎉

_🙌 Many thanks to Prof. Zachary Dodds and many others for the original implementation of Picobot! 🙌_
