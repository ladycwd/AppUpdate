
[![](https://jitpack.io/v/MarsadMaqsood/AppUpdate.svg)](https://jitpack.io/#MarsadMaqsood/AppUpdate)


App Update
===================
Library to check app updates


<img src="https://github.com/MarsadMaqsood/AppUpdate/blob/master/assets/image.gif" alt="alt text" width="300" height="620">

    
#### Installation

**Maven**


	<repositories>
		<repository>
		    <id>jitpack.io</id>
		    <url>https://jitpack.io</url>
		</repository>
	</repositories>
	
	
	<dependency>
	    <groupId>com.github.MarsadMaqsood</groupId>
	    <artifactId>AppUpdate</artifactId>
	    <version>0.1.+</version>
	</dependency>
	
-------

**Gradle**

	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
	
	
	dependencies {
	        implementation 'com.github.MarsadMaqsood:AppUpdate:0.1.+'
	}
	
-------
```java
setTime(long miliseconds)
setUrl(String url)
setNotificationIcon(Drawable icon)
setUpdateTitle(String updatetitle)
setUpdateContentText(String updateContentText)
setDownloadDialogTitle(String title)
setToastMsg(String message)
setIsShowBackgroundDownload(boolean value)
setIsShowNetworkErrorToast(boolean value)
setIsShowToast(boolean value)
setCustomsActivity(class cls)
setCallback(CheckUpdateTask.Callback calback)
```

-------
**Json Structure**

    {
        "versionCode":VERSION_CODE,                    //int
        "versionName":"VERSION_NAME",                  //string
        "contentText":"DIALOG_CONTENT_TEXT",           //string
        "minSupport":MINIMUM_SUPPORTED_VERSION_CODE,   //int
        "url":"APP_DOWNLOAD_URL"                       //string
    }

---
	
#### How to Use

```java
UpdateWrapper updateWrapper = new UpdateWrapper.Builder(this)
        //set time in millisecounds
        .setTime(3000)
        //set notification icon
        .setNotificationIcon(R.mipmap.ic_launcher)
        //set update file url
        .setUrl("https://marsad.ml/update.json")
        //set custom update dialog title //Default is "Update Available"
        .setUpdateTitle("Custom Title Here")
        //set custom update dialog content if empty then text from json set
        .setUpdateContentText("Content Text Here")
        //set customs download dialog title
        .setDownloadDialogTitle("Title Here")
        //set customs activity
        .setCustomsActivity(cls)
        //set showToast. default is true
        .setIsShowToast(false)
        //add callback ,return new version info
        .setCallback((model, hasNewVersion) -> {
            Log.d("Latest Version", hasNewVersion + "");
            Log.d("Version Name", model.getVersionName());
            Log.d("Version Code", model.getVersionCode() + "");
            Log.d("Version Description", model.getContent());
            Log.d("Min Support", model.getMinSupport() + "");
            Log.d("Download URL", model.getUrl());
        })
        .build();

updateWrapper.start();

```        

-------

#### License

Apache License 2.0. See the [LICENSE](https://github.com/MarsadMaqsood/AppUpdate/blob/master/LICENSE) file for details.
