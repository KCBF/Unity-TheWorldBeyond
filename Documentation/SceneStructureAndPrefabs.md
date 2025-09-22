# Scene Structure & Prefabs

The main scene in The World Beyond is "TheWorldBeyond.unity," containing the core experience. This scene should be the only one in the Build settings. Most content in this scene is pre-existing, meaning the system doesn't spawn it at runtime. Exceptions include the virtual room (visible through the flashlight), Passthrough walls, and ground grass in your room. Other notes about the scene include:

* *NavMesh:* Oppy walks on this, and it lives under the Environment/EnvRoot object. *NavMesh* is part of the Unity Editor. The scene adds obstacles dynamically (e.g., your room walls, furniture, and trees/rocks in the foreground).
* [*WorldBeyondManager:*](../Assets/TheWorldBeyond/Scripts/GameManagement/WorldBeyondManager.cs) Holds the *WorldBeyondManager* component, managing the whole demo. Consider *WorldBeyondManager* as the `main()` function.
* [*MultiToy:*](../Assets/TheWorldBeyond/Scripts/Toy/MultiToy.cs) You can attach *MultiToy* to your hand/controller. Only one MultiToy will ever exist, and you can attach it to either hand.
* *Oppy:* Everything related to Oppy is in *Oppy*.
* *Environment:* Everything in the virtual world, except the UFO, is included in *Environment*.
