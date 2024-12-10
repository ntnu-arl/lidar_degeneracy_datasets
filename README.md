# LiDAR Degeneracy Datasets

Dataset associated with submission for handling LiDAR-degenerative environments through LiDAR-radar-inertial fusion with factor graphs.

The datasets consist of sensor measurements (IMU, LiDAR, and FMCW radar) of an aerial robot manually flown through environments challenging for LiDAR sensors. These are a biking tunnel (geometric self-similarity) and a university corridor filled with fog (obscurants). In addition CAD extrinsics between the sensors are provided.

## Environments

### [Fyllingsdalen Tunnel](https://maps.app.goo.gl/Crj1o13NznuE5fZn8)

Manual flight along a 8m-wide, 500m-long, straight section of a biking tunnel in Bergen, Norway.

![fyllingsdalen bycicale tunnel image](images/drone_in_tunnel.png)

Bag files can be found [here](https://ntnu.box.com/s/congyw29kpo80exau7e1tpeyoqay6u9d)

### [Fog-Filled University Corridor](https://maps.app.goo.gl/V5ZfTVAy4xxQHPzs5)

Manual flight in a university environment in the Elektro building of NTNU in Trondheim, Norway. The first corridor flown through after takeoff is filled with dense fog.

![fog-filled university corridor image](images/image-1580.png)

Bag files can be found [here](https://ntnu.box.com/s/30syn4fpmq5tfgosy99tji4aqirooj1r)

## Robot Equipiment

### Drone

#### Sensors

Synchronized using microcontroller-based internally developed synchronization/triggering module

- [Ouster OS0-128 LiDAR](https://ouster.com/products/scanning-lidar/os0-sensor/)
- [VectorNav VN100 IMU](https://www.vectornav.com/products/detail/vn-100)
- [Texas Instruments IWR6843AOP-EVM Radar](https://www.ti.com/tool/IWR6843AOPEVM)

The header time stamp for IMU and radar originate from the triggering module, to replay the trigger-stamped LiDAR data from packet topics use [this](https://github.com/ntnu-arl/ouster-ros/tree/dev/sensor_sync_replay) driver.

##### Topics

| **Source** 	| **Topic**                                                                                                                                                         	| **Rate [Hz]** 	|
|:----------:	|-------------------------------------------------------------------------------------------------------------------------------------------------------------------	|---------------	|
| Triggering 	| - `/sensor_sync_node/trigger_0`<br>- `/sensor_sync_node/trigger_1`                                                                                                	| - 800<br>- 10 	|
| IMU        	| - `/vectornav_node/imu`<br>- `/vectornav_node/magetic_field`<br>- `/vectornav_node/pressure`<br>- `/vectornav_node/temperature`<br>- `/vectornav_node/uncomp_imu` 	| 200           	|
| LiDAR      	| - `/os_cloud_node/imu_packets`<br>- `/os_cloud_node/lidar_packets`<br>- `/os_cloud_node/metadata`                                                                 	| 10            	|
| Radar      	| `/radar/cloud`                                                                                                                                                    	| 10            	|

##### Extrinsics

All extrinsics are given with respect to the IMU

**LiDAR**

- translation [x, y, z]
  - `[-0.00171, 0.02149, 0.0358]`
- orientation [x, y, z, w]
  - `[0.000462, 0.0008483, 0.0028835, 0.9999954]`

**Radar**

- translation [x, y, z]
  - `[0.07771, 0.02141, -0.03631]`
- orientation [x, y, z, w]
  - `[0.953717, 0, -0.3007058, 0]`

## Acknowledgements

We thank the Vestland Fylkeskommune for providing access to the Fyllingsdal sykkeltunnel.

## Reference

If you use this work in your research, please cite the following publication:

**Degradation Resilient LiDAR-Radar-Inertial Odometry** ([link](https://arxiv.org/abs/2403.05332))

```bibtex
@inproceedings{nissov2024degradation,
  author={Nissov, Morten and Khedekar, Nikhil and Alexis, Kostas},
  booktitle={2024 IEEE International Conference on Robotics and Automation (ICRA)}, 
  title={Degradation Resilient LiDAR-Radar-Inertial Odometry}, 
  year={2024},
  pages={8587-8594},
  doi={10.1109/ICRA57147.2024.10611444}
}
```