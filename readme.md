# Artificial Intelligence Prolog Labs

## Lab 1: Intro to the grid world

Hello! Welcome to Week 2 of Artificial Intelligence. Congratulations for making it through Week 1. This week, you will be introduced to the grid world, learn how to move around it and ultimately create a spiral.

### How to run?

This is one of the most important parts of the lab. In order to run the grid world, you need open `ailp.pl` using swipl. This week we are doing `lab grid` so we will pass that as a command line argument (e.g. `swipl ailp.pl lab grid`).
 
Upon loading you will likely see a lot of warnings
about singleton variables, this is normal and because the functions in `lab_grid_12345` have not been implemented. 

Next, Type in `start.` and hit enter to start the webserver. If you press `Y`, then the webpage will open in your default browser. **Hit the run button on the webpage before you continue.**

We will use a shell to initialise the grid so type in `shell.` and then `setup.` in the following command prompt. (While the main prolog prompt is `?-`, in the shell it will look like `?`).

After the `setup/0` has finished, you can exit the shell using either `stop.`,`CTRL+D` or `CTRL+C` then (a)bort at the prompt.


### Create predicate `m/1`

The first step of moving around the grid world is defining the directions that we are able to move. They are `n`,`e`,`s` and `w`. For the first exercise in this lab, you will need to define the predicate `m(A)` such that it is true when `A` is a valid move.

### Create predicate `on_board/1`

Next, We need to create a predicate that tells us if a position is on the board. Positions are stored as a compound term `p(X,Y)` where both X and Y range from 1 to the grid size inclusive.

### Create predicate `pos_step/3`
### Create predicate `new_pos/3`
### Create predicate `spiral/1`

## Lab 2: Identity Loss

### Create predicate `find_links_by_actor/2`
### Create predicate `find_identity/1`