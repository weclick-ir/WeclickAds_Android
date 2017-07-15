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
  پروژه خود قراخوانی کنید:
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
</div>


