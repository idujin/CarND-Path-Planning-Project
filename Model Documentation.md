# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program
   
### Model
## Collisions prevention
To avoid collisions, I computed the distance between the front car and mine. If the distance is smaller than the minimum distance I already set (I set the value to 30), ref_vel is decremented by 0.224 m. In addition, if the velocity of the front car is slower than mine, ref_vel is additionally decreased considering the distance. Specific equation is as below.


## Cost function
To get the cost function, I used speed, distance and the number of car in front of mine at each of lane. For the front cars, the higher speed and the distance, get the lower cost. However, for the behind cars, the higher speed get the lower cost, and distance logic is same as the front car case.

## Lane change conditions
Basically, if the vehicle cannot assure minimum distance between the front car, the lane is changed to other side with lower cost. However, I set some limitations. First, if the distance between front car and mine is less than 10 miles, the vehicle does not change lane. Similarly, if the distance between backward car and mine is less than 15 miles, the lane does not changed. Second, vehicle does not change lane during changing lane. I condidered if the vehicle is not located on the range of (center - 1, center + 1)[meters], it is during changing lane. Finally, even if one side of lane has the lower cost than the others, the lane is not changed when the distance to front car on that side is less than the distance between to front car on current lane.

