# DVPermissionHelper
[![](https://jitpack.io/v/Devil-Chen/DVPermissionHelper.svg)](https://jitpack.io/#Devil-Chen/DVPermissionHelper)

Android简单的权限请求，使用接口回调

## 依赖
**根bulid.gradle添加**
```
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```
**在项目bulid.gradle添加**
```
dependencies {
    implementation 'com.github.Devil-Chen:DVPermissionHelper:1.0.0'
}
```

**在类中定义了一些常用的权限，可直接使用**
```
    /**通讯录权限*/
    public static final String[] PERMISSION_CONTACTS = new String[]{
            Manifest.permission.WRITE_CONTACTS,
            Manifest.permission.GET_ACCOUNTS,
            Manifest.permission.READ_CONTACTS
    };

    /**电话*/
    public static final String[] PERMISSION_PHONE = new String[]{
            Manifest.permission.READ_CALL_LOG,
            Manifest.permission.READ_PHONE_STATE,
            Manifest.permission.CALL_PHONE,
            Manifest.permission.WRITE_CALL_LOG,
            Manifest.permission.USE_SIP,
            Manifest.permission.PROCESS_OUTGOING_CALLS,
            Manifest.permission.ADD_VOICEMAIL
    };

    /**日历*/
    public static final String[] PERMISSION_CALENDAR = new String[]{
            Manifest.permission.READ_CALENDAR,
            Manifest.permission.WRITE_CALENDAR
    };

    /**相机*/
    public static final String[] PERMISSION_CAMERA = new String[]{
            Manifest.permission.CAMERA
    };

    /**传感器*/
    @RequiresApi(api = Build.VERSION_CODES.KITKAT_WATCH)
    public static final String[] PERMISSION_SENSORS = new String[]{
            Manifest.permission.BODY_SENSORS
    };

    /**位置*/
    public static final String[] PERMISSION_LOCATION = new String[]{
            Manifest.permission.ACCESS_FINE_LOCATION,
            Manifest.permission.ACCESS_COARSE_LOCATION
    };

    /**存储*/
    public static final String[] PERMISSION_FILE_STORAGE = new String[]{
            Manifest.permission.READ_EXTERNAL_STORAGE,
            Manifest.permission.WRITE_EXTERNAL_STORAGE
    };

    /**麦克风*/
    public static final String[] PERMISSION_MICROPHONE = new String[]{
            Manifest.permission.RECORD_AUDIO
    };

    /**短信*/
    public static final String[] PERMISSION_SMS = new String[]{
            Manifest.permission.READ_SMS,
            Manifest.permission.RECEIVE_WAP_PUSH,
            Manifest.permission.RECEIVE_MMS,
            Manifest.permission.RECEIVE_SMS,
            Manifest.permission.SEND_SMS
    };
```

## 使用
```
    //判断是否有权限操作
    String[] permissions = DVPermissionUtils.arrayConcatAll(DVPermissionUtils.PERMISSION_CAMERA,DVPermissionUtils.PERMISSION_FILE_STORAGE,DVPermissionUtils.PERMISSION_MICROPHONE);
    if (!DVPermissionUtils.verifyHasPermission(this,permissions)){
        DVPermissionUtils.requestPermissions(this, permissions, new DVPermissionUtils.OnPermissionListener() {
            @Override
            public void onPermissionGranted() {
                Toast.makeText(MainActivity.this,"权限申请成功",Toast.LENGTH_SHORT).show();
            }

            @Override
            public void onPermissionDenied() {
                Toast.makeText(MainActivity.this,"权限申请失败",Toast.LENGTH_SHORT).show();
            }
        });
    }else{
        Toast.makeText(MainActivity.this,"权限已经申请",Toast.LENGTH_SHORT).show();
    }
});
```