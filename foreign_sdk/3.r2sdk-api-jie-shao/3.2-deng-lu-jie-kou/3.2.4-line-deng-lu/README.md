# 3.2.4 LINE登录



**基本配置:**

1.buil.gradle里面的android下添加compileOptions配置

```text
android {
    ……
compileOptions {
    sourceCompatibility JavaVersion.VERSION_1_8
    targetCompatibility JavaVersion.VERSION_1_8
}
…….
}
```

2.AndroidManifest里面配置

```text
<meta-data android:name="line_channel_id" android:value="@string/line_channel_id" />
```

**功能说明：**

研发方可以直接调用该接口实现游戏的第三方LINE登录。接口内部会先进行LINE自身的登录然后再进行R2 SDK的登录，研发方无需关心内部实现只需要在接口回调中获取r2Uid作为玩家的唯一标识即可。

**接口形式：**

```text
public static void doLogin(Activity activity, R2Callback<ResponseLoginData> callback)
```

**接口示例**

```text
R2LineApi.doLogin(this, new R2Callback<ResponseLoginData>() {
    @Override
    public void onSuccess(ResponseLoginData result) {
        Log.i("r2_sdk_demo", "finally login successfully, uid = " + result.toString());
        showToastMsg("login success: " +  result.toString());
        mR2Uid = result.getR2Uid();
        loginSuccess(result.getR2Uid());
    }

    @Override
    public void onCancel() {
        Log.e("r2_sdk_demo","login onCancel ");
    }

    @Override
    public void onError(R2Error error) {
        Log.e("r2_sdk_demo","login falied, err = " + error);
    }
});
```

