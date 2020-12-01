# 4.2 Google Iab 支付接口



所有与Google Iab支付相关的接口都以静态方法形式封装在R2GoogleIabApi类中。如无特殊说明，所有接口必须在Android UI线程中调用。接口调用后，SDK通过统一接口形式回调结果数据给研发方。

泛型接口形式如下：

```text
public interface GoogleIabCallback<T> {
    /**
     * 接口调用成功，
     * @param  T 为返回的数据
     */
    public void onSuccess(T t);
    /**
     * 操作取消
     */
    public void onCancel();
    /**
     * 接口调用中发生错误 - 可以通过 error.getCode() 和error.getDescription()
     * 来查看具体错误信息，便于调试
     * @param error 返回的错误
     */
    public void onError(GoogleIabError error);
}
```

