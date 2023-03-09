---
layout: post
title: "🐟 Exercises In Digital Discipleship, Puzzle I: Einstein's Riddle"
date: 2023-03-08 01:10:00 -0500
categories: logic riddle einstein
published: true
---


This is an **intermediate** exercise written for the digital discipleship program created by SevenShepherd. If you are new or haven't gone through our fundamentals course, you may want to check that out before attempting to understand this exercise.

This is a fun puzzle that was allegedly created by Albert Einstein as a boy. Einstein said that only 2% of the world could solve it. Considering that there are 5!^5 or 24,883,200,000 combinations with only 1 correct solution, you might find the task daunting but I can assure you that anyone who has gone through our class successfully can understand all 3 solutions below.

# **Riddle**

1. There are 5 houses in five different colors.
2. In each house lives a person with a different nationality.
3. These five owners drink a certain type of beverage, smoke a certain brand of cigar and keep a certain pet.
4. No owners have the same pet, smoke the same brand of cigar or drink the same beverage.

The question is: ***Who owns the fish?*** 🐟

# **Hints**

1. the Brit lives in the red house
2. the Swede keeps dogs as pets
3. the Dane drinks tea
4. the green house is on the left of the white house
5. the green house's owner drinks coffee
6. the person who smokes Pall Mall rears birds
7. the owner of the yellow house smokes Dunhill
8. the man living in the center house drinks milk
9. the Norwegian lives in the first house
10. the man who smokes blends lives next to the one who keeps cats
11. the man who keeps horses lives next to the man who smokes Dunhill
12. the owner who smokes BlueMaster drinks beer
13. the German smokes Prince
14. the Norwegian lives next to the blue house
15. the man who smokes blend has a neighbor who drinks water

<span style="font-style:Italic;font-size:32px;">My Pencil & Paper Solution</span>

- `Hints: 8,9,14`
We can see that the Norwegian lives in the first house and that he lives next to the blue house. We also learn here that the owner who lives in the center house drinks milk.

| ???           | **Blue** | ???      | ??? | ??? |
| **Norwegian** | ???      | ???      | ??? | ??? |
| ???           | ???      | **Milk** | ??? | ??? |
| ???           | ???      | ???      | ??? | ??? |
| ???           | ???      | ???      | ??? | ??? |

- `Hints: 4,5`
Since the owner of the green house drinks coffee he cannot be the owner in the center.
That leaves the `first`, `fourth`, and `fifth` positions open, however in hint #5 we see that he
lives on the left of the house that is white so "Mr. Green" cannot be `first` either.
That leaves position `four`, and `five`. The last deduction is that he must live in the `forth` house
because the `fifth` position isn't left of anything. 

| ???           | Blue  | ???      | **Green**  | **White** |
| Norwegian     | ???   | ???      | ???        | ???       |
| ???           | ???   | Milk     | **Coffee** | ???       |
| ???           | ???   | ???      | ???        | ???       |
| ???           | ???   | ???      | ???        | ???       |

- `Hint: 1`
If the Norwegian lives in the first house and the Brit lives in the red house then that places
the `red house square in the center`. This means the `Norwegian lives in the yellow house`.

| **Yellow**    | Blue  | **Red**  | Green  | White |
| Norwegian     | ???   | **Brit** | ???    | ???   |
| ???           | ???   | Milk     | Coffee | ???   |
| ???           | ???   | ???      | ???    | ???   |
| ???           | ???   | ???      | ???    | ???   |

- `hint: 15`
The man who smokes blends lives next to someone who drinks water, this hint eliminates 
the white house, leaving either `yellow` or `blue`.

- `Hint: 7`
The `Norwegian smokes Dunhill` so this bring us back to hint 15, if the Norwegian smokes Dunhill and not blends, only the owner of the `blue house smokes blends`. Let's not forget that the man who
smokes blends also lives next to someone who drinks water, and since the Brit drinks milk, we can deduce that the `Norwegian drinks water`.

| Yellow      | Blue       | Red  | Green  | White |
| Norwegian   | ???        | Brit | ???    | ???   |
| **Water**   | ???        | Milk | Coffee | ???   |
| **Dunhill** | **Blends** | ???  | ???    | ???   |
| ???         | ???        | ???  | ???    | ???   |

- `Hint: 11`
We see here that the owner who keeps the horses lives next to the man who smokes Dunhill.

| Yellow    | Blue       | Red  | Green  | White |
| Norwegian | ???        | Brit | ???    | ???   |
| Water     | ???        | Milk | Coffee | ???   |
| Dunhill   | Blends     | ???  | ???    | ???   |
| ???       | **Horses** | ???  | ???    | ???   |

- `Hint: 12`
If the owner who smokes BlueMaster drinks beer, only `Blue & White` are possible houses.
Since the owner of the blue house already smokes blends, we have deduced that the owner of
the `white house smokes BlueMaster and drinks beer`

- It looks as though through process of elimination we've also deduced that the owner of the `blue
house drinks tea`.

- `Hint: 3`
The Dane happens to drink tea

| Yellow    | Blue     | Red  | Green  | White            |
| Norwegian | **Dane** | Brit | ???    | ???              |
| Water     | **Tea**  | Milk | Coffee | **Beer**         |
| Dunhill   | Blends   | ???  | ???    | **BlueMaster** |
| ???       | Horses   | ???  | ???    | ???              |

- `Hint: 2, 13`
The German smokes Prince, he must live in the green house since white smokes BlueMaster and the
other houses are already occupied (i.e. Red -> Brit), ergo the `German lives in the green house`.

- Process of elimination has also revealed that the remaining race left is the Swede, therefore the
`Swede must live in the white house`.

- `Hint: 2`
The Swede keeps dogs as pets

| Yellow    | Blue   | Red  | Green      | White      |
| Norwegian | Dane   | Brit | **German** | **Swede**  |
| Water     | Tea    | Milk | Coffee     | Beer       |
| Dunhill   | Blends | ???  | **Prince** | BlueMaster |
| ???       | Horses | ???  | ???        | **Dogs**   |

- Yet another process of elimination on who smokes what, reveals one spot left for Pall Mall.
`The Brit must smoke Pall Mall`.

- `Hint: 6`
We also find in hint #6 that the person who smokes Pall Mall also rears birds. `The Brit rears birds`.

| Yellow    | Blue   | Red           | Green  | White      |
| Norwegian | Dane   | Brit          | German | Swede      |
| Water     | Tea    | Milk          | Coffee | Beer       |
| Dunhill   | Blends | **Pall Mall** | Prince | BlueMaster |
| ???       | Horses | **Birds**     | ???    | Dogs       |

- `Hint: 10`
For our final clue, we learn that the individual who smokes blends lives next to the one who keeps cats. `We find that not only is it the Norwegian who keeps cats`, but through process of elimination we have solved the final piece of the puzzle, and that is that `the German owns the fish`!

| Yellow    | Blue   | Red       | Green    | White      |
| Norwegian | Dane   | Brit      | German   | Swede      |
| Water     | Tea    | Milk      | Coffee   | Beer       |
| Dunhill   | Blends | Pall Mall | Prince   | BlueMaster |
| **Cats**  | Horses | Birds     | **Fish** | Dogs       |

So there you have it, the German owns the fish. This was an article I wrote on WordPress
back in 2016, but I had worked out the solution some years earlier on paper.

<span style="font-style:Italic;font-size:32px;">Programmatic Solution (Permutation)</span>

If we are going to solve a problem we need to recognize that it has variables and that those variables need 
a data structure to exist in so we can manipulate these variables into a proper solution. Lets store them in a dictionary of lists.

```python
variables = {
    'colors' : ['red'     , 'green'  , 'white' , 'yellow'    , 'blue'  ],
    'races'  : ['brit'    , 'swede'  , 'dane'  , 'norwegian' , 'german'],
    'drinks' : ['tea'     , 'coffee' , 'milk'  , 'beer'      , 'water' ],
    'smokes' : ['pallMall', 'dunhill', 'blends', 'blueMaster', 'prince'],
    'pets'   : ['dogs'    , 'birds'  , 'cats'  , 'horses'    , 'fish'  ]
}
```

Next we'll be defining our constraints, the basic rules that govern the position and associated items that we will use to bruteforce our solution. If two items are related to one another, for instance hint #1 which states that the brit lives in the red house, we say that they are equal mathematically. When we attempt to bruteforce the answer, we will be crunching number representations of each list. 

```python
equals  = lambda a,b: True if a == b else False
next_to = lambda a,b: True if a == b - 1 or a == b + 1 else False
left_of = lambda a,b: True if a == b - 1 else False
```

In order to fully comprehend the following snippet of code, we must first understand De Morgan's theorem. These laws are used in propositional logic, Boolean algebra, simplification of logical expressions in computer programs and digital circuit designs.

> "the negation of a disjunction is the conjunction of the negations; and <br>
the negation of a conjunction is the disjunction of the negations;" ― [Wikipedia](https://en.wikipedia.org/wiki/De_Morgan%27s_laws)


```python
( not True and not False ) == ( not (True or  False) )
( not True or  not False ) == ( not (True and False) )
```

We will use the aforementioned laws to reduce the verbosity of the resulting code below. In essence we are bruteforcing permutations against constraints defined in the lambda functions.

```python
perm = list(permutations(range(1, 5+1)))
for red, green, white, yellow, blue in perm:
    if not left_of(green, white):
        continue
    for brit, swede, dane, norwegian, german in perm:
        if not ( equals(brit, red) and next_to(norwegian, blue) ):
            continue
        for tea, coffee, milk, beer, water in perm:
            if not ( equals(dane, tea) and equals(green, coffee) and \
                     milk == 3         and norwegian == 1 ):
                continue
            for pallMall, dunhill, blends, blueMaster, prince in perm:
                if not ( equals(yellow, dunhill) and equals(blueMaster, beer) and \
                         equals(german, prince)  and next_to(blends, water) ):
                    continue
                for dogs, birds, cats, horses, fish in perm:
                    if not ( equals(swede, dogs)   and equals(pallMall, birds) and \
                             next_to(blends, cats) and next_to(horses, dunhill) ):
                        continue
                    ...
```

We could also negate the python keyword **all** to achieve the same effect. 

```python
perm = list(permutations(range(1, 5+1)))
for red, green, white, yellow, blue in perm:
    if not left_of(green, white):
        continue
    for brit, swede, dane, norwegian, german in perm:
        if not all([equals(brit, red), next_to(norwegian, blue)]):
            continue
        for tea, coffee, milk, beer, water in perm:
            if not all([ equals(dane, tea), equals(green, coffee), 
                         milk == 3, norwegian == 1 ]):
                continue
            for pallMall, dunhill, blends, blueMaster, prince in perm:
                if not all([ equals(yellow, dunhill), equals(blueMaster, beer), 
                             equals(german, prince), next_to(blends, water) ]):
                    continue
                for dogs, birds, cats, horses, fish in perm:
                    if not all([ equals(swede, dogs), equals(pallMall, birds), 
                                 next_to(blends, cats), next_to(horses, dunhill) ]):
                        continue
                    ...
```
It's important to realize why we can't just test the constraints under the final nested iterative loop.
If we attempted to do that, it could take a very long time to compute the answer. Imagine if `left_of(green, white)` was in the last loop instead of the first, we wouldn't have hit the continue in the first iterative loop and instead we would have had to go through all the permutations of each subsequent loop after the first just to check the constraint that should have ended all the unnecessary iterations. By placing the constraints in the highest loop that supports their variables, we save massive amounts of time.

When we reach a solution by bruteforcing all the permutations above, we will have arrived at our solution. This solutions data structure will look something like this if it were printed out:

```python
print(
    [red     , green  , white , yellow    , blue  ],
    [brit    , swede  , dane  , norwegian , german],
    [tea     , coffee , milk  , beer      , water ],
    [pallMall, dunhill, blends, blueMaster, prince],
    [dogs    , birds  , cats  , horses    , fish  ]
)

[3, 4, 5, 1, 2] [3, 5, 2, 1, 4] [2, 4, 3, 5, 1] [3, 1, 2, 5, 4] [5, 3, 1, 2, 4]
```

Our next step is to associate the solved positions with their string counterparts into something that looks more like this:

```python
(
    [ ('red'     , 3), ('green'  , 4), ('white' , 5), ('yellow'    , 1), ('blue'  , 2) ]
    [ ('brit'    , 3), ('swede'  , 5), ('dane'  , 2), ('norwegian' , 1), ('german', 4) ]
    [ ('tea'     , 2), ('coffee' , 4), ('milk'  , 3), ('beer'      , 5), ('water' , 1) ]
    [ ('pallMall', 3), ('dunhill', 1), ('blends', 2), ('blueMaster', 5), ('prince', 4) ]
    [ ('dogs'    , 5), ('birds'  , 3), ('cats'  , 1), ('horses'    , 2), ('fish'  , 4) ]
)
```
We can accomplish this with a simple lambda expression which combines the strings found in the corresponding variables dictionary in their old order configuration with the newly ordered values we just bruteforced. The reason we do this is so we can sort the list into its proper arrangement, we then immediately discard the position as it is no longer needed once the string is sorted.

```python
g = lambda oldLst,newPos: [i for i,j in sorted(zip(oldLst, newPos), key=lambda x: x[1])]
```
The resulting data structure from the list comprehension will produce a list of tuples filled with the strings in their proper order. We just simply need to print them out by iterating over the solved positions.

```python
for (k,v), new in zip(variables.items(), (
    [red     , green  , white , yellow    , blue  ],
    [brit    , swede  , dane  , norwegian , german],
    [tea     , coffee , milk  , beer      , water ],
    [pallMall, dunhill, blends, blueMaster, prince],
    [dogs    , birds  , cats  , horses    , fish  ]
)):
    print("{:6s}: {:10s} {:10s} {:10s} {:10s} {:10s}".format(k, *g(v, new)))
```

Full program & output

{% highlight python %}
from itertools import permutations

def main():
    variables = {
        'colors' : ['red'     , 'green'  , 'white' , 'yellow'    , 'blue'  ],
        'races'  : ['brit'    , 'swede'  , 'dane'  , 'norwegian' , 'german'],
        'drinks' : ['tea'     , 'coffee' , 'milk'  , 'beer'      , 'water' ],
        'smokes' : ['pallMall', 'dunhill', 'blends', 'blueMaster', 'prince'],
        'pets'   : ['dogs'    , 'birds'  , 'cats'  , 'horses'    , 'fish'  ]
    }

    equals  = lambda a,b: a == b
    next_to = lambda a,b: a == b - 1 or a == b + 1
    left_of = lambda a,b: a == b - 1
                        
    perm = list(permutations(range(1, 5+1)))
    for red, green, white, yellow, blue in perm:
        if not left_of(green, white):
            continue
        for brit, swede, dane, norwegian, german in perm:
            # if not ( equals(brit, red) and next_to(norwegian, blue) ):
            if not all([equals(brit, red), next_to(norwegian, blue)]):
                continue
            for tea, coffee, milk, beer, water in perm:
                # if not ( equals(dane, tea) and equals(green, coffee) and \
                #          milk == 3         and norwegian == 1 ):
                if not all([ equals(dane, tea), equals(green, coffee), 
                             milk == 3, norwegian == 1 ]):
                    continue
                for pallMall, dunhill, blends, blueMaster, prince in perm:
                    # if not ( equals(yellow, dunhill) and equals(blueMaster, beer) and \
                    #          equals(german, prince)  and next_to(blends, water) ):
                    if not all([ equals(yellow, dunhill), equals(blueMaster, beer), 
                                 equals(german, prince), next_to(blends, water) ]):
                        continue
                    for dogs, birds, cats, horses, fish in perm:
                        # if not ( equals(swede, dogs)   and equals(pallMall, birds) and \
                        #          next_to(blends, cats) and next_to(horses, dunhill) ):
                        if not all([ equals(swede, dogs), equals(pallMall, birds), 
                                     next_to(blends, cats), next_to(horses, dunhill) ]):
                            continue

                        g = lambda oldLst,newPos: [i for i,j in sorted(zip(oldLst, newPos), key=lambda x: x[1])]
                        
                        # iterate through the solved positions sorting each tuple of solutions as we print
                        for (k,v), new in zip(variables.items(), (
                            [red     , green  , white , yellow    , blue  ],
                            [brit    , swede  , dane  , norwegian , german],
                            [tea     , coffee , milk  , beer      , water ],
                            [pallMall, dunhill, blends, blueMaster, prince],
                            [dogs    , birds  , cats  , horses    , fish  ]
                        )):
                            print("{:6s}: {:10s} {:10s} {:10s} {:10s} {:10s}".format(k, *g(v, new)))

if __name__ == "__main__":
    main()
{% endhighlight %}

```
colors: yellow     blue       red        green      white
races : norwegian  dane       brit       german     swede
drinks: water      tea        milk       coffee     beer
smokes: dunhill    blends     pallMall   prince     blueMaster
pets  : cats       horses     birds      fish       dogs
```

<span style="font-style:Italic;font-size:32px;">Programmatic Solution (Constraint Based)</span>

Lets attempt to write a constraint based python program to solve Einstein's Riddle.
Constraint programming is a `declarative programming paradigm` that focuses on `what` to execute
rather than `how` to execute (imperative). 

Firstly, install python-constraint module.

```
$ pip install python-constraint
```

Import the necessary requirements and create the solver object, assigning it to a variable call problem.

```python
from constraint import *

problem = Problem()
```

Using the same variables dictionary structure as before, we iterate over each list, and associate a value 1-5 subsequently to each item of the list using the built in `addVariables()` method. We apply exclusivity to each list by applying the constraint `AllDifferentConstraint()` with `addConstraint()`.

```python
for values in variables.values():
    problem.addVariables(values, range(1,5+1))
    problem.addConstraint(AllDifferentConstraint(), values)
```

Our next goal is to apply the logic of the constraints via lambda functions to each association.

```python
# constraints: equal
for i in (
    ["brit"      , "red"  ], ["swede" , "dogs"   ],
    ["dane"      , "tea"  ], ["green" , "coffee" ],
    ["pallMall"  , "birds"], ["yellow", "dunhill"],
    ["blueMaster", "beer" ], ["german", "prince" ]
):
    problem.addConstraint(lambda a, b: a == b, i)

# constraints: next_to
for i in (
    ["blends"   , "cats"], ["horses", "dunhill"],
    ["norwegian", "blue"], ["blends", "water"  ]
):
    problem.addConstraint(lambda a, b: a == b - 1 or a == b + 1, i)

# constraints: left_of, middle, first
problem.addConstraint(lambda a, b: a == b - 1, ["green"    , "white"])
problem.addConstraint(lambda a: a == 3       , ["milk"              ])
problem.addConstraint(lambda a: a == 1       , ["norwegian"         ])
```

To retrieve the solution all that needs to be done is to call the method `getSolution()` upon the problem object.

```python
solution = problem.getSolution()
```

The data structure returned is in dictionary form, we will need to format the output.

```python
{
    'blends'    : 2, 'dunhill': 1, 'green' : 4, 'coffee': 4, 'horses'    : 2, 
    'norwegian' : 1, 'blue'   : 2, 'white' : 5, 'yellow': 1, 'red'       : 3, 
    'brit'      : 3, 'cats'   : 1, 'water' : 1, 'beer'  : 5, 'blueMaster': 5, 
    'pallMall'  : 3, 'birds'  : 3, 'prince': 4, 'german': 4, 'dane'      : 2, 
    'swede'     : 5, 'dogs'   : 5, 'tea'   : 2, 'fish'  : 4, 'milk'      : 3
}
```

This solution has given us the groups by number. For instance group 1 contains dunhill, norwegian, yellow, cats, and water; all we have to do is place the strings in each group in an order we decide.

```python
def order(key):
    for position, array in enumerate(variables.values()):
        if key in array:
            return position

ordered = [ 
    sorted([ k for k,v in solution.items() if v == i], key=lambda x: order(x) ) 
        for i in range(1, max(solution.values())+1)
]
```

Now that we have the data organized into their respective groups, all we have to do now is swap columns for rows.

```python
[
    ['yellow', 'norwegian', 'water' , 'dunhill'   , 'cats'  ], 
    ['blue'  , 'dane'     , 'tea'   , 'blends'    , 'horses'], 
    ['red'   , 'brit'     , 'milk'  , 'pallMall'  , 'birds' ], 
    ['green' , 'german'   , 'coffee', 'prince'    , 'fish'  ], 
    ['white' , 'swede'    , 'beer'  , 'blueMaster', 'dogs'  ]
]
```

There's a few ways we can accomplish this, one way is to use numpy `np.array(ordered).T.tolist()`, the other is to use a pandas `DataFrame()`.

```python
df = pd.DataFrame(
    ordered,
    index   = ["first" , "second", "third"  , "fourth" , "fifth"],
    columns = ["color:", "race:" , "smokes:", "drinks:", "pets:"]
).transpose()
```

Personally i'd like to avoid added overhead by creating my own solution to transpose.

```python
# transpose & format output
for i in map(list, zip(*ordered)):
    print("{:10s} {:10s} {:10s} {:10s} {:10s}".format(*i))
```

Full program & output

{% highlight python %}
from constraint import *

def main():
    problem = Problem()

    variables = {
        'houses' : ['red'     , 'green'  , 'white' , 'yellow'    , 'blue'  ],
        'races'  : ['brit'    , 'swede'  , 'dane'  , 'norwegian' , 'german'],
        'drinks' : ['tea'     , 'coffee' , 'milk'  , 'beer'      , 'water' ],
        'smokes' : ['pallMall', 'dunhill', 'blends', 'blueMaster', 'prince'],
        'pets'   : ['dogs'    , 'birds'  , 'cats'  , 'horses'    , 'fish'  ]
    }

    # addVariables: each list gets numbered 1 - 5
    # addConstraint: apply exclusivity
    for values in variables.values():
        problem.addVariables(values, range(1,5+1))
        problem.addConstraint(AllDifferentConstraint(), values)

    # constraints: equal
    for i in (
        ["brit"      , "red"  ], ["swede" , "dogs"   ],
        ["dane"      , "tea"  ], ["green" , "coffee" ],
        ["pallMall"  , "birds"], ["yellow", "dunhill"],
        ["blueMaster", "beer" ], ["german", "prince" ]
    ):
        problem.addConstraint(lambda a, b: a == b, i)

    # constraints: next_to
    for i in (
        ["blends"   , "cats"], ["horses", "dunhill"],
        ["norwegian", "blue"], ["blends", "water"  ]
    ):
        problem.addConstraint(lambda a, b: a == b - 1 or a == b + 1, i)

    # constraints: left_of, middle, first
    problem.addConstraint(lambda a, b: a == b - 1, ["green"    , "white"])
    problem.addConstraint(lambda a: a == 3       , ["milk"              ])
    problem.addConstraint(lambda a: a == 1       , ["norwegian"         ])

    solution = problem.getSolution()

    def order(key):
        for position, array in enumerate(variables.values()):
            if key in array:
                return position

    ordered = [ 
        sorted([ k for k,v in solution.items() if v == i], key=lambda x: order(x) ) 
            for i in range(1, max(solution.values())+1)
    ]

    # transpose & format output
    for i in map(list, zip(*ordered)):
        print("{:10s} {:10s} {:10s} {:10s} {:10s}".format(*i))


if __name__ == "__main__":
    main()
{% endhighlight %}

```
yellow     blue       red        green      white
norwegian  dane       brit       german     swede
water      tea        milk       coffee     beer
dunhill    blends     pallMall   prince     blueMaster
cats       horses     birds      fish       dogs
```