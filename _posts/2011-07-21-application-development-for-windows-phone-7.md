--- 
layout: post
title: Application Development for Windows Phone 7
excerpt:
  Over the past couple of weeks, I have been working on my first Windows Phone 7 application for my new HTC Trophy on Verizon. First off, I absolutely love my Windows Phone and no, I have not been drinking too much koolaid here in Redmond. I truly think that the Windows Phone software has a great user interface and is packed with features that just make life easier, with over 500 new features coming in Mango.
---
Over the past couple of weeks, I have been working on my first <a href="http://www.microsoft.com/windowsphone/en-us/default.aspx" target="_blank">Windows Phone 7</a> application for my new <a href="http://www.htc.com/us/products/trophy-verizon?view=1-1&amp;sort=0&amp;filters=4-0-0" target="_blank">HTC Trophy</a> on <a href="http://www.verizonwireless.com/b2c/index.html" target="_blank">Verizon</a>. First off, I absolutely love my Windows Phone and no, I have not been drinking too much koolaid here in Redmond. I truly think that the Windows Phone software has a great user interface and is packed with features that just make life easier, with over <a href="http://techcrunch.com/2011/05/24/microsoft-officially-announces-windows-phone-7-1-mango-with-500-new-features/" target="_blank">500 new features</a> coming in <a href="http://www.youtube.com/watch?v=OP30F3ZxTmw" target="_blank">Mango</a>. Back to the topic at hand, Windows Phone is a fantastic platform to develop on and for developers that already use <a href="http://msdn.microsoft.com/en-us/vcsharp/aa336809" target="_blank">C#</a> and the <a href="http://www.microsoft.com/net/" target="_blank">.NET Framework</a> for their applications, <a href="http://www.silverlight.net/" target="_blank">Silverlight</a> applications for Windows Phone is a no brainer. Aside from the development aspect, actually going from code to <a href="http://www.microsoft.com/windowsphone/en-us/apps/default.aspx" target="_blank">Marketplace</a> was extremely easy. I was able to launch my application in 24 hours, without any problems.

<a href="http://mbmccormick.com/wp-content/uploads/2011/07/Screenshot1.png"><img class="size-full wp-image-131 alignright" title="Screenshot1.png" src="http://mbmccormick.com/wp-content/uploads/2011/07/Screenshot1.png" alt="" width="230" height="383" /></a>

My application, <a href="http://windowsphone.com/s?appid=2b36d281-9189-e011-986b-78e7d1fa76f8" target="_blank">LaundryMinder</a>, turns your phone into a laundry monitoring device. You simply place your device on your washer or dryer when you are doing your laundry and start the LaundryMinder application. When your laundry is done and the machine stops vibration, the application uses the phone’s <a href="http://en.wikipedia.org/wiki/Accelerometer" target="_blank">accelerometer</a> to detect this and then sends out an email, text message, or phone call to notify you. This application works for both the washer and dryer cycle and accounts for even the slightest changes in movement, to account for newer laundry machines that produce very little vibration. To keep from draining the battery, the accelerometer is only polled every 2 minutes to check for vibration. This also helps account for washing machine cycle changes when the tub is draining or filling.

<a href="http://mbmccormick.com/wp-content/uploads/2011/07/Desktop.png"><img class="alignleft size-thumbnail wp-image-133" title="Desktop.png" src="http://mbmccormick.com/wp-content/uploads/2011/07/Desktop-150x150.png" alt="" width="150" height="150" /></a>

I developed this application using C# and Silverlight on .NET Framework 4, three technologies that I am very familiar with, which made development a breeze. After installing the <a href="http://create.msdn.com/en-US/home/getting_started" target="_blank">Windows Phone SDK</a> in <a href="http://www.microsoft.com/visualstudio/en-us" target="_blank">Visual Studio 2010</a>, I was ready to begin development. In another post, I will go in depth with the code, but I will spare the details for now. Using the new SDK, I was able to run my application in an emulator that had support for the accelerometer. This allowed me to test the sensitivity of my accelerometer, without having to do 10 loads of laundry. Once I was happy with my application, I generated a clean build and uploaded this to the Marketplace.

Publishing my application to the Marketplace was really easy. After setting up my account, I created a new application where I uploaded my <a href="http://forums.asp.net/t/1277554.aspx" target="_blank">XAP file</a>, entered some version information, tags, description, screenshots, logos, etc. and I also had the option to select a price. I decided to release this application for free, so this step did not apply for me. After submitting my application for approval, I had about a 24 hour waiting period where my application was tested in an emulator and on several physical devices, someone reviewed my application and ensured that it did not violate any regulations, and alas my application was published.

You can download LaundryMinder on the Marketplace <a href="http://windowsphone.com/s?appid=2b36d281-9189-e011-986b-78e7d1fa76f8" target="_blank">here</a> and you can check out the source code for this application on GitHub <a href="https://github.com/mbmccormick/LaundryMinder" target="_blank">here</a>.