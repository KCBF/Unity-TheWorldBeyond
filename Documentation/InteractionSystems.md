# Interaction Systems

You can include hands-support using Interaction components with little understanding of the code. Learn more about the [*Interaction SDK*](https://developers.meta.com/horizon/documentation/unity/unity-isdk-interaction-sdk-overview/) from our documentation. In The World Beyond, we use the *Interaction SDK* to let users grab and release energy orbs.

* The *OVRInteraction* object exists under the *OVRCameraRig* prefab. Important fields on the *WorldBeyondManager* game object point to children of this interaction rig.
* The ball prefab is located in [Assets/TheWorldBeyond/VFX/EnergyBall/EnergyBallPrefab.prefab](../Assets/TheWorldBeyond/VFX/EnergyBall/EnergyBallPrefab.prefab). The *Interaction SDK* manages many components on the object.
* Other hand behaviors like wall opening or toy switching are custom and exist outside *ISDK*.
