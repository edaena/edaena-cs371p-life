![http://dl.dropbox.com/u/1158059/GameOfLife.jpg](http://dl.dropbox.com/u/1158059/GameOfLife.jpg)

# Introduction #

---


This project is a variation of the classic "Conway's Game of Life" programming assignment.  There are two lowest-level classes of cell, each with subtly different characteristics.  A grid contains numerous instances of these cells, with the grid's cell collection being potentially homogeneous or heterogeneous.  The focus of the assignment was to efficiently abstract enough information about these two individual cell species such that a grid class could be a template for either heterogeneous or homogeneous collections.

As can be inferred from our intricate UML diagram, design considerations were more difficult and impactful in this project than in projects prior.  Starting on the third day began very slowly and deliberately, doing rough pseudo-UML sketches.



### Class Diagram ###
![http://dl.dropbox.com/u/1158059/Life.jpg](http://dl.dropbox.com/u/1158059/Life.jpg)



## Abstract Cell ##

---

Abstract Cell is the abstract class that includes all the variables and behavior that can be inherited by child classes.  The inherited characteristics are state (alive or dead), symbol, and neighbor count, and the inherited methods are several getters, methods to invert


## Conway Cell ##

---

Conway Cell is a cell that can have up to eight neighbors.  This meant that every time we mentioned the notion of a neighbor within Conway, we had specify things that differed from those in Fredkin.  All things considered, Conway is a simpler construct than Fredkin.

## Fredkin Cell ##

---

Fredkin Cell is essentially a Conway cell with a different notion of neighbors and an age counter.  When a Fredkin Cell reaches a certain age, its age ceases to be represented numerically and is instead represented symbolically, as a plus.  These facets require Fredkin to track age.

## Cell ##

---

The Cell class, allows for heterogeneity amongst our objects in the grid.  It uses a Handle class to act through that Handle's get() method.  Initially we had the get() in the Cell class, but decided it would be better to protect it by putting it in the Handle.

## Handle ##

---

The handle class manages our cells by providing a thin layer of abstraction that allowed us to use new and delete only once.  Without a handle, the heterogeneous grid would have been more difficult to implement, as proven by the struggles to create vectors of heterogeneous shapes during class.

## Life ##

---

The grid represents the world that the cells interact in. and Life is the main driver that manages it.  Rows and columns are read in initially and create the two dimensional array.  This two dimensional array is a vector of vector of ints called grid.  The vector alive\_positions lists places where cells exist.  This is iterated through every time we need to iterate through the live locations of cells

Our grid was bordered by a pad of dead cells that allowed us to work with the cells on the edges more comfortably, provided we made sure to print the correct cells later on.  This led to some indexing issues that we had to debug

The alive\_positions vector necessitated a way to contain positions in a single object, which is our position struct.  We did not include it in the UML due to its simplicity.  A position is just an X, Y coordinate pair.

## Testing ##

---

Life was not a difficult program to test.  The only bothersome part was the issue of copy pasting large strings, which was a recurring annoyance throughout the projects this semester.  We ended up with about 49 tests, many of these being helper tests.