struct rectangle:

- we walk throught how to calculate area of recangle and benefit of using struct.

1. we define separate width and height and calcaulte the area of them in this case we need to define width and height to new rectangle as variable and pass them
2. to refactor the above solution we can use Tuple. It will be more clear now an structure but we still need to remmeber the first element is the width and the second one is the height.
3. we can use Struct
   to add more meaning that we define which parameter is the width and which one is the height.
4. we can use methods with struct
   Methods are similar to functions: we declare them with the fn keyword and a name, they can have parameters and a return value, and they contain some code that’s run when the method is called from somewhere else. Unlike functions, methods are defined within the context of a struct, and their first parameter is always self, which represents the instance of the struct the method is being called on.
   we define the methods related to struct using `impl` block which is the implementation of the srtuct and has all associated method related to this struct.

#### Associated Functions

All functions defined within an impl block are called associated functions because they’re associated with the type named after the impl. We can define associated functions that don’t have self as their first parameter (and thus are not methods) because they don’t need an instance of the type to work with.
Associated functions that aren’t methods are often used for constructors that will return a new instance of the struct.

```
impl Rectangle {
    fn square(size: u32) -> Rectangle {
        Rectangle {
            width: size,
            height: size,
        }
    }
}
```

To call this associated function, we use the `::` syntax with the struct name; let sq = Rectangle::square(3);

#### Multiple impl Blocks

Each struct is allowed to have multiple impl blocks

```
impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

impl Rectangle {
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}
```

There’s no reason to separate these methods into multiple impl blocks here, but this is valid syntax.
