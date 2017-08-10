# bs-glamor – [BuckleScript](https://github.com/bloomberg/bucklescript) bindings for [glamor](https://github.com/threepointone/glamor)

The API is still **experimental**. Only the `css` function from glamor is exposed (with its result slightly incorrectly typed as a `string`); no other functions such as `renderStatic` are supported yet.

## Installation

```sh
npm install --save bs-glamor
```

In your `bsconfig.json`, include `"bs-glamor"` in the `bs-dependencies`.

## Usage

The following examples (in [Reason](https://facebook.github.io/reason) syntax) assume that `Glamor` is included in the namespace:

```reason
open Glamor;
```

* Simple styling:

    ```reason
    css [
        color "red",
        border "1px solid black"
    ]
    ```

* Styling with selectors (`@media`, `:hover`, `&`, etc.):

    ```reason
    css [
        color "red",
        Selector "@media (min-width: 300px)" [
            color "green"
        ]
    ]
    ```

* Selectors can be nested:

    ```reason
    css [
        color "red",
        Selector "@media (min-width: 300px)" [
            color "green",
            Selector "& .foo" [
                color "blue"
            ]
        ]
    ]
    ```
    
You can also combine stylings with a class names. For example if you want to use 
some class from third party libraries, like Bootstrap, and add your own classes, or just 
add a classname for test purposes along with glamor styles:

     ```reason
     <div className=("btn " ^ css [color "red"]) />
     ```

You can isolate inclusion of the `Glamor` namespace in the following way:

```reason
Glamor.(css [color "red"])
```

The result of the `css` function can be assigned to a class name, e.g. in JSX:

```reason
<div className=(css [color "red"]) />
```

## Example

See [reason-react-tictactoe](https://github.com/poeschko/reason-react-tictactoe) for a live example.

## Development

```sh
npm run start
```

### Tests

There are some simplistic tests using [bs-jest](https://github.com/BuckleTypes/bs-jest).

```sh
npm run test
```

## Thanks

Thanks to [reason-react-example](https://github.com/chenglou/reason-react-example), [reason-react](https://github.com/reasonml/reason-react), and [bs-jest](https://github.com/BuckleTypes/bs-jest) for inspiration how to create a Reason library, and of course, thanks to [glamor](https://github.com/threepointone/glamor).
