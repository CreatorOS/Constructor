# Constructor

A `constructor` is an optional function that is executed upon contract creation.

Some characteristics of a constructor:

- A contract can have only one constructor.
- It is used to initialize state variables of a contract.
- A constructor can be either public or internal.

## Passing parameters to a constructor

Here are examples of how to pass arguments to `constructors`.

```
// Base contract X
contract X {
    string public name;

    constructor(string memory _name) {
        name = _name;
    }
}

// Base contract Y
contract Y {
    string public text;

    constructor(string memory _text) {
        text = _text;
    }
}
```

## Initializing parent contract with parameters

There are 2 ways to initialize parent contract with parameters.

Pass the parameters in the inheritance list.

```
contract BCon is X("Input to X"), Y("Input to Y") {

}
```

Pass the parameters in the constructor, similar to function modifiers.

```
contract CCon is X, Y {
    constructor(string memory _name, string memory _text) X(_name) Y(_text) {}
}
```

## Order of contructor execution

Parent constructors are always called in the order of inheritance regardless of the order of parent contracts listed in the constructor of the child contract.

Order of constructors called:

1. Y
2. X
3. DCon

```
contract DCon is X, Y {
    constructor() X("X was called") Y("Y was called") {}
}
```
