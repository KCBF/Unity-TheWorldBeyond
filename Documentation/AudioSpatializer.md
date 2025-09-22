# Audio Spatializer

Audio in The World Beyond uses the *Oculus AudioManager* and *Oculus Spatializer*. Understand it deeply from our documentation [here](https://developers.meta.com/horizon/documentation/unity/audio-spatializer-features/). The mixer for the project exists at [Assets/TheWorldBeyond/Audio/WorldBeyondAudioMixer.mixer](../Assets/TheWorldBeyond/Audio/WorldBeyondAudioMixer.mixer).

* Use simple raycasting for occlusion. For instance, if a sound is in the virtual world behind your Passthrough wall. See [`SoundEntry_Manager.HandleObstructed()`](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/Scripts/SoundEntry_Manager.cs#L94).
* The system mutes environment audio when all Passthrough walls are closed. Audio increases as you open each wall. When a wall status changes, the system adjusts the audio in [`AudioManager.SetRoomOpenness()`](https://github.com/oculus-samples/Unity-TheWorldBeyond/blob/main/Assets/Scripts/AudioManager.cs#L444).
