---
layout: post
title: Enabling Remote Desktop on Windows 7 Home Premium
date: 2010-03-25 00:00
comments: true
categories: []
---
<p>My reasoning for this post is two-fold: I wanted to get Remote Desktop enabled on my new laptop, so that I can connect remotely from my Android phone. I also wanted to enable concurrent sessions for the laptop computers at home, in the common event that my family members need assistance from me while I'm at home.</p>

<p>On the main computer/server/multimedia powerhouse at home, I had previously used Sala's Terminal Server Patch to accomplish this. But because of the architecture changes made to the Windows operating system since Windows XP, Sala's patch was not going to make the cut.</p>

<p>I recently ran across a <a href="http://thegreenbutton.com/forums/t/79427.aspx?PageIndex=1" target="_blank">forum post</a>, which makes this process so much easier. If you want, you can skip forum post and download the utility <a href="http://www.mediafire.com/file/hzz2l5mznzm/Concurrent_RDP_Win7_RTM_patcher_v1.1.zip" target="_blank">here</a>. Not only does this tool enable Remote Desktop on any version of Windows 7, it also allows for concurrent sessions.</p>

<p>Once you download and extract the utility, run the COM script as an administrator. You will be prompted with certain tweaks that you might find useful. Once the script patches the proper executables, it restarts the Remote Desktop service and voila!</p>
