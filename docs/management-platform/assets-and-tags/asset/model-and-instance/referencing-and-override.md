# Referencing and Override

## **References**

References in the VC Hub system refer generically to relationships between models and instances, and instances refer generically to model instances and instances.

References can occur in multiple hierarchies, so there may also be a reference relationship between two instances.

Below we use an example to illustrate the relationship between them.

Assumption:

- There is a "Motor" model under the Model module, and there is an "Power" tag under "Motor";
- There is a "Line" model under the Model module, and a model instance "Motor Instance" of the "Motor" model under "Line";
- Under the Instance module, there is an instance of the "Line" model, named "Line Instance".

The relationship of each object is shown in the figure below:

![alt text](29.png)


#### **Motor**

There is a subset of "instantaneous power" tags under the "motor" model, and the whole "motor" is independent, it does not depend on any object.

#### **Line and Motor**

There is a subset of "Motor Instance" instances under the "Line" model, and since "Motor Instance" references the "Motor Since "Motor Instance" references the "Motor" model, the "Instantaneous Power" tag from the "Motor" model also exists under the "Motor Instance". The "Instantaneous Power" tag under the "Line" model is referenced to the "Instantaneous Power" tag under the "Motor" model. The "Instantaneous Power" tag in the " Line" model is referenced to the "instantaneous power" tag in the "Motor" model.

#### **The "Motor Instance" is referenced from the "Motor" model.**

The Instantaneous Power tag under the Motor instance is referenced from the Instantaneous Power object under the Motor model.

**Production Line Instances and Production Lines**

The "Line Instance" instance is referenced from the "Line" model, and there will be a "Motor Instance" under the "Line Instance". The "Motor Instance" will exist under the "Line Instance" and will reference the "Instantaneous Power" tag under the "Motor Instance".

The "Line Instance" is referenced from the "Line" model.

The "Motor Instance" under "Line Instance" is referenced from the "Motor Instance" under "Line".

The "Instantaneous Power" tag under "Motor Instance" under "Line Instance" is referenced from the "Motor Instance" under "Line". The "Instantaneous power" tag under "Motor instance" under "Line" is referenced from the "Instantaneous power" tag under "Motor instance" under "Line".

#### **Influence between referenced objects**

When there is a reference relationship between two objects, besides the referencing object will bring over the subset objects under the referenced object, similarly, when the referenced object adds and deletes its own subset, it will affect the referencing object, for example:

When you add a tag named "Switch State" under the "Motor" model, the "Motor Instance" under the "Line" model will be automatically added. A tag named "Switch State" is automatically added to the "Motor Instance" under the "Line" model, because the "Motor Instance" under the "Line Instance" is referenced from the "Line Instance" model. Because "motor instance" under "Line instance" is referenced from "motor instance" under "production line" model, a "switch state" tag is also added to "motor instance" under "Line instance". A tag for "Switch State" is also added to the "Motor Instance" under "Line Instance".

When the "Instantaneous power" under the "Motor" model is deleted, the "Instantaneous power" tag is also added to the "Motor instance" under the "Line" model. The "Instantaneous power" tag is deleted from the "Motor instance" in the "Line" model, and the "Instantaneous power" in the "Line instance" is also deleted at the same time.

"The "Motor Instance" in the "Line" model is created by reference to the "Motor" model. Similarly, the "Line Instance" is referenced from the "Line" model, so we can't do anything to the subset of "Line Instance". Similarly, the "Line Instance" was created by referencing the "Line" model, so we cannot add or delete any subsets of the "Line Instance". In this case, if we want to modify a node under an instance, we have to operate under its root reference model. For example, if we want to add a tag "Daily Energy Consumption" to "Motor Instance" under "Line Instance", then I want to add a tag "Daily Energy Consumption" to "Motor Instance". For example, if we want to add a tag "Daily Energy Consumption" to the "Motor Instance" of the "Instance", we only need to add it under the "Motor" model, and the program will automatically synchronize the referenced data.

## **Override**

In the above, the definition of reference is introduced, and the concept of rewriting occurs between the reference and the referenced node.

![alt text](30.png)

As shown in the figure, the "instantaneous power" under the "line instance" is referenced from the "instantaneous power" under the "line" model, and the "instantaneous power" under the "line" model is referenced from the "motor" model. The "instantaneous power" under the "line" model is referenced from the "instantaneous power" under the "motor" model, which, in general, realizes a 2-tier referencing Overall, a 2-layer referencing relationship is realized.

We use "Instantaneous Power Out", "Instantaneous Power Middle", and "Instantaneous Power In" to refer to them (the references do not have any meaning here, and are only for (there is no meaning in the substitution here, it is only for the sake of explanation).

Suppose we create "Instantaneous Power In" with an initial value of 50 and a unit of "W", then we initialize "Instantaneous Power Out", When we initialize "Instantaneous Power Out" and "Instantaneous Power Middle", their initial value will also be 50, and the unit of configuration will also be "W", under this premise:

1. At this time we modify the initial value of "Instantaneous Power In" to 100, because "Instantaneous Power Middle" referenced from "Instantaneous Power In", then The initial value of "Instantaneous Power Middle" will be synchronized to 100, and since "Instantaneous Power Out" is referenced from "Instantaneous Power Middle", then The initial value of "Instantaneous Power Middle" is also synchronized to 100;
2. We modify the initial value of "Instantaneous Power Middle" to 80, and because "Instantaneous Power Out" is referenced from "Instantaneous Power Middle", then the initial value of "The initial value of "Instantaneous Power Middle" will also be synchronized to 80, and the initial value of "Instantaneous Power Middle" will be in a rewrite state. At this time, if the value of "Instantaneous power In" is modified, it will not be synchronized to "Instantaneous power Middle", nor will it be synchronized to "Instantaneous power Out", but if the unit of "Instantaneous power In" is modified, the value of "Instantaneous power Out" will be synchronized to "Instantaneous power Out". However, if we change the unit of "In", the synchronization will still be performed;
3. If we modify the initial value of "Instantaneous Power Out" to 200, its initial value will be rewritten, and no matter how the initial values of "Instantaneous Power Middle" and "Instantaneous Power In" are updated, the synchronization will still be carried out; however, if we modify the unit of "Instantaneous Power In", the synchronization will still be carried out. No matter how the initial values of "Instantaneous Power Middle" and "Instantaneous Power In" are updated, the initial value of "Instantaneous Power Out" will not be affected.

In summary, override only exists between the reference and the referenced, when the configuration of the referenced object is modified, the referenced object to modify the configuration, it will not be synchronized to the referenced object, on the contrary, when the configuration of the referenced object is configured for the configuration of the special modification, then the referenced object to modify the configuration will be synchronized to the referenced object.

#### **How to override**

When a reference object is overridden, a "green dot" is displayed on the right side of the input box, as shown in the initial value in the following figure.

![alt text](31.png)

Users need to lift the override, directly click on the "green dot" will be grayed out, the initial value will be reset to the initial value of the referenced object, the following figure is the initial value of the referenced object is 0, then it will be reset to 0. 

![alt text](32.png)


There is a special case where the initial value of "Instantaneous Power Out" is inherited from the initial value of "Instantaneous Power Middle", which is 100, and we want to rewrite the initial value of "Instantaneous Power Out" to 100. We want to rewrite the initial value of "Instantaneous Power Out" to 100, so how do we uninherit the relationship between them?

In this case, it is not effective to change the initial value of "Instantaneous Power Out" to 100. The rewrite flag in the configuration popup window - "gray dot on the right side of the configuration item" provides an active rewrite status change function. Users can click on the "Gray Dot" to change it to green.

![alt text](33.png)

