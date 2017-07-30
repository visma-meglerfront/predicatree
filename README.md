# PredicaTree

This is a (somewhat) lightweight library to parse and execute predicate-based structure algorithms.

A useful application example is dynamic sorting.

## Installation

Add this to `composer.json`:

```json
"require": {
	"adeptoas/predicatree": "^1.0.0"
}
```

Make sure to merge your `require`-blocks!

## Usage

Currently only supports sorting.

### Sorting

Sorting programs are generated by `SortProgram::build(array $data)`.

The data array is specified as follows:
```php
[
    'apriori'       =>  ['a generic array with whatever knowledge you want to equip sorting with'],
    'collection'    =>  [
        'a collection specifier (see section below)'
    ],
    'predicates'    =>  [
        'a sequential list',
        'of if-then predicates',
        'just as specified below'
    ]
]
```

Sorting can then be executed via `$program->sort(Collection $collection)` and returns a sorted collection
according to the specified `predicates`.

### Collections

In order to sort stuff, you have to give it order. Therefor, this library contains some collection types.
Features basic sort operations like `add`, `remove`, `move` and will be explained in detail when I feel like it

Collections are specified by their type (currently `Dictionary` and `OrderedSet`) and their items like so:
```php
[
    'type'  =>  'OrderedSet',
    'items' =>  [1, 3, 7, 9, 11]
]
```

### Predicates

Predicates represent the `if-then` rules in this package, and are specified as follows:
```php
[
    'if'    =>  [
        'operand'   =>  'SOME_OPERAND',
        'operators' =>  ['all', 'operators', 'for', 'the', 'operand']
    ],
    'then'  =>  [
        'method'    =>  'someCollectionMethod',
        'arguments' =>  ['all', 'methods', 'for', 'the', 'method']
    ]
]
```

Currently features operands:
- `EQUAL`, which takes two (obvious) arguments (plus an optional third boolean for strict comparison)
- `NOT`, which takes a fully specified predicate (as array) as its only argument to negate. Attention: Sequential array with one argument formatted as array means double array braces!!

Currently features methods:
- Everything listed as public in `Collection` class

## Examples

Examples will be added to the `Examples/` directory once I come up with meaningful examples that don't involve confidential data from my dayjob.