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