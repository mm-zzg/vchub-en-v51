# Assets and Tags

 Assets can be used in configuration software to represent various devices, facilitiesor materials in the real world. The hierarchy of assets allows the user tovisualize the structure and layout of the system.

 In the VC Hub system, tags are used as a medium to establish communicationwith the actual production device through various common industrial protocols for the purpose of equipment detection and issuing commands.

 A tag is an abstract concept used to identify real-time data or configuration information. It can represent the measured value of a sensor, the state of a device, or other device-related data.

 An asset is the top node of a tag. There can be any number of assets in a VC Hub system, and the user can create tags to be maintained in any asset, with the tags in each asset isolated from each other, and the tags are dependent on the assets to exist in the system.

 It can be considered that tags are atomic level objects of assets, and assets are containers of tags, and multiple tags can be created in one asset. (Based on performance and a reasonable grouping mechanism, it is recommended that the number of tags in a single asset does not exceed 30,000.)

 In order to be applicable to complex real production environments, VC Hub introduces the concept of models and instances, which are located in the same subset of assets as tags, in order to make it easier for the user to model real devices, reuse the model and instantiate multiple device instances.

## **An example**

 For example, in a workshop, there are 5 production lines, and each line is equipped with 10 motors, assuming that these 10 motors are of the same brand and model,then in the model management, we can first create a model of the motor, which can be created under the model with multiple tags, and then create a model of the line, and then create 10 instances of the motor using the motor model under the model of the line, and we get a model of the line with 10 motor instances mounted under it.

 In the early stage of production, which is the case of the 5 production lines we are talking about, we switch to instance management, create 5 production line instances by referencing the production line model, and update the difference configuration of the tags under the motors in the 5 production lines.

 Under the above operation, finally, we get 5 sets of complete production line data,which makes it easier to modify the program in case of increasing or decreasing the production line in the subsequent workshops.

 The models, examples and tags mentioned here are all attributed to one asset, the data between the assets are isolated from each other and cannot be referenced to each other. The examples here are mainly used to understand why the VC Hub system proposes the concept of assets on top of the tags, for the specific use of the module, please refer to the introduction of the specific manual for the relevant functions of this module.

