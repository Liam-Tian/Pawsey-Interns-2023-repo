# Automated Data Acquisition and Analytics for Livestock Management using UAVs
This is a repo containing more information of our work. Our source code and paper will be released after published.

## Table of Contents

- [Abstract](#abstract)
- [Energy Consumption Model](#energy-consumption-model)
- [Optimal Altitude Evaluation](#optimal-altitude-evaluation)
- [Deep Reinforcement Learning](#deep-reinforcement-learning)
- [Visualization](#visualization)
- [Reference](#reference)

## Abstract

In the context of Australia, due to its unique geographical distribution, it is difficult for farmers to closely monitor animal health and welfare. There is a need for innovative and autonomous solutions to keep up with demand in the agricultural industry. This project proposes using Unmanned Aerial Vehicles (UAVs) as an effective solution to offer an integrated wearable sensor data acquisition and analytics platform for livestock monitoring. Using computer vision algorithms, it will deploy UAVs to fly on the farm periodically and detect livestock with collars. The UAVs then fly in close proximity to the animals and establish communication with their wearable sensors. UAVs will also pull out the raw data at high speed and transmit it to the Cloud for further analysis. Data analytics methods will run in real-time at the cloud data centre to infer valuable phenomena and alert the farmers if urgent action is necessary.

## Energy Consumption Model

Due to limited space, we do not introduce the energy model in the poster. We reference the model proposed by [[1]](#refer-anchor-1). The basic idea is to divide the whole procedure into multiple phase: 1) waking-up phase, 2) sensing phase, 3) transmission phase and 4) processing phase. The energy consumption will be determined separately for each phase. 

## Optimal Altitude Evaluation

The action space of UAVs in our work is based on 2d space including horizontal and vertical movement. Therefore the altitude of UAVs should be determined for the maximum coverage radius. Following the assumption in [[2]](#refer-anchor-2), we formulate the evaluation into a optimization problem and solve the value by implicit differentiation.

## Deep Reinforcement Learning

We give the essentials of reinforcement learning here.

* State: The 2d location of each node and the current data load.
* Reward: A data-driven reward function is designd. A reward is given depending on the data amount collectd in current timestep.
* Action Space: A discrete set with 7 elements: left, right, forward, backward and idle.

## Visualization
<img src="v1.gif" alt="Cover" width="50%"/><img src="v2.gif" alt="Cover" width="50%"/>
In the figures above, the cross symbol is the UAVs, among which the black one (Type II) is responsible for pre-processing raw data from the bottom layer, while others (Type I) are deployed by DQNs to find the shortest path to approach the sensor nodes. These nodes will be marked by different colors, meaning assigning to different clusters and will be visited by their own UAVs.

The figure left is the traditional method without considering the mobility of the nodes in real time, and these clusters will soon be mixed with each other, bringing the difficulty for UAVs to collect data. These UAVs have to go through the whole pasture to collect data, slowing down the efficiency. Instead, our method tries to update the cluster for every timestep. Since every UAV is only responsible for their own cluster, thus they just need to move around the sub-area of the pasture, thus improving the efficiency.

Traditional Method:
* Avg. CDPS: 18.33 bytes / step
* Avg. ECPS: 14.79 J / step

Our Method:
* Avg. CDPS: 19.29 bytes/ step
* Avg. ECPS: 13.57 J /step

## Reference
<div id="refer-anchor-1"></div>

- [1] [Bouguera T, Diouris J F, Chaillout J J, et al. Energy consumption model for sensor nodes based on LoRa and LoRaWAN[J]. Sensors, 2018, 18(7): 2104.]

<div id="refer-anchor-2"></div>

- [2] [Al-Hourani A, Kandeepan S, Lardner S. Optimal LAP altitude for maximum coverage[J]. IEEE Wireless Communications Letters, 2014, 3(6): 569-572.]
