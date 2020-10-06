# Artificial Intelligence Prolog Labs

## Exercise 1: Intro to the grid world

Hello! Welcome to Week 2/3 of Artificial Intelligence. Congratulations for making it through Week 1. In this exercise you will be introduced to the grid world, learn how to move around it and ultimately create a spiral. For this exercise you will be editing `lab_grid_12345.pl`.

### Possible Queries 

The following queries have been exported from the library code:

| Query Name                  | Description                               |
|-----------------------------|-------------------------------------------|
| start                       | Initiate the web server                   |
| shell                       | Open the command shell                    |
| my_agent(-A)                | Returns the ID of your Agent              |
| ailp_grid_size(-N)          | Returns the size of the grid              |
| get_agent_position(+A,-Pos) | Returns the position of Agent A           |
| agent_do_moves(+A,+L)       | Makes Agent A perform the list of moves L |

### How to run?

**PLEASE READ THIS SECTION**. In order to run the grid world, you need to open `ailp.pl` using swipl. This exercise is known as `lab grid` so we will pass that as a command line argument (e.g. `swipl ailp.pl lab grid`).
 
Upon loading you will likely see a lot of warnings
about singleton variables. this is normal and only because the functions in `lab_grid_12345.pl` have not been implemented. 

Next, Type in `start.` and hit enter to start the webserver. If you press anything but 'N'/'n', then the webpage will open automatically in your default browser. **Hit the run button on the webpage before you continue.**

We will use a shell to initialise the grid so type in `shell.` and then `setup.` in the following command prompt. (While the main prolog prompt is `?-`, in the shell it will look like `?`).

After the `setup/0` has finished, you can exit the shell using either `stop.`,`CTRL+D` or `CTRL+C` then (a)bort at the prompt.

### Identifying your Agent

At the top left of the grid, you will be able to see a coloured shape. This is your agent. For the first task in this exercise, you need to find a query that allows you to identify your agent and their current position and run it in the shell.

### Create predicate `m/1`

The first step of moving around the grid world is defining the directions that we are able to move. They are `n`,`e`,`s` and `w`. For the first part of this exercise, you will need to define the predicate `m(A)` such that it is true when `A` is a valid direction.

### Create predicate `on_board/1`

Next, We need to create the predicate `on_board(+P)` that tells us if a position `P` is on the board. Positions are stored as a compound term `p(X,Y)` where both X and Y range from 1 to the grid size inclusive.

TIP: You can use the predicate `ailp_grid_size/1` to find the size of the grid.

### Create predicate `pos_step/3`

For this step we need to find the new position after an agent has made a possible step (although we don't need to check the validity yet!). The full predicate is `pos_step(+Pos,+Dir,-NPos)`.

### Create predicate `new_pos/3`

We are now able to combine the previous steps together to find the new position after a move has been made as well as to check that the move is valid. `new_pos(+Pos,+M,-NPos)` should be true if moving from `Pos` in direction `M` will lead to `NPos` and `NPos` is on the board.

### Create predicate `complete/1`

The predicate `complete(+L)` should be true if the Length of `L` is equal to the number of cells in the grid. The size of the grid **SHOULD NOT** be hardcoded.

### Create predicate `spiral/1`

The final part of this exercise is to implement the predicate `spiral(-L)` which will move the agent from the start position `p(1,1)` towards the center of the grid in a spiral pattern. L should be the list of steps that are taken by the agent to reach the center **including** the start position (You can test this using `complete/1`) 

TIP: In order for the agent to actually move, you will need to use `agent_do_moves(A,L)` where A is the identifier of your Agent and L is a path **that does not include** your current position.
## Exercise 2: Identity Loss

For the next exercise, you will need to use a wikipedia API to uncover the identity of an actor based only on links from their wikipedia page. For this exercise you will be editing `lab_identity_12345.pl`.

### Possible Queries

The following queries have been exported from the library code:

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


### Experiment with the predicates

Before you start to find the secret identity it is a good idea to familiarise yourself with the predicates. Can you find a query that stores all the links from a wikipedia page of your choice in a list?

### Create predicate `find_links_by_actor/2`

It's now time to create a predicate that finds all the links on a given actors wikipedia page. This predicate will take the form of `find_links_by_actor(+Actor,-Links)`


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