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
 
 <p>
 ابتدا خط زیر را در فایل 
 <code>build.gradle</code>
 در سطح پروژه خود اضافه کنید:
 </p>
 
<code dir="ltr">
<pre>
allprojects {
    repositories {
        maven { url 'https://weclick.ir/repo' }
        //...
    }
 }
 </pre>
 </code>
 
 <p>
 سپس در فایل 
 <code>build.gradle</code>
 سطح ماژول خود مخزن را معرفی کنید:
 </p>
 
<pre dir="ltr">
<code>
dependencies {
    compile 'ir.weclick:[VERSION_CODE]'
    //...
}
</code>
</pre>
 
</div>
