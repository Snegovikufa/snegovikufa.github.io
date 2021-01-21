+++
title = "Rider cannot launch xamarin ios app from Windows 10"
date = 2021-01-21T16:22:15+05:00
author = "Rustam Safin"
cover = "img/mac_agent_devices_grayed_out.png"
tags = ["xamarin", "rider", "jetbrains", "development"]
description = "JetBrains Rider grays my iOS devices list. In Visual Studio I can launch applications with no errors."
showFullContent = false
+++

Can't run Xamarin iOS application from Rider?
=============================================

JetBrains Rider grays my iOS devices list:

![](/img/mac_agent_devices_grayed_out.png)

That means that Rider has got Info.plist not from your repository, but from somewhere else.

As for me it was file

`%localappdata%\XamarinBuildDownloadCache\GSgnI-5.0.2\Resources\GoogleSignIn.bundle\Info.plist`

The same path for Mac environtment:

`~/Library/Caches/XamarinBuildDownload/GSgnI-5.0.2/Resources/Info.plist`

Open file in your text editor and write UIDeviceFamily array exactly as it written within your repository's `Info.plist`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    ...
    ...
    ...
    <key>UIDeviceFamily</key>
    <array>
        <integer>1</integer>
        <integer>2</integer>
    </array>
</dict>
</plist>
```