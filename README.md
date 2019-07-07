# Qrcode
安卓扫码

此代码基本是使用kotlin编写实现扫码的相关操作，包含轻量级轻量级zxing.jar，基本代码实现与github上其他java版本基本相同！

# 二维码相关操作

```groovy

  /**
   * 生成二维码
   * param text 文字
   * param bitmapWidthAndHeight 图片的宽高
   */
  QrcodeUtil.createQrCode(text:String,bitmapWidthAndHeight:Int):Bitmap?

  /**
   * 获取图片二维码文件内容
   */
  QrcodeUtil.getQrCodeTextFromFile(filaPath:String) :String?


}
```

fragment使用，QrCodeFragment添加到界面即可使用。

QrCodeFragment的onresume实现了初始化camera，初始化时添加了权限检测checkPermission(android.Manifest.permission.CAMERA)，
请确认是否包含camera权限，否则无法实现扫码，可再activity添加权限检测后再初始花fragment

# QrCodeFragment部分说明代码以及方法

```groovy

  override fun onResume() {
    super.onResume()
    initCamera()
  }
  
  
  /**
   * 初始化相机
   */
  fun initCamera() {
    if (hasSurface && checkPermission(android.Manifest.permission.CAMERA)){
      //some init camera code ...
    }
  }

	/**
   * 设置扫码callback
   */
  fun setCallback(callback:QRCodeCallback)
  
  /**
   * 延时重新扫描
   */
  fun restartScanDelay(time: Long)
  
  /**
   * 延时重新扫描
   */
  fun restartScanDelay(time: Long)
  
  /**
   * 照明是否打开
   */
  fun isTorchOn(): Boolean 
  
  //扫码结果回掉
  interface QRCodeCallback {

  	fun onScanSuccess(text: String)

  	fun onScanFail()

  }

```