Rust scad generator
===

A library for creating openscad models using rust. I created this project partly because I wanted to learn
more about rust and partly because openscad handles variables in a weird way. Variables in a single scope get
assigned the last value they had in that scope at all points in that scope. This means that the following
code

```OpenScad
current_value = 0;
for( i = [0: 3])
{
    current_value = current_value + i;
    echo(current_value);
}
echo(current_value);
```
would print

```
0
1
2
3
0
```
instead of
```
0
1
3
5
5
```
as you would expect in most programming languages.

My library works around this issue by using rust to do all logic and generate simple 
scad code which accomplishes the same thing as more complex scad code would. 

## Usage

Add the following to your cargo.toml.
```
[dependencies]
scad_generator = {git = "https://github.com/TheZoq2/Rust-Scad.git"}
```

And import the crate.
```Rust
#[macro_use]
extern crate scad_generator;
use scad_generator::*;
```

See the documentation for a tutorial.

## Documentation
The documentation  can be found at http://thezoq2.github.io/Rust-Scad/doc/scad_generator/index.html


## Utility repo
Since including dependencies in rust projects using cargo is so simple, I have a repository
with some standard objects like nuts, screws and some RC things like servos in a separate
repo which you can also include using cargo. For now it's undocumented but I will get 
around to that eventually.

[https://github.com/TheZoq2/Rust-scad-util](https://github.com/TheZoq2/Rust-scad-util)
