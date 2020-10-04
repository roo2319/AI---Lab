# Artificial Intelligence Prolog Labs

## Lab 1: Intro to the grid world

Hello! Welcome to Week 2 of Artificial Intelligence. Congratulations for making it through Week 1. This week, you will be introduced to the grid world, learn how to move around it and ultimately create a spiral.

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

This is one of the most important parts of the lab. In order to run the grid world, you need open `ailp.pl` using swipl. This week we are doing `lab grid` so we will pass that as a command line argument (e.g. `swipl ailp.pl lab grid`).
 
Upon loading you will likely see a lot of warnings
about singleton variables, this is normal and because the functions in `lab_grid_12345` have not been implemented. 

Next, Type in `start.` and hit enter to start the webserver. If you press `Y`, then the webpage will open in your default browser. **Hit the run button on the webpage before you continue.**

We will use a shell to initialise the grid so type in `shell.` and then `setup.` in the following command prompt. (While the main prolog prompt is `?-`, in the shell it will look like `?`).

After the `setup/0` has finished, you can exit the shell using either `stop.`,`CTRL+D` or `CTRL+C` then (a)bort at the prompt.

### Identifying your Agent

At the top left of the grid, you will be able to see a coloured shape. This is your agent. For the first task in this lab, find a query that allows you to identify your agent and their current position.

### Create predicate `m/1`

The first step of moving around the grid world is defining the directions that we are able to move. They are `n`,`e`,`s` and `w`. For the first exercise in this lab, you will need to define the predicate `m(A)` such that it is true when `A` is a valid move.

### Create predicate `on_board/1`

Next, We need to create a predicate that tells us if a position is on the board. Positions are stored as a compound term `p(X,Y)` where both X and Y range from 1 to the grid size inclusive.

TIP: You can use the predicate `ailp_grid_size/1` to find the size of the grid.

### Create predicate `pos_step/3`

For this step we need to find the new position after an agent has made a possible step (although we don't need to check the validity yet!).  

### Create predicate `new_pos/3`

We are now able to combine the previous steps together to find the new position after a move has been made as well as to check that the move is valid. `new_pos(Pos,M,NPos)` should be true if moving from `Pos` in direction `M` will lead to `NPos` and `NPos` is on the board.

### Create predicate `complete/1`

The predicate `complete(L)` should be true if the Length of L is equal to the number of cells in the grid. The size of the grid **SHOULD NOT** be hardcoded.

### Create predicate `spiral/1`

The final section of this lab is to implement the predicate `spiral(L)` which will move the agent from the start position `p(1,1)` towards the center of the grid in a spiral pattern. L should be the list of steps that are taken by the agent to reach the center **including** the start position (You can test this using `complete/1`) 

TIP: In order for the agent to actually move, you will need to use `agent_do_moves(A,L)` where A is the identifier of your Agent and L is a path **that does not include** your current position.
## Lab 2: Identity Loss

For this weeks lab, we will be using a wikipedia API to uncover the identity of an actor based only on links from their wikipedia page. We will also be implementing a simple breadth first search. 

### Possible Queries

### How to run?

Run using `swipl ./ailp.pl lab identity` 

The file `lab_identity_12345.pl` will automatically be consulted and should be the place that your work is done. There is no need to follow the steps to start the webserver this week (although once you have created `find_identity/1` you can use `test/0` to check that your solution works).

### Create predicate `find_links_by_actor/2`



### Create predicate `find_identity/1`
