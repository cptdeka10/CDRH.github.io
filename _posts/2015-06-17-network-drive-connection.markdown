---
layout: post
title: "Network Drive Connection Problems (and Solution)"
date: 2015-06-17 09:51
categories: nebnews network smb
author: Jessica Dussault
redirect_to: http://cdrhdev.unl.edu/log/2015/network-drive-connection-problems/
---

We recently finished work on making the [Nebraska Newspapers](http://nebnewspapers.unl.edu/) version of the [Chronicling America](http://chroniclingamerica.loc.gov/) project, which involved moving around lots of really, really large files like tiffs.  I got off to a rocky start because my computer was having trouble connecting to the network drives which host those files.  I'm putting a description of my [problem](#problem) below, as well as the [solution](#solution) I came up with in the hopes that it may help someone else.  The below is my attempt to mount a Windows network drive to my Mac (OS X - Yosemite).

### <a name="problem"></a>The Problem

Alrighty, so the first step to connecting to a network drive, on a mac running Yosemite, is to click Go > Connect to Server.  Well....shoot.

![A volume on the server "libsvr12" failed to mount. There was an error mounting a volume]({{ site.url }}assets/2015-06-17/2_mount_fail.jpg)

It says "A volume on the server failed to mount."  Yet, when I look in the filesystem via the GUI I can see that they have appeared.  I should note that this is not always the case, sometimes they really, truly, failed to mount.

![Screenshot of the volumes appearing in the GUI window]({{ site.url }}assets/2015-06-17/3_wait_but.jpg)

If I'm feeling lucky, I will try opening one.  I've been burned a few times at this step, and I am beginning to firmly believe that gingerly clicking on one of the volumes rather than confidently swaggering in is more likely to be successful.  Otherwise, the share will sense my cockiness and promptly disconnect me.  Today is a good day:

![Screenshot of volume displaying its contents through the GUI]({{ site.url }}assets/2015-06-17/4_careful_selection.jpg)

Things could be worse.  The network drives are probably accessible 50% of the time and since I am pretty eager to get to work, I decide to accept that prayer is a good enough solution rather than looking for a permanent fix.  Just gonna open the terminal and start working with the files and -- well.

![Image of the terminal's "ls" command showing the volumes as being "invalid arguments"]({{ site.url }}assets/2015-06-17/5_terminal_reports.jpg)

I made a big mistake by changing windows.  The network drives, having deigned to show up at the connection party, do not like being ignored.  Clicking back to them, I find that they have disconnected.  Through trial and error I have found that the volumes dislike being ignored regardless of whether or not I have interacted with them in the terminal.  No problem, I'll just start over and reconnect...

![Image in which suddenly the server says "connection failed"]({{ site.url }}assets/2015-06-17/6_clicked_away.jpg)

Or maybe not.  "There was a problem connecting to the server...Check the server name or IP address, and then try again."

![Image: There was a problem connecting to the server...check the server name or IP address, and then try again. If you continue to have problems, contact your system administrator.]({{ site.url }}assets/2015-06-17/7_sometimes_error.jpg)

Frustratingly, I could not simply unmount the drives via the command line with the "umount" command.  It was time to go research network drives.  :(

### <a name="solution"></a>The Solution

Previous to this experience, I knew nothing about SMB or Windows sharing, etc.  I did some reading about the [SMB](http://en.wikipedia.org/wiki/Server_Message_Block) "Server Message Block" protocol.  To my dismay, I found that not all of the Samba tools are available for Mac, which has switched to using some of its own SMB utilities.  It seems simple now, but it took me more than a try or two to connect to the network drives when I was looking at examples on the internet.

If you want to see all the volumes associated with a particular network drive:

```
smbutil view //libsvr12
```

List all drives currently mounted:

```
mount -t smbfs
```

Mount a drive!  Many examples on the internet listed a password as part of the command, but when I tried that I was unable to connect.  The below command will simply prompt you for the password (which is 10x better, anyway).

{% highlight bash %}
mkdir /Volumes/rosewater3
mount -t smbfs //jdussault@servername/Rosewater3 /Volumes/rosewater3
# mount -t smbfs //username@server/volume /mount/path
{% endhighlight %}

Unmount the drives.  Although I had not been about to use "umount" above, I found that with the -t for "vfstype" I was able to unmount the volumes, including the ones that said claimed they were not really there.

```
umount -t smbfs /mount/path
```

I've been mounting and unmounting the volumes this way for a few weeks and it seems to help, at least when the volumes get "stuck" in that halfway they're-mounted-but-don't-exist kind of state.
