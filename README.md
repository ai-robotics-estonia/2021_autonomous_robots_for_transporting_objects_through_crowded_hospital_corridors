*This is a template repository for this organization. Start by replacing the placeholder for the project name with it's actual title.*

# [Project Name]

## Summary
*This section is to be filled out by the project manager based on the [summary document](https://docs.google.com/spreadsheets/d/12xi2yOMm-X5PEecgyRe3WEurcSaN9A5z4DHgBacQT6M).*

| Company | [Company](https://website.link) |
| :--- | :--- |
| Project Manager | [Project Manager](https://profile.link) |
| Project Team | [Team Member 1](https://profile.link); [Team Member 2](https://profile.link); ... |
| Challenge Tackled |  |
| Technology Used |  |
| Lessons Learned |  |
| Result Published |  |
| Target Group |  |
| Diagrams/Photos |  |
| Video |  |

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

- *What your application does,*
- *Why you used the technologies you used,*
- *Some of the challenges you faced and features you hope to implement in the future.*

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
  title={Scalable and heterogenous mobile robot fleet-based task automation in crowded hospital environments - a field test},
  author={Robert Valner and Houman Masnavi and Igor Rybalskii and Rauno Põlluäär and Erik Kõiv and Alvo Aabloo and Karl Kruusamäe and Arun Kumar Singh},
  journal = {Frontiers in Robotics and AI},
  year = {2022},
  doi={10.3389/frobt.2022.922835 },
}
