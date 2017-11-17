# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program
   
The solution is heavily inspired by the lesson video. I've just added 

### Setup (main.cpp: 233-258)
Just setup some variables we are going to need later on.

### Prediction (main.cpp: 265-305)
In the prediction phase, i'm iterating over all the data supplied by the sensor fusion. For each car I get, the sensor fusion data is extracted. Using these informations, we calculate in which lane the particular car is driving. 
At the end, we check if there are any cars nearby.

### Action (main.cpp: 307-336)

In the action phase, we use the data from the prediction to decide if we need to do a lane change. 
If there is no car ahead of us, we just stay in the lane and accelerate until we reach max_speed. If there is a car ahead of us and no lane is free, we slow down. Here I tried to implement some kind of cruise control, to just stay behind the car infront of me, but I couldn't find a smooth solution.
Whenever there is a chance to switch lanes and surpass the slow driving vehicle in front of us, we will do it. 
Here in germany it would be better to implement a cost function which penalises a surpass on the right lane, as german drivers don't like this behavior at all. But for this projet, this behavior is sufficient.

### Trajectory (main.cpp: 338-340)

The trajectory part is strictly following the lessons' video. I calculate some anchor points and use "spline.h" to create a smooth tractory. Only addition to the video is the adaption of speed (410-418).
Here it could be a good idea to create different trajectories and select one of them based on cost functions (p.e. filter by jurk, ...). 
