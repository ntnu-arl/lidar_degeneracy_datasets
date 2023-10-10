# LiDAR Degeneracy Datasets (UNDER DEVELOPMENT)

Dataset associated with submission for handling LiDAR-degenerative environments through LiDAR-radar-inertial fusion with factor graphs.

The datasets consist of sensor measurements (IMU, LiDAR, and FMCW radar) of an aerial robot manually flown through environments challenging for LiDAR sensors. These are a biking tunnel (geometric self-similarity) and a university corridor filled with fog (obscurants). In addition CAD extrinsics between the sensors are provided.

## Environments

### [Fyllingsdalen Tunnel](https://maps.app.goo.gl/Crj1o13NznuE5fZn8)

Manual flight along a 8m-wide, 500m-long, straight section of a biking tunnel in Bergen, Norway.

![INSERT IMAGE HERE](images/drone_in_tunnel.png)

Bag files can be found [INSERT DATASET LINK HERE]()

### [Fog-Filled University Corridor](https://maps.app.goo.gl/V5ZfTVAy4xxQHPzs5)

Manual flight in a university environment in the Elektro building of NTNU in Trondheim, Norway. The first corridor flown through after takeoff is filled with dense fog.

![INSERT IMAGE HERE](images/image-1580.png)

Bag files can be found [INSERT DATASET LINK HERE]()

## Robot Equipiment

### Drone

![INSERT IMAGE HERE](image.png)

#### Sensors

Synchronized using microcontroller-based internally developed synchronization/triggering module

- [Ouster OS0-128 LiDAR](https://ouster.com/products/scanning-lidar/os0-sensor/)
- [VectorNav VN100 IMU](https://www.vectornav.com/products/detail/vn-100)
- [Texas Instruments IWR6843AOP-EVM Radar](https://www.ti.com/tool/IWR6843AOPEVM)

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
