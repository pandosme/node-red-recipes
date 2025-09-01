***

# Thermal Monitoring and Alarm Threshold Adjustment for Axis Thermal Cameras

Easily monitor thermal alarms with ambient temperature compensation using an Axis thermal camera and Node-RED.  
This recipe provides a dashboard to visualize live video, track ambient temperature, and automatically set alarm thresholds based on changing ambient conditions.

***

## Usage

1. **Install Required Software & Nodes**
   - Make sure **Node-RED** is installed and running on a host in the same network as your Axis camera.
   - Install the [node-red-dashboard](https://flows.nodered.org/node/node-red-dashboard) for visualization.
   - Install [node-red-contrib-axis-com](https://flows.nodered.org/node/node-red-contrib-axis-com) for connecting to Axis cameras.

2. **Import the Flow**
   - Download [`flows.json`](./flows.json)
   - In Node-RED, select `Import` -> paste JSON or upload file.

3. **Configure Camera Settings**
   - Double-click relevant nodes (camera IP, credentials, etc.) to enter your Axis thermal camera details.
   - By default, the flow supports a **single Axis thermal camera**. You can extend it to support multiple cameras if needed.

4. **Launch the Dashboard**
   - Access the Node-RED dashboard to:
     - View live video from your thermal camera
     - Monitor ambient and alarm area temperatures over time
     - Adjust alarm thresholds using user-defined offsets in the UI

***

## Features

- **Live Video Monitoring:**  
  View your thermal camera feed directly in the dashboard.

- **Ambient Temperature Tracking:**  
  Automatically monitor and display ambient temperature changes.

- **Automatic Alarm Threshold Adjustment:**  
  Keeps alarm area temperature thresholds in sync with ambient shifts at a user-defined offset.

- **Manual Adjustment Option:**  
  Easily set offsets and review current alarm/ambient readings from the dashboard.

- **No Code Changes Needed:**  
  All necessary controls available from the Node-RED dashboard.

***

## Requirements

- Axis thermal camera with HTTP API enabled
- [Node-RED](https://nodered.org/)
- [node-red-dashboard](https://flows.nodered.org/node/node-red-dashboard)
- [node-red-contrib-axis-com](https://flows.nodered.org/node/node-red-contrib-axis-com)

***

## Limitations

- Currently supports **only a single thermal camera** (can be extended by editing the flow).
- Ensure all components and credentials are correctly set up in Node-RED.

***

## Screenshots

**Dashboard Example:**  


**Flow Overview:**  


***

## Troubleshooting

- If the camera feed doesn’t display, verify IP address, authentication, and network connectivity.
- For ambient/alarm value issues, ensure correct function node settings and Axis camera compatibility.

***

## Example Flow

The flow enables you to:
1. Monitor live video and temperature data from your Axis thermal camera.
2. Automatically adjust alarm area thresholds when ambient temperature changes.
3. Use the dashboard for all key interactions—no manual editing required in the flow.

***

**Ready to use!**  
Import, configure, and go—visualize and manage thermal alarms with ease.
