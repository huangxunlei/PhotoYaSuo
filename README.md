# PhotoYaSuo
[![](https://jitpack.io/v/huangxunlei/PhotoYaSuo.svg)](https://jitpack.io/#huangxunlei/PhotoYaSuo)

### Step 1. Add the JitPack repository to your build file
 Add it in your root build.gradle at the end of repositories:
 ```
   allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
  ```
###  Step 2. Add the dependency
```
dependencies {
		compile 'com.github.User:Repo:Tag'
	}
```

## 使用方法

```
   /**
     * @param uri    从相册或相机获取到的图片
     */
    public void compressImage(Uri uri) {
        Log.e("===compressImage===", "====开始====uri==" + uri.getPath());
        try {
            //图片临时存储路径
            File saveFile = new File(getExternalCacheDir(), "终极压缩.jpg");
            Bitmap bitmap = MediaStore.Images.Media.getBitmap(getContentResolver(), uri);
            Log.e("===compressImage===", "====开始==压缩==saveFile==" + saveFile.getAbsolutePath());
            //执行压缩方法
            NativeUtil.compressBitmap(bitmap, saveFile.getAbsolutePath());     
        } catch (IOException e) {
            e.printStackTrace();
        }

    }
```
