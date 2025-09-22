# Sample Scenes

The main scene to build is "TheWorldBeyond.unity." Smaller scenes in the project simplify the development experience, located in the [SampleScenes](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/SampleScenes) folder:

## Passthrough Pet
![Passthrough Pet](../Media/ScreenshotPassthroughPet.png "Passthrough Pet")

Explore augmented pet behavior here. It provides Scene elements as occluding colliders so Oppy convincingly renders behind and avoids furniture. A NavMesh is created for her to walk on, and pressing the index trigger on the right controller sets a target towards which she navigates. Learn more about Unity's navigation system from [their documentation.](https://docs.unity3d.com/Manual/com.unity.ai.navigation.html)

* NavMesh created from Scene objects in [`NavMeshSurface.BuildNavMesh()`](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/Scripts/SamplePetExperience.cs#L47)
* Pet walking via [`NavMeshAgent.SetDestination()`](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/Scripts/SamplePetExperience.cs#L72)
* Animation controller demonstrating switching between idle/running
* Occlusions using Scene objects provided by the prefabs in this scene's `OVRSceneManager`
* Control character look direction with [`SamplePet.DoLookAtBehavior()`](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/Scripts/SamplePet.cs#L101)
* Blob shadow to help visually ground virtual content

## Passthrough Room
![Passthrough Room](../Media/ScreenshotPassthroughRoom.png "Passthrough Room")

Scene elements are loaded, and wall/ceiling/door/window game objects are destroyed. A modified ball shooter demonstrates collision with Scene elements. This scene can serve as a base when your room is the center of a VR playspace.

* Floor outline as mesh via `OVRScenePlaneMeshFilter`
* Grass distribution using floor outline and exterior space in [`SampleBoundaryDebris.CreateBoundaryDebris()`](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/Scripts/SampleBoundaryDebris.cs#L79) and [`SampleBoundaryDebris.CreateExteriorDebris()`](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/Scripts/SampleBoundaryDebris.cs#L113)
* Virtual objects culled when within the room
* [`VolumeAndPlaneSwitcher`](https://developers.meta.com/horizon/documentation/unity/unity-scene-plane-and-volume-sample) automatically converts plane anchors (Deck, Couch) to volumes

## Virtual Frames
![Virtual Frames](../Media/ScreenshotVirtualFrames.png "Virtual Frames")

Rendering a virtual world outside your windows is achieved with rendering tricks shown in this scene. Prefabs similar to the overrides in this scene's OVRSceneManager are required. The virtual environment renders first, then the frame-and-depth-occluder prefab where windows and doors are. Finally, Scene walls render 0 to alpha, revealing Passthrough.

* Furniture resizer to demonstrate consistent frame width
* Floor fade material at door base
* Grass at door perimeter instantiated in [`SampleDoorDebris.SpawnDebris()`](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/Scripts/SampleDoorDebris.cs#L46)
* User notification if missing door or windows in Scene data

## Voice Transcription
![Voice Transcription](../Media/ScreenshotVoiceTranscription.png "Voice Transcription")

This sample transcribes the user's speech to text, including a button supported by the Interaction SDK and a text dialog prefab for developers to provide more information to users.

* Get text transcriptions from the [Voice SDK](https://developers.meta.com/horizon/documentation/unity/voice-sdk-overview/)
* Unity Canvas using hands or controllers powered by the [Interaction SDK](https://developers.meta.com/horizon/documentation/unity/unity-isdk-interaction-sdk-overview/)
* *SampleNotif* prefab for displaying information and requesting user action
* Sample code for checking and requesting microphone permissions in [`SampleVoice.CheckPermissionsAndContinue()`](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/Scripts/SampleVoice.cs#L87)
