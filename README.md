# Autonomous transportation robots in crowded hospital environments

## Summary

| Company | [Tartu University Hospital](https://www.kliinikum.ee/) |
| :--- | :--- |
| Project Manager | [Karl KRUUSAMÄE](https://www.etis.ee/cv/Karl_Kruusamae) |
| Project Core Team | [Robert Valner](https://www.etis.ee/cv/Robert_Valner); Karl Riis; Meelis Kull; Houman Masnavi; Igor Rybalskii; Rauno Põlluäär; Erik Kõiv; Renno Raudmäe; Alvo Aabloo; [Arun Kumar Singh](https://www.etis.ee/CV/Arun%20Kumar_Singh/) |
| Challenge Tackled | Deploying mobile robots that handle dynamic obstacles (e.g. humans in hosptial corridors) and coordinate tasks with other robots as well as IoT devices. |
| Technology Used | ROS, ROS2, Robotics Middleware Framework (RMF), FreeFleet, Pal Robotics TIAGo, Clearpath Jackal, Forecasting Human Trajectories with Uncertainty Estimation |
| Lessons Learned | Deploying mobile robots in hospital is feasible but continues to require simultaneous engineering effort. Potentially outdated infrastructure (e.g., lack of centrally-controlled doors and elevators) add barriers to deploying AI-based technoloogy. It is possible to create a relatively well-performing trajectory forecasting method whilst keeping the inner workings of its algorithm easy to follow. |
| Result Published | We integrated a software stack and deployed a mobile robot to transport time-critical samples for the intensive care unit to the hospital lab. Our work builds upon Robotics Middleware Framework (RMF), an open source, actively growing and highly capable fleet management platform which is yet to reach full maturity. Additionally, we benchmarked and assessed the feasibility of forecasting human walking trajectories so that this information would serve as an input for motion planning algorithms for the mobile robot. |
| Target Group | Hospitals, warehouses, manufacturing floors, supermarkets and department stores, transportation hubs (airports, tainstations, etc), schools, etc |
| Diagrams/Photos | http://doi.org/10.3389/frobt.2022.922835 |
| Video | Supplemental data at http://doi.org/10.3389/frobt.2022.922835 |

## Implementation Details

Figure below shows the architecture of our deployed system. The setup consists of
* robots
* automated doors
* user interface devices, such as tablets
* dispensers and ingestors, which are used to place and retrieve objects from the robot respectively
* and RMF, orchestrating the whole setup. 

All devices are connected via Virtual Private Network (VPN). FreeFleet is used as the fleet manager. Structurally FreeFleet is segregated to a central server and clients, a client per each robot. The server is responsible for mediating navigation requests from RMF and providing feedback to RMF via aggregating the state of the whole fleet. The FreeFleet client passes navigation requests from the server to the driver of the local robot (ROS Navigation) and provides feedback of the robot’s state. Both RMF and the FreeFleet server are running on a dedicated PC. FreeFleet server and clients communicate purely via Cyclone DDS, thus the server can simultaneously manage both ROS1 and ROS2 based robots. Each door, dispenser and ingestor is equipped with a custom controller ([door controller](https://github.com/project-covsg24/card_swipe_py); [tablet-based dispenser](https://github.com/project-covsg24/rmf_dispenser_ingestor_tools)) that accepts commands from and sends feedback to RMF. Finally, RMF Web is utilized as a graphical user interface, mostly deployed on tablets via a web browser.

<p align="center">
  <img src="https://github.com/scafld/covsg24_fleet_backend/blob/main/docs/system_setup.png" class="center" width=600"/>
</p>

For further details, refer to [our article published at the Frontiers in Robotics and AI](http://doi.org/10.3389/frobt.2022.922835) and [the replication package](https://doi.org/10.5281/zenodo.6467038). The latest source code and instructions of our ongoing development can be found in the [GitHub for SCAFLD](https://github.com/scafld). 

### Description

- The results, lessons learned and the source code of deploying a heterogeneous mobile robot fleet for transporting time-critical samples from an intensive care unit to the laboratory at the Tartu University Hospital.
- The developed system showcases the level of maturity for several technological capabilities and tools. Among them, the Robotics Middleware Framework (RMF), an open-source fleet management system for interoperability of heterogeneous robotic systems.
- Futhermore, a trajectory forecasting method is proposed which operates by generating a large number of potential future trajectories for one historical trajectory, and then choosing a limited number of representative predictions from them by dividing them into separate probability groups and running K-Means clustering on each group separately

### How to Install, Run & Use

For detailed instructions:
- To replicate the deployment demo: https://doi.org/10.5281/zenodo.6467038
- To replicate the trajectory forecasting: https://github.com/karlriis/trajectory-forecasting 
- To be up-to-date on our ongoing development: https://github.com/scafld

### Licensing

Please refer to the above linked repositories for specific software licenses of integrated components. Since [Open Robotics](https://github.com/osrf) maintains RMF and ROS2 under Apache 2.0, the majority of the work is licensed under Apache 2.0 software license.

### How to Contribute

If you are interested in contributing, feel free to contact people in the project team or just reach out to us via our GitHub at https://github.com/scafld.

Also, if the content in this repository is helping your research, please cite us as follows:
```
@article{valner_frobt2022,
  title = {Scalable and heterogenous mobile robot fleet-based task automation in crowded hospital environments - a field test},
  author = {Robert Valner and Houman Masnavi and Igor Rybalskii and Rauno Põlluäär and Erik Kõiv and Alvo Aabloo and Karl Kruusamäe and Arun Kumar Singh},
  journal = {Frontiers in Robotics and AI},
  year = {2022},
  volume = {9},
  pages = {922835},
  doi = {10.3389/frobt.2022.922835}
}
