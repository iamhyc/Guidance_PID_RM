# DJI Script SDK

**THIS IS NOT DJI OFFICIAL SDK.** (under developing)

support script interface for M100 real-time/automation control with diverse functions provided. Dependent on DJI Guidance suite.

## Demo

Takeoff Procedure

```
TAKEOFF
D 0 0 2
WAIT
```

PID Adjust Procedure

```
XP 0.8 0.35 0.3
XV 0.8 0.35 0.3
YP 0.8 0.35 0.3
YV 0.8 0.35 0.3
PZ 0.8 0.35 0.3

VEL 1.0 1.0 1.0
ERR 0.1 0.1 0.1
```

Flight Procedure

```
D 1 1 2
WAIT_TIME 2
INC 0 0 1
WAIT
D 99 99 -1
WAIT
```

Vision Coordination Nav

```
T T T T T
WAIT_TIME 0.5
D 99 99 -1

T T T T T
WAIT_TIME 0.5
D 99 99 -1
```

Fail Safe Procedure (e.g.: Lose Target scene)

```
FAIL_SAFE HEIGHT_FIX #execute height fix script
	T T T T T
	WAIT_TIME 0.5
	D 99 99 -1

FAIL_SAFE DATE_BACK #back to last state (State Machine)
	T T T T T
	WAIT_TIME 0.5
	D 99 99 -1
```

Landing Procedure

```
D 99 99 0.5
WAIT
L
```

## Test

```
#for DJI official SDK
roslaunch dji_sdk sdk_manifold.launch
rosrun guidance guidanceNode
#for script engine controller
rosrun dji_sdk_demo dji_sdk_client
rosrun sdk_controller dji_sdk_controller
```

