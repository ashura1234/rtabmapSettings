# Dependencies Installation
### Windows
- Azure Kinect Camera: [Azure Kinect SDK 1.4.1.exe](https://download.microsoft.com/download/3/d/6/3d6d9e99-a251-4cf3-8c6a-8e108e960b4b/Azure%20Kinect%20SDK%201.4.1.exe)
# Rtapmap Installation
### Windows
[Download](https://github.com/introlab/rtabmap/releases/download/0.20.8/RTABMap-0.20.8-win64-cuda11_1.exe) and install
# Import Settings
[Azure Kinect Config File](https://raw.githubusercontent.com/pearnets/rtabmapSettings/main/config_Azure_Kinect.ini)
[Realsense L515 Config File](https://raw.githubusercontent.com/pearnets/rtabmapSettings/main/config_L515_1080p.ini)
[Realsense D435i Config File](https://raw.githubusercontent.com/pearnets/rtabmapSettings/main/config_D435i.ini)
[Realsense D435i Camera Settings File](https://raw.githubusercontent.com/wiki/IntelRealSense/librealsense/d400_presets/HighResHighAccuracyPreset.json)

Window -> Preferences -> General Settings -> Load settings
Select correesponding .ini file -> OK

**D435i ONLY**: 
Window -> Preferences -> Source -> D400 Series Visual Presets -> Select Camera Settings File -> OK
# Depth Calibration
- Find a large flat wall with texture
- Start recording 10 meters away from the wall. Record slowly to and from the wall while rotating the camera:
	- File -> New database
Press the Start button
	- [Demo Video](https://www.youtube.com/watch?v=cjDFDPpLnRc&ab_channel=matlabbe)
[Demo Video 2](https://www.youtube.com/watch?v=BDRPv4cVSwg&ab_channel=AlexTeichman)
- Press the Stop button when finished
- File -> Depth calibration -> Calibrate
- Save the calibration file
- Window -> Preferences -> Source -> Depth Image Filtering -> select the saved calibration .bin file  -> OK

Calibrated Models:
[Azure Kinect Distortion Model](https://github.com/pearnets/rtabmapSettings/blob/main/distortion_model_Azure_Kinect.bin?raw=true)
[Azure Kinect 2160p Distortion Model](https://github.com/pearnets/rtabmapSettings/blob/main/distortion_model_Azure_Kinect_2160p.bin?raw=true)
[Realsense L515 Distortion Model](https://github.com/pearnets/rtabmapSettings/blob/main/distortion_model_L515_new.bin?raw=true)
[Realsense D435i Distortion Model](https://github.com/pearnets/rtabmapSettings/blob/main/distortion_model_D435i.bin?raw=true)

To load distortion model:
Window -> Preferences -> Source -> Depth Image Filtering -> Choose corresponding .bin file

# Capture Point Clouds
1. File -> Close database
2. File -> New database
3. Set the camera on a tripod on the dolly and raise the tripod head to ~5 ft high from the floor
4. Tilt the camera ~ 30 degree up from the horizontal plane and make sure part of the ceiling is captured
5. Find an object with clear texture as the starting point then press the Start button
6. Push the dolly and scan around the target space. Make sure all ceilings and walls are captured and shown in the 3D Map window (Scoll on the 3D Map window to zoom in or out. Click and drag to rotate.)
	- <u>**If the 3D View and Odometry windows turn red, retreive back to the last camera position shown translucently in the Odometry window and try to match it until both window turn yellow or black.**</u>
	- Avoid mirrors and reflective surfaces.
	- Keep the camera within the effective range from the target surfaces
		- Azure Kinect: < 3 meters (WFOV mode), < 5 meters (NFOV mode)
		- Realsense L515: < 3 meters
		- Realsense D435i: < 2 meters
8. Make sure to capture a loop (return back to where the record starts)
9. Tilt the camera ~ 30 degree down from the horizontal plane and make sure part of the floor is captured
10. Repeat step 6 and make sure part of the previously scanned walls and the floor are captured
11. Press the Stop button
12. Tools -> Post-processing -> OK 
13. File -> Close database -> Save

# Output .ply Point Cloud
[Azure Kinect Output Settings File](https://raw.githubusercontent.com/pearnets/rtabmapSettings/main/Output_Settings_Azure_Kinect.ini)
[Realsense D435i and L515 Output Settings File](https://raw.githubusercontent.com/pearnets/rtabmapSettings/main/Output_Settings_D435i_L515.ini)

- File -> Open database -> select saved database
- File -> Export 3D clouds
- Load Settings -> select correesponding .ini file -> Save
