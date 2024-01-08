# Organize a room with OOP in Python

- Repository: `openspace-organizer`
- Type: `Consolidation`
- Duration: `2 days`
- Deadline: `xx/xx/20xx 5:00 PM`
- Team: `solo or team`

## Mission Objectives

Create an algorithm that randomly assigns people to a spot in the open space.

## Learning Objectives

- Make good use of classes using the Object-oriented programming (OOP) paradigm
- Use imports in a clean way
- Use a clean architecture
- Read data from an Excel file
- Structure a project
- [If in teams] Use Git as a team with Trello and integrate versioning and management
  - Split functionalities into tasks
  - Assign tasks to people
  - Develop functionalities on separate branches
  - Use pull requests to merge branches

## The Mission

Your company moved to a new office. It's an open space with 6 tables of 4 seats.

As many of you are new colleagues, you come up with the idea to change seats every day to get to know each other better by working side by side with your new colleagues.

You will create a script that runs each day to re-assign everybody to a new seat. 

### Must-have features

You want to build a program that allows you to (i) get a list of colleagues from an Excel file and (ii) place them ***randomly*** on the different tables of the open space.

#### The default setup of the open space is 6 tables of 4 seats → 24 seats ####

- The program can take a filepath as an argument to load the list of colleagues 
- The program distributes at random the people on the existing tables and says how many seats are left
- The program can gracefully deal with the possibility of having too many people in the room

### Nice-to-have features

Once you have a basic program, you want to make it more interactive and more configurable. Below are a couple of suggestions.

- Allow the possibility to ask the program to display the current repartition:
  - The number of people in the room 
  - The number of available seats in the room
  - The number of seats that are left
- Allow the possibility to define the room setup from a `config.json` file
- Allow the possibility to change dynamically the setup and re-run the program
- Allow the possibilty to add someone in the room (for instance, a new colleague arriving or someone being late)
- Allow the possibilty to add a table if the room is full
- Improve the algorithm to avoid having someone alone at a table
- Allow the possibility to integrate an Excel "black" list → _X wants to be seated next to Y_, or _X doesn't want to be seated next to Y_
- Create an HTML page to interact with your program in a browser: 
  - Allows to choose any Excel file from your computer
  - Allows you to interact with the different features of the program and to execute it

### Quality Assurance

Read our "Coding Best Practices Manifesto" and apply what's in there!

Please keep the must-have version separate from the nice-to-have version by using a different branch on GitHub. Please specify that in your README too.

### Steps

Now, let's get to the heart of it. **Read through all of the below before starting!**

#### 0. preparation

Create a GitHub repo called `challenge-openspace-classifier` and share it with your team if needed. 

Create two files:
- `README.md`
- `main.py`

Create a `utils` folder with three files:
- `file_utils.py`
- `table.py`
- `openspace.py`

You're ready to go!

If you're doing it as a team → split the work between the members in a Trello board (using a Kanban-like setup) and let each member create a feature branch to develop his own work.

#### 1. A table

You need to define a useful class structure to generate a table and the amount of seats it has. This is set up in the `table.py` file.

##### 1.1 Seat

In `table.py`, create a class called `Seat` with two attributes:
- `free` which is a boolean
- `occupant` which is a string

Add two methods to the same class: 
- `set_occupant(name)` which allows the program to assign someone a seat if it's free
- `remove_occupant()` which removes someone from a seat and returns the name of the person occupying the seat before

##### 1.2 Table

Create another class `Table` with at least the below attributes:
- `capacity` which is an integer
- `seats` which is a list of `Seat` objects (size = `capacity`)

Go on and add some methods to the class:
- `has_free_spot()` that returns a boolean (`True` if a spot is available)
- `assign_seat(name)` that places someone at the table
- `left_capacity()` that returns an integer

#### 2. An open space

In `openspace.py`, create a class `OpenSpace` that contains these attributes:
- `tables` which is a list of `Table` _(you will need to import `Table` from `table.py`!)_
- `number_of_tables` which is an integer

Add some methods:
- `organize(names)` that will **randomly** assign people to `Seat` objects in the different `Table` objects
- `display()` to display the different tables and there occupants in a nice and readable way
- `store(filename)` to store the repartition in an Excel file

#### 3. Main script

In `main.py`:
- Import everything you need to launch the organizer
- Load the colleagues from the Excel file defined in the config file
- Launch the organizer and display the results

## Deliverables

1. Publish your source code on the GitHub repository
2. Pimp up the README file:
   - Description
   - Installation
   - Usage
   - (Visuals)
   - (Contributors)
   - (Timeline)

## Evaluation criteria

| Criteria       | Indicator                                                      | Yes/No |
| -------------- | -------------------------------------------------------------- | ------ |
| 1. Is complete | The student has implemented all must-have features             |        |
|                | There is a published GitHub repo available                     |        |
|                | The program runs until the end without any error               |        |
|                | The program starts by running `python main.py` in the terminal |        |
| 2. Is correct  | The code is well typed                                         |        |
|                | There is a docstring for every function/method/class           |        |
|                | All other quality assurance guidelines are respected           |        |
| 3. Is great    | There is an interaction with the user                          |        |
|                | The algorithm doesn't create table with people sitting alone   |        |
|                | The result is nicely displayed and can be saved in a file      |        |
|                | The team used a proper Git workflow and task management system |        |

## Final note

![You've got this!](https://media.giphy.com/media/BcCoMy2A0eYELrRZ6O/giphy.gif)
