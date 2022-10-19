---
id: zx8yd0lbaxdq24ungv43d5e
title: Bringing a Gun to a Trainer Fight
desc: ''
updated: 1665531180847
created: 1665326284083
tags:
  - foobar
  - google
  - python
  - level-4
---

## Instructions

Uh-oh -- you've been cornered by one of Commander Lambdas elite bunny trainers! Fortunately, you grabbed a beam weapon from an abandoned storeroom while you were running through the station, so you have a chance to fight your way out. But the beam weapon is potentially dangerous to you as well as to the bunny trainers: its beams reflect off walls, meaning you'll have to be very careful where you shoot to avoid bouncing a shot toward yourself!

Luckily, the beams can only travel a certain maximum distance before becoming too weak to cause damage. You also know that if a beam hits a corner, it will bounce back in exactly the same direction. And of course, if the beam hits either you or the bunny trainer, it will stop immediately (albeit painfully).

Write a function solution(dimensions, your_position, trainer_position, distance) that gives an array of 2 integers of the width and height of the room, an array of 2 integers of your x and y coordinates in the room, an array of 2 integers of the trainer's x and y coordinates in the room, and returns an integer of the number of distinct directions that you can fire to hit the elite trainer, given the maximum distance that the beam can travel.

The room has integer dimensions [1 < x_dim <= 1250, 1 < y_dim <= 1250]. You and the elite trainer are both positioned on the integer lattice at different distinct positions (x, y) inside the room such that [0 < x < x_dim, 0 < y < y_dim]. Finally, the maximum distance that the beam can travel before becoming harmless will be given as an integer 1 < distance <= 10000.

For example, if you and the elite trainer were positioned in a room with dimensions [3, 2], your_position [1, 1], trainer_position [2, 1], and a maximum shot distance of 4, you could shoot in seven different directions to hit the elite trainer (given as vector bearings from your location): [1, 0], [1, 2], [1, -2], [3, 2], [3, -2], [-3, 2], and [-3, -2]. As specific examples, the shot at bearing [1, 0] is the straight line horizontal shot of distance 1, the shot at bearing [-3, -2] bounces off the left wall and then the bottom wall before hitting the elite trainer with a total shot distance of sqrt(13), and the shot at bearing [1, 2] bounces off just the top wall before hitting the elite trainer with a total shot distance of sqrt(5).

### Test cases

Your code should pass the following test cases.

Note that it may also be run against hidden test cases not shown here.

Input:
`solution.solution([3,2], [1,1], [2,1], 4)`
Output:
    `7`

Input:
`solution.solution([300,275], [150,150], [185,100], 500)`
Output:
    `9`

### Thought Process

- If the absolute distance between the shooter and the target is greater than the maximum distance, the shot will not hit the target (`solution = 0`).
  - If the absolute distance between the shooter and the target is equal to the maximum distance, the shot will hit the target and only one shot is possible (`solution = 1`).
- The shots in the example are vectors relative to the shooter's position, not absolute coordinates in the room.
  - Angles can be used to represent the shot direction, using the sides of a triangle with the shooter's position as the origin.
  - The angle of a shot can be calculated using `atan2(y, x)`.

## Python

```py
from itertools import product
from math import atan2

# Props to some of the visuals by Peter Agalakov and some syntax from
# Jason Lavoie (courtesy of Copilot)
def solution(dimensions, your_position, trainer_position, distance):
    """
    INPUT:
    - dimensions: list of two integers [x, y] representing the width and height
    of the room
    - your_position: list of two integers [x, y] representing your x and y
    coordinates in the room
    - trainer_position: list of two integers [x, y] representing the trainer's
    x and y coordinates in the room
    - distance: integer representing the maximum distance the beam can travel
    OUTPUT:
    - int: maximum number of distinct directions that you can fire to hit the
    trainer, given the maximum distance that the beam can travel
    """

    max_distance = distance
    shooter_x, shooter_y = your_position
    hits = dict()

    # Generates the matrix of points that will need to be reflected into the
    # other quadrants; the strange range logic is required because the constraints
    # specify Python 2.7, which doesn't play nicely with range() and floats
    for reflect in product(*[range(-(max_distance // -d) + 1) for d in dimensions]):
        # Finds all hits for the shooter and the trainer
        for position in your_position, trainer_position:
            # Generates the four reflection quadrants of the room
            for quadrant in [(1, 1), (-1, 1), (-1, -1), (1, -1)]:
                x, y = [
                  # Mirrors odd-numbered reflections across the y-axis
                  (d * r + (d - p if r % 2 else p)) * q
                  for d, p, r, q in zip(dimensions, position, reflect, quadrant)
                ]
                # Calculates the distance from the shooter to the hit
                distance = (abs(x - shooter_x) ** 2 + abs(y - shooter_y) ** 2) ** 0.5
                # Calculates the angle from the shooter to the hit
                angle = atan2(shooter_x - x, shooter_y - y)
                # Ignores hits that are out of range or have already been
                # recorded at a shorter distance
                if distance > max_distance or (angle in hits and distance > abs(hits[angle])):
                    continue

                # Mark shooter hits (bad) with a negative distance and trainer
                # hits (good) with a positive distance
                hits[angle] = distance * (-1 if position == your_position else 1)

    # Returns the number of distinct angles that hit the trainer
    return len([1 for travel in hits.values() if travel > 0])


# Test cases
print(solution([3, 2], [1, 1], [2, 1], 1)) # 1
print(solution([3, 2], [1, 1], [2, 1], 0)) # 0
print(solution([3, 2], [1, 1], [2, 1], 4)) # 7
print(solution([23, 10], [6, 4], [3, 2], 23)) # 8
print(solution([300, 275], [150, 150], [185, 100], 500)) # 9
print(solution([2, 5], [1, 2], [1, 4], 11)) # 27
```
