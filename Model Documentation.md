# Path Planning

## Minimizing Jerk and Acceleration

The car builds a trajectory based on a list of desired waypoints. In order to simplify the calculation of this trajectory, waypoints are converted to Frenet coordinates, then new waypoints are calculated along the path that would result in the desired velocity. In order to minimize jerk and acceleration, the trajectory is smoothed using splines.

## Collision Avoidance

The car uses sensor data to detect and predict the positions of other cars relative to its position. When a vehicle is detected ahead of the car, in the same lane and within an unsafe distance, the car decelerates to maintain a safe margin.

A vehicle is determined to be at an unsafe distance when it is less than 30 meters ahead of the car.

## Lane Changes

In order to be as efficient as possible, the car will change lanes when it is safe to do so, and attempt to maintain a speed as close as possible to the speed limit. The car uses sensor to data to determine the positions of other vehicles relative to its own position, and will change lanes when there a vehicle in the same lane obstructing its path and there is no vehicle detected in an adjacent lane within a distance that would cause the lane change to be an unsafe maneuver.

The thresholds used for safety margins for this car are 30 meters ahead and 20 meters behind in order to perform a lane change.

Lane changes are smoothed using splines to interpolate a trajectory between the cars current lane position and the desired lane position.

## Improvements

There are some ways in which this project can be improved:
- use a PID or MPC to follow the planner's output
- better lane monitoring for detecting other vehicles for safer and smoother transitions
