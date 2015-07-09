If, at any point, you need help, have questions, or get unexpected or unexplained errors, please don't hesitate to use the [Google Group](http://groups.google.com/group/android2cloud).

# Pre-Requisites #

  * An [App Engine](http://appengine.google.com) account
  * [Python](http://www.python.org)
  * The server [source](http://android2cloud.googlecode.com/files/android2cloud-app-engine.zip)
  * The Chrome extension [source](http://android2cloud.googlecode.com/files/android2cloud-chrome.zip)

# Precautions #

By installing your own server, you are affirming your understanding that updates to the Android application and/or Chrome extension may break your implementation. You should keep your server up to date at all times, as the way these component pieces pass information is liable to change.

# Installing the server #

  1. Create a new App Engine application; make a note of the ID (we'll reference that as app-id from now on)
  1. Extract/unzip the downloaded source to a convenient location
  1. Navigate to the location you extracted the source to in your console/terminal/shell
  1. Modify src/app.yaml to replace android2cloud with app-id
  1. Run the following command:
```
python google_appengine/appcfg.py update src
```
  1. When the application finishes uploading, you will need to wait for App Engine to build the indexes. As soon as that is finished, your server is set up. To check the status of your indexes, log in to the control panel at http://appengine.google.com, choose app-id, and choose Datastore Indexes on the left. It will either say "Building" (not ready) or "Serving" (ready).

# Configuring Android #

  1. Open the application
  1. Select "Change Account"
  1. Select "Add Account"
  1. Enter an account name for Account
  1. Enter http://app-id.appspot.com (http:// is necessary, no trailing /) for Host
  1. Save
  1. Log in
  1. Grant access
  1. Select the new account

# Configuring Chrome #

Please note, Chrome's support for this is nearly nonexistent. That is my fault, and I'm working to remedy it. In the meantime, please forgive the numerous complicated steps below.

  1. Unzip the source archive to a permanent location
  1. Open manifest.json
  1. Change the server variable from "android2cloud.appspot.com" to "app-id.appspot.com"
  1. Change the consumer\_key and consumer\_secret to "anonymous"
  1. Save and close manifest.json
  1. Open background.html
  1. Change every instance of "android2cloud.appspot.com" with "app-id.appspot.com"
  1. Save and close background.html
  1. Open chrome://extensions
  1. Click "developer mode"
  1. Select "Load unpacked extension"
  1. Open the folder you unzipped the source to
  1. Authenticate when the window opens