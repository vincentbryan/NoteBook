### 1. A Brief Introduction to A*

* The A* algorithm is guaranteed to find the best path from the origin to the destination, if exists
* Critical to any discussion of efficient pathplanning if the notion of hierarchical maps

In the real world, people do not formulate precise path plans which stretch on for miles. Rather, if a person has some domain knowledge of the intermediate terrain, they will subdivide the path.

* Subdivide the line to the destination into midpoints, each of which is then used as a subdestination. Unfortunately, this always leaves the possibility that a chosen midpoint will be at an impossible location, which can eliminate the ability to find a valid path.

### 2. A Faster Implementation of the Standard A*

//TODO



### 3. Smoothing the A* Path

#### 3.1 A Simple Solution

>  Add a  cost penalty each time a turn is taken.

Unfortunately, this simplistic solution is not very effective, because 

1. all turns are still at 45-degree angles, which causes the movement to continue to look rather unrealistic.
2. In addition, the 45-degree-angle turns often cause paths to be much longer thanthey have to be. 
3. Finally, this solution may add significantly to the time required to perform the A* algorithm.

#### 3.2 Smoothing Algorithm 

> This simple smoothing algorithm is similar to "line of sight" smoothing, in which all waypoints are progressively skipped until the last one that can be "seen" from the current position.



### 4. Adding Realistic Turns

The next step is to add realistic curved turns for our units, so that they don't appear to change direction abruptly every time they need to turn.

#### 4.1 A Simple Solution

> using spline to smooth the abrupt corners into turns

While this solves some of the aesthetic concerns, it still results in physically very unrealistic movement for most units. For example, it might change an abrupt cornering of a tank into a tight curve, but the curved turn would still be much tighter than the tank could actually perform.(not taking the radius into account)

#### 4.2 A Better Solution

For a better solution, the first thing we need to know is the turning radius for our unit. Turning radius is a fairly simple concept: if you're in a big parking lot in your car, and turn the wheel to the left as far as it will go and proceed to drive in a circle, the radius of that circle is your turning radius.

