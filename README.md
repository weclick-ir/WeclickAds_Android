<div dir="rtl">

<h1>راهنمای نصب SDK وی‌کلیک</h1>

<h3>
برای استفاده از
SDK
تبلیغات ویکلیک به حساب کاربری نیاز دارید!
</h3>

<a href="http://weclick.ir">
برای ساخت حساب کاربری به سایت ویکیلیک مراجعه کنید!
</a>

<div dir="ltr">

[![Weclick!](https://weclick.ir/images/logo.png)](https://weclick.ir)

</div>

<h2>
نصب با استفاده از 
<code>build.gradle</code>
</h2>


<p>
بعد از ایجاد حساب کاربری برای نصب 
SDK 
بر روی پروژه خود باید ادرس مخزن را به فایل 
<code>build.gradle</code>
اضافه کنید!
</p>
 <ul dir="rtl">
 <li>
 <p dir="rtl">
 ابتدا خط زیر را در فایل 
 <code>build.gradle</code>
 در سطح پروژه خود اضافه کنید:
 </p>
 </li>
 </ul>
 
<pre dir="ltr" align="left" style="text-align:left">
<code>
allprojects {
    repositories {
        maven { url 'https://weclick.ir/repo' }
        //...
    }
 }
 </code>
 </pre>
 
 <ul dir="rtl">
 <li>
 <p dir="rtl">
 سپس در فایل 
 <code>build.gradle</code>
 سطح ماژول خود مخزن را معرفی کنید:
 </p>
 </li>
 </ul>
 
<pre dir="ltr">
<code>
dependencies {
    compile 'ir.weclick:[VERSION_CODE]'
    //...
}
</code>
</pre>
 
 <p>
 پس از اعمال تغیرات مجدد پروژه را بیلد کنید.
 </p>
 
 <h2>
 تنظیمات اولیه
 </h2>
 
 <p>
 پس نصب باید کلاس
 <code>
 WeclickAds
 </code>
  را بصورت زیر در کلاس
  <code>Application</code>
  پروژه خود فراخوانی کنید:
 </p>
 <div dir="ltr">
 
 ```java
 
 public class App extends Application {
    @Override
    protected void onCreate() {
        super.onCreate();
        WeclickAds.initialize(getApplicationContext(),"YOUR_CLIENT_KEY");
    }
 }
 ```
 </div>
 
 <p>
 می توانید 
 <code> CLIENT_KEY</code>
 خود را در فایل 
 <code>AndroidManifest.xml</code>
 معرفی کنید:
 </p>
 
 <p>
 درون بلوک 
 <code> &lt;application&gt; </code>
 به شکل زیر کلید خود را قرار دهید:
 </p>
 
 <div dir="ltr">
 
 ```xml
 <meta-data
    android:name="ir.weclick.CLIENT_KEY"
    android:value="PUT_CLIENT_KEY_HERE"/>
 ```
 
 
  ```java
 
 public class App extends Application {
    @Override
    protected void onCreate() {
        super.onCreate();
        WeclickAds.initialize(getApplicationContext());
    }
 }
 ```
 
</div>

<h2>
نمایش تبلیغ
</h2>

<ul>
<li>
<p>
ابتدا کامپوننت تبلیغ را به
<code>layout</code>
خود اضافه کنید!
</p>

<p>

دقت کنید درصورتی ک تبلغی برای نمایش وجود نداشته باشد یا شما از طریق پنل کاربری خود تبلیغ را غیر فعال کنید کامپوننت تبلیغ به حالت
<code>GONE</code>
می رود لذا باید ترتیب چیدمان کامپوننت های شما طوری باشد که با تغییر بهم نریزد!
</p>
</li>
</ul>

<div dir="ltr">

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/activity_test_ad"
    android:gravity="center_horizontal"
    android:layout_width="match_parent"
    android:layout_height="match_parent">


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_alignParentLeft="true"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:background="@color/colorAccent"
        android:orientation="horizontal"
        android:visibility="visible">
        
        <!--ADD YOUR OTHER VIEWS HERE-->

    </LinearLayout>


    <ir.weclick.weclickads.WeclickAdView
        android:id="@+id/weclick_ad"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:elevation="20dp"
        app:adSize="BANNER"
        app:detachable="true">
    </ir.weclick.weclickads.WeclickAdView>

</RelativeLayout>

```
</div>

<ul>
<li>
<p>
در کلاس مرتبط با 
<code>layout</code>
کامپوننت را پیدا کنید:
</p>
</li>
</ul>

<div dir="ltr">

```java
private WeclickAdView adView;

adView= (WeclickAdView) findViewById(R.id.weclick_ad);
```
</div>

<ul>
<li>
<p>
برای نمایش تبلیغ در کامپوننت ایجاد شده باید یک
<a href="#">
<code>WeclickAdRequest</code>
</a>
ایجاد نموده و به کامپوننت معرفی کنید!
</p>
</li>
</ul>

<div dir="ltr">

```java
WeclickAdRequest request=new WeclickAdRequest.Builder()
                .setAdFormat(WeclickAdFormat.BANNER)
                .setAdSize(WeclickAdSize.FULL_BANNER)
                .setAge(19)
                .setGender(1).build();

adView.setRequest(request);
```

</div>

<h2>
سایر موارد
</h2>

<ul>
<li>
<p>
دسترسی ها
<code>uses-permission</code>
</p>
</li>
</ul>

<div dir="ltr">

```xml
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
    <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
```

</div>

<p>
بجز 
<code>INTERNET</code>
و
<code>ACCESS_NETWORK_STATE</code>
باقی موارد اجباری نبوده و برای هدفمندی تبلیغ می باشد درنتیجه به بازدهی بیشتر تبلیغ کمک می کند.
</p>


</div>


