# Node-RED Recipes for Axis Cameras

Welcome! This project is a curated library of practical **Node-RED flows ("recipes") designed specifically for Axis devices**. Whether you're integrating, automating, or managing Axis devices—and even if you're not a full-time developer—these recipes will streamline your workflow.

**[Node-RED](https://nodered.org/)** is a user-friendly automation platform that makes working with Axis devices simple for engineers, integrators, and IT professionals. Each recipe below is ready for real-world use or as a starting point to adapt for your specific needs.

***

## 📋 Quick Comparison

| Recipe | Complexity | Key Features | Best For |
|--------|-----------|--------------|----------|
| [🌅 Sunrise/Sunset WDR](#-sunrisesunset-wdr-control) | ⭐ Beginner | Scheduled automation, Light-based control | Day/night optimization |
| [💾 SD Recording Export](#-export-sd-recordings-to-local-mp4) | ⭐⭐⭐ Advanced | Video archival, Format conversion, Indexing | Backup & compliance |
| [📹 Dashboard Video & Analytics](#-dashboard-video--object-analytics) | ⭐⭐ Intermediate | Live streaming, Object detection overlay | Real-time monitoring |
| [🌡️ Thermal Monitoring](#-thermal-monitoring--alarm-adjustment) | ⭐⭐⭐ Advanced | Temperature tracking, Auto-adjusting alarms | Industrial safety |
| [🔒 Securing Node-RED](#-securing-node-red-in-cameras) | ⭐⭐ Intermediate | Settings editor, Password hashing, Authentication | Security hardening |

***

## 🎯 Recipes by Use Case

### 🌅 Sunrise/Sunset WDR Control
**Complexity:** ⭐ Beginner | **Setup Time:** 5 minutes

Automatically turns Wide Dynamic Range (WDR) on at sunrise and off at sunset, ensuring optimal image quality in changing lighting conditions.

**Key Features:**
- ⏰ Automated scheduling based on sunrise/sunset times
- 📍 Location-aware (automatically calculates sun times)
- 🎛️ Simple configuration - just set camera IPs and credentials

**Requirements:** `node-red-contrib-cb-suncron`

**[View Recipe →](recipes/sunrise-sunset/README.md)**

---

### 💾 Export SD Recordings to Local MP4
**Complexity:** ⭐⭐⭐ Advanced | **Setup Time:** 15-20 minutes

Complete video archive management system that fetches recordings from camera SD cards, converts them to MP4, and maintains a searchable local index.

**Key Features:**
- 📥 Automated download from camera SD storage
- 🔄 MKV to MP4 conversion via ffmpeg
- 📊 Searchable JSON index with metadata
- 🗂️ Date-organized file structure
- 🧹 Automatic cleanup of source files
- ⚡ Concurrent processing with throttling

**Requirements:** `ffmpeg` (system), Node-RED exec node

**[View Recipe →](recipes/export-SD-recordings-to-local-MP4/README.md)**

---

### 📹 Dashboard Video & Object Analytics
**Complexity:** ⭐⭐ Intermediate | **Setup Time:** 10-15 minutes

Interactive dashboard displaying live camera feeds with optional object detection analytics overlay for real-time monitoring and analysis.

**Key Features:**
- 📺 Live video streaming in Node-RED dashboard
- 🎯 Object detection visualization (via DataQ ACAP)
- ✏️ User-defined area selection tool
- 📡 MQTT integration for real-time analytics
- 🎨 Customizable overlays and UI elements

**Requirements:** `node-red-dashboard`, MQTT broker, DataQ ACAP (for analytics)

**[View Recipe →](recipes/dashboard-video/README.md)**

---

### 🌡️ Thermal Monitoring & Alarm Adjustment
**Complexity:** ⭐⭐⭐ Advanced | **Setup Time:** 15-20 minutes

Professional thermal monitoring dashboard with intelligent alarm threshold management that automatically adjusts based on ambient temperature changes.

**Key Features:**
- 📹 Live thermal video feed display
- 📈 Temperature history tracking and visualization
- 🎯 Auto-adjusting alarm thresholds with user-defined offsets
- 🌡️ Ambient temperature compensation
- 🎛️ Dashboard-based configuration (no code editing needed)
- 📊 Real-time temperature graphs

**Requirements:** `node-red-dashboard`, `node-red-contrib-axis-com`

**[View Recipe →](recipes/thermal-monitoring/README.md)**

---

### 🔒 Securing Node-RED in Cameras
**Complexity:** ⭐⭐ Intermediate | **Setup Time:** 10 minutes

Secure Node-RED instances running on Axis cameras with an editable settings template and password hash generator. Solves the challenge of configuring authentication when the settings.js file isn't directly accessible.

**Key Features:**
- ✏️ In-browser settings.js editor and updater
- 🔐 Built-in bcrypt password hash generator
- 👥 Separate authentication for flow editor and dashboard
- 📝 Template-based configuration with guided comments
- 🔄 One-click settings deployment
- 📖 Follows official Node-RED security best practices

**Requirements:** `node-red-contrib-bcrypt`

**[View Recipe →](recipes/securing-node-red-in-cameras/README.md)**

***

## About

This collection is **community-driven** and open source. Want to add a recipe, suggest an improvement, or ask a question?  
_The [GitHub repository](https://github.com/pandosme/node-red-recipes) is open for your pull requests, issues, and feedback!_

***

**Need help getting started?**  
Each recipe folder includes a README with setup instructions and usage tips.  
Whether you’re new to Node-RED or Axis scripting, these flows provide clear, working solutions that don’t require deep programming knowledge.

***

Feel free to **explore, use, and share** these examples and automation ideas!

***
