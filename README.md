# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    
* Simulator, it can be downloaded from the [here](https://github.com/udacity/self-driving-car-sim/releases)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 


## Rubric

### Compilation
#### Your code should compile
The code is compiled successfully without error.

### Implementation

#### The PID procedure follows what was taught in the lessons
PID values are calculated in UpdateError method line 25 to line 29 of PID.cpp. The steering angle calculation is based on total Error value that is calculated at line 34 of PID.cpp.

### Reflection

#### Describe the effect each of the P, I, D components had in your implementation.

The value of Proportional component will cause car to make extreme adjustment. At the straight road, this cause car run zig-zag. But low value of P will cause the car can't adjust steering angle at non-straight road in timely manner.

[![P component](http://img.youtube.com/vi/qvq4YVBtXok/0.jpg)](http://www.youtube.com/watch?v=qvq4YVBtXok)

The value of Derivative component will cause more granular adjustment. Fitted value of this component will cause car runs smoothly, because of less extreme steering angle adjustment. 

[![D component](http://img.youtube.com/vi/W4mTvUIvT-s/0.jpg)](http://www.youtube.com/watch?v=W4mTvUIvT-s)


The value of I should make general adjustment based on overall error. At the implementation i have to set this value to very small this, because any big value more than 0.01 will cause the car to run zig-zag. Significant value of I component doesn't contribute to smoothing run. 
 

#### Describe how the final hyperparameters were chosen

Hyperparameters are choosen by manual tuning, by running simulation many times. I started with P component, from 0.1 to 1. Then followed by D component. For I component, initially i started, with value 0.1, but the simulation didn't run well. Then i decrease the I component value until almost reaching zero. 

I did try Sebastian's twiddle algorithm, but i didn't manage to come up with working solution, and i have run out of time. 

### Simulation

#### The vehicle must successfully drive a lap around the track
The car simulation runs without leaving drivable surface.

[![Simulator Video](http://img.youtube.com/vi/lNjpbqzQtp8/0.jpg)](http://www.youtube.com/watch?v=lNjpbqzQtp8)


