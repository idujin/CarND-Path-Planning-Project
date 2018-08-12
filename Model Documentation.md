# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program
   
## Model
### Collisions prevention
To avoid collisions, I computed the distance between the front car and mine. If the distance is less than the minimum distance already set (I set the value to 30), the ref_vel will decreased by 0.224. In addition, if the velocity of the front car is slower than the velocity of my car, ref_vel is additionally decreased considering the distance. Specific equation is in line 293 to 297.


### Cost function
To get the cost function, I used the speed, distance, and number of cars in front of each car in each lane. For the front car, higher speeds and distances get lower costs. However, for the behind cars, the higher speed get the lower cost, and distance logic is same as the front car case.

### Lane change conditions
Basically, if the car can not get the minimum distance from the front car, the lane will change to the other with less cost. However, I set some limitations. First, if the distance between the front car of another lane and my car is less than 10 miles, the car will not change the lane. Likewise, if the distance between the rear car of another lane and my car is less than 15 miles, the lane is not changed. Second, it will not update to the new lane during lane change. I have considered the vehicle is changing lane if the vehicle is not in the (center-1, center + 1) [meter] range. Finally, the lane will not change if the distance between the front car and my car in the lane to change is less than the distance between the front car in the current lane and my car.

