# Grid world Lab 1
## Exercise 2: Identity Loss - Part 2

This is a direct continuation from last weeks lab sheet, and will focus on actually finding the identity of the actor, now that we have gathered all the links.

### Possible Queries

The same queries have been exported as in exercise 2 part 1:

| Predicate				   						| Meaning                                                               				|
|-----------------------------------------------|---------------------------------------------------------------------------------------|
| `actor(-Actor)`								| return each possible secret actor identity  (e.g. `'Billy Bob Thornton'`)		|
| `wp(+Title,-WikiText)`					| connect to Wikipedia page with given Title and return its WikiText    				|
| `wp(+Title)`								| connect to Wikipedia page with given Title  and print its WikiText 					|
| `wt_link(+WikiText, -Link)`				| return any Link contained in the given WikiText										|
| `agent_ask_oracle(+A, +Orac,+Qu,-Ans)`| This is used to question the oracle. If the Agent's Question is `link` then the Oracle's Answer will be a random link from the Wikipedia page whose title is the (name of the) secret random actor identity |
| `test`										| test if `find_identity/1` successfully returns correct identity in all possible cases	|

### How to run?

Run using `swipl ./ailp.pl lab identity` 

The file `lab_identity_12345.pl` will automatically be consulted and should be the place that your work is done. There is no need to follow the steps to start the webserver this time (although once you have created `find_identity/1` you can use `test/0` to check that your solution works).

### Create predicate `find_links_by_actor/2`

If you haven't already, then you need to create a predicate that finds all the links on a given actors wikipedia page. This predicate will take the form of `find_links_by_actor(+Actor,-Links)`. 

### Create predicate `find_identity/1`

For the next stage, we need to implement `find_identity(-Actor)` to discover the secret actor (which is randomly chosen each time the program is run). `find_identity/1` will use `agent_ask_oracle(oscar,o(1),link,L)` to gain a link `L` that belongs to the secret actor. This link can be used to eliminate certain actors until eventually there is only one possible actor left. Make sure that `find_identity/1` is deterministic (it only returns one answer)!

**WARNING** - Make sure that your definition of `find_identity/1` is not trivially true, (i.e. it's not just true for any possible A)

TIP - The use of `findall/3`, `bagof/3` or `include/3` is reccomended.

## Exercise 3: Breadth first search

For the final prolog exercise, you will need to implement a breadth first search in order to find an oracle (shown as a red square). A breadth first search is a slow algorithm but will always find the shortest path. This exercise may be tough, but assuming you have completed the other exercises, then you will be able to do it! (there is also plenty of support on offer from TA's, staff and your peers!). For this exercise you will be editing `lab_search_12345.pl`.

### Possible Queries

The exported queries for this exercise are the same as exercise 1, except map_adjacent is now also exported. See below for list:

| Query Name                      | Description                                     |
|---------------------------------|-------------------------------------------------|
| start                           | Initiate the web server                         |
| shell                           | Open the command shell                          |
| my_agent(-A)                    | Returns the ID of your Agent                    |
| ailp_grid_size(-N)              | Returns the size of the grid                    |
| get_agent_position(+A,-Pos)     | Returns the position of Agent A                 |
| agent_do_moves(+A,+L)           | Makes Agent A perform the list of moves L       |
| **map_adjacent(+Pos,?AdjPos,?OID)** | **Returns positions adjacent to Pos and their OID** |


### How to run

Run using `swipl ./ailp.pl lab search`. The file `lab_search_12345.pl` will automatically be consulted and should be the place that your work is done. 

This time you will need to follow the steps from exercise 1 to run the webserver (`start.`, click run on the website, `shell.`, `setup.`). You can use `search.` while in the shell as a shortcut for typing `search_bf` outside of the shell.

### Exploring `map_adjacent/3`

After you have loaded the exercise you will notice that you are now in a more complicated version of the world from exercise 1. The world is randomly generated at runtime but will have at most 25 Walls (in black) and exactly 1 oracle (in red). Not every world will be solvable, and if it's not then your predicate should just fail!

The query `map_adjacent(+Pos,?AdjPos,?OID)` must receive a `Pos` although it is optional whether or not to give an `AdjPos`/`OID`. `OID` will always be a member of `[agent, empty, t(X),o(X)]`.

For this section, try to write queries in your terminal that:
    
1. Find all the adjacent cells around position P (giving multiple solutions)
2. Find all the adjacent cells around position P
(as a List) 
3. Find **ONLY** the empty cells around position P
4. Find the empty cells next to your agent
5. Find the OID of the oracle

NOTE: These queries don't need to work generally, it is enough that they only work in your current version of the grid (i.e, it is ok to instantiate things like P)

### Create predicate `complete/1`

As the goal of the task is to move next to an oracle, the predicate `complete(+Pos)` must be defined in order to know when the task is done. This predicate should be true if the position is adjacent to an oracle

### Create the predicate `search_bf/0`

You need to implement `search_bf/0` as well as any other supporting predicates that you want to use. `search_bf.` should use a breadth first search to navigate the agent to the oracle. This is a more complex task than previous but these tips should help guide you:  

- You may want to find the path to the oracle and then make all the moves at once using `agent_do_moves/2`.
- Remember that move lists given to `agent_do_moves/2` **DO NOT** include the current position at the start 
- Keeping track of which cells have already been visited will make sure that you don't check cells multiple times.
- Test often, And use `trace/0` if you aren't sure why something isn't working.
- Don't be afraid to ask for help!