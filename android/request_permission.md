# Requesting Permissions
> 29/06/2017

- If the device is running Android 6.0 (API level 23) or higher, and the app's **`targetSdkVersion is 23 or higher`**, the app requests permissions from the user at run-time. The **user can revoke the permissions at any time**, so the app needs to check whether it has the permissions every time it runs.
- If the device is running Android 5.1 (API level 22) or lower, or the app's **`targetSdkVersion is 22 or lower`**, the system asks the user to grant the permissions when the user installs the app. If you add a new permission to an updated version of the app, the system asks the user to grant that permission when the user updates the app. Once the user installs the app, the only way they can revoke the permission is by uninstalling the app.

- Function to request permission at runtime :
  ```java
  public static final int REQUEST_WRITE_STORAGE = 100;
  
  /**
   * Checks for permission to write to storage device.
   * Requests permission, if not exists
   */
  public void getWritePermission() {
        // Here, thisActivity is the current activity
        if (ContextCompat.checkSelfPermission(this,
                Manifest.permission.WRITE_EXTERNAL_STORAGE)
                != PackageManager.PERMISSION_GRANTED) {

            // Should we show an explanation?
            if (ActivityCompat.shouldShowRequestPermissionRationale(this,
                    Manifest.permission.WRITE_EXTERNAL_STORAGE)) {

                // Show an explanation to the user *asynchronously* -- don't block
                // this thread waiting for the user's response! After the user
                // sees the explanation, try again to request the permission.

            } else {
                // No explanation needed, we can request the permission.
                ActivityCompat.requestPermissions(this,
                        new String[]{
                            Manifest.permission.WRITE_EXTERNAL_STORAGE,
                        },
                        REQUEST_WRITE_STORAGE);
            }
        }
    }
    
  @Override
  public void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults) {
      super.onRequestPermissionsResult(requestCode, permissions, grantResults);
      switch (requestCode) {
          case REQUEST_WRITE_STORAGE: {
              if (grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                  Toast.makeText(this, "The app was allowed to write to your storage!", Toast.LENGTH_SHORT).show();
                  // Reload the activity with permission granted or use the features what required the permission
              } else {
                  Toast.makeText(this,
                          "The app was not allowed to write to your storage. Hence, it cannot function properly. Please consider granting it this permission",
                          Toast.LENGTH_SHORT).show();
              }
          }
      }
  }
    
  ```
