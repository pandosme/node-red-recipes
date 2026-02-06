# Securing Node-RED in Cameras

A practical solution for securing Node-RED instances running on Axis cameras. Since users cannot directly access the `settings.js` file when Node-RED runs inside a camera, this flow provides an editable template that generates and stores the updated settings file with proper authentication configuration.

This recipe helps you implement Node-RED's security features as documented in the [official Node-RED security guide](https://nodered.org/docs/user-guide/runtime/securing-node-red).

![Flow screenshot](./flows.png)

***

## The Challenge

When Node-RED runs on Axis cameras, the `settings.js` file is not directly accessible to users through typical file system access. This makes it difficult to implement security settings like authentication, which requires editing the settings file.

## The Solution

This flow provides two utilities:

1. **Settings Editor Flow** (top, yellow) - Edit and save the `settings.js` file directly from Node-RED
2. **Password Hash Generator** (bottom, blue) - Generate bcrypt password hashes for user authentication

***

## Usage

### 1. Install Required Node

- Use the palette manager in Node-RED to install:
  **`node-red-contrib-bcrypt`**

### 2. Import the Flow

- Download [`flows.json`](./flows.json)
- In Node-RED, use menu: `Import` > paste JSON or upload file

### 3. Generate Password Hashes

**Important:** Node-RED requires bcrypt password hashes, not plain text passwords.

1. **Open the "Password" node** in the password hash generator flow (bottom flow)
2. **Enter your desired password** as plain text
3. **Click the inject/timestamp node** to trigger the flow
4. **Copy the generated hash** from the debug output (debug 3)
5. **Repeat for each user** you want to create (flows editor and dashboard can have different credentials)

### 4. Edit the Settings File

1. **Double-click the "Edit the setting.js here" template node** (in the top flow)
2. **Locate the commented security sections** - look for lines like:
   ```javascript
   //adminAuth: {
   //    type: "credentials",
   //    users: [{
   //        username: "admin",
   //        password: "$2a$08$...",
   //        permissions: "*"
   //    }]
   //},
   ```

3. **Remove the comment markers (//)** to enable authentication

4. **Replace the password hash** with the hash you generated:
   ```javascript
   adminAuth: {
       type: "credentials",
       users: [{
           username: "admin",
           password: "$2a$08$YOUR_GENERATED_HASH_HERE",
           permissions: "*"
       }]
   },
   ```

5. **Configure dashboard authentication separately** (if using Node-RED dashboard):
   ```javascript
   //ui: {
   //    middleware: function(req,res,next) { next(); }
   //},
   ```
   The flows editor (`adminAuth`) and dashboard (`ui`) have **separate authentication configurations** and can use different credentials.

### 5. Save and Apply Settings

1. **Click the inject/timestamp node** in the settings editor flow (top flow)
2. The updated settings will be written to `sdcard/NodeRED/node-red-data/settings.js`
3. **Restart Node-RED** for the changes to take effect
4. **Test your credentials** - you should now be prompted to log in

***

## Requirements

- Node-RED running on an Axis camera
- [node-red-contrib-bcrypt](https://flows.nodered.org/node/node-red-contrib-bcrypt) for password hash generation
- Basic understanding of JavaScript syntax (for editing settings)

***

## Key Concepts

### Two Separate Authentication Systems

1. **Flow Editor Authentication (`adminAuth`):**
   - Secures access to the Node-RED flow editor interface
   - Required for anyone who will create or modify flows
   - Configured in the `adminAuth` section of settings.js

2. **Dashboard Authentication (`ui.middleware`):**
   - Secures access to Node-RED dashboard views
   - Separate from flow editor credentials
   - Configured in the `ui` section of settings.js
   - Can use different usernames/passwords than the flow editor

### Uncommenting vs. Editing

The default `settings.js` file includes security configurations that are **commented out** (prefixed with `//`). To enable security:

1. **Remove the `//` prefix** from the relevant lines
2. **Replace placeholder values** (like password hashes) with your actual values
3. **Maintain proper JavaScript syntax** (commas, brackets, etc.)

### Password Hashing

- **Never use plain text passwords** in settings.js
- **Always generate bcrypt hashes** using the provided password hash generator flow
- **Each password generates a unique hash** - copy it immediately after generation

***

## Features

- ✏️ **In-Browser Settings Editor** - Edit settings.js without file system access
- 🔐 **Password Hash Generator** - Built-in bcrypt hash generation
- 👥 **Separate User Credentials** - Different logins for editor vs. dashboard
- 📝 **Template-Based** - Pre-configured settings structure with helpful comments
- 🔄 **One-Click Apply** - Inject to save changes instantly
- 📖 **Guided Configuration** - Follow Node-RED's official security best practices

***

## Tips

- **Test with a backup:** Before applying security, make note of current access methods in case you get locked out
- **Use strong passwords:** The password hash generator accepts any string, but use strong passwords for production
- **Different credentials recommended:** Use different usernames/passwords for flow editor and dashboard access
- **Document your credentials:** Store them securely - password recovery requires physical camera access
- **Restart is required:** Settings changes only take effect after Node-RED restart

***

## Troubleshooting

- **Locked out of Node-RED:**
  Physical access to the camera's file system may be required to reset settings.js. Contact your system administrator.

- **Password hash doesn't work:**
  Ensure you copied the complete hash from the debug output, including the `$2a$` prefix.

- **Syntax errors after editing:**
  JavaScript is strict about syntax. Ensure commas, brackets, and quotes are properly matched. Use the template structure as a guide.

- **Settings not applied:**
  Verify the file path is correct: `sdcard/NodeRED/node-red-data/settings.js`
  Restart Node-RED after making changes.

- **Dashboard still accessible without login:**
  Dashboard authentication is separate from editor authentication. Ensure you've uncommented and configured the `ui` section as well.

***

## Security Best Practices

For complete security guidance, refer to the official [Node-RED Security Documentation](https://nodered.org/docs/user-guide/runtime/securing-node-red).

Key recommendations:
- Enable both editor and dashboard authentication
- Use unique, strong passwords for each user
- Limit user permissions based on roles
- Regularly review and update credentials
- Keep Node-RED updated to the latest version

***
