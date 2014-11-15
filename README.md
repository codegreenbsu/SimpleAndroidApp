SimpleAndroidApp
================

Just our "hello world" app to start creating Android Applications for our project.

There is an issue with Android Studio 21 where it REALLY wants to use Java SDK 7.
These are the steps to install is and (optionally) remove the Java SDK 1.6 that Apple 
Forces you to use:

- [Install the Java SDK 7 from Oracle](Install the Java 1.7.0_71 JDK from Oracle.
See: http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html)

NOTE:  the Java .jdk file will be in the /Library/Java/JavaVirtualMachines directory now
instead of the /System/Library/Java/JavaVirtualMachines/ directory. 
Just copy them over to the /System/...

<pre><code>
sudo cp -r /Library/Java/JavaVirtualMachines/* /System/Library/Java/JavaVirtualMachines/
</code><pre>

You may be able to stop here and point Android Studio's SDK path to:

/System/Library/Java/JavaVirtualMachines/sdk1.7.0_71.sdk/...

If that doesn't work, this worked for me before adding the above path to the Android Studio SDK path:

- REMOVE Java 1.6 - Apple forces you to use it and will blow away any updates you try to install if it detects 1.6 at all

<pre><code>
sudo rm -rf /System/Library/Java/JavaVirtualMachines/
sudo rm /private/var/db/receipts/com.apple.pkg.JavaForMacOSX*
</code><pre>
Now open the InstallHistory.plist file and remove any lines that match the search for "java"

<pre><code>
sudo vi /Library/Receipts/InstallHistory.plist
</code></pre>

Then:

<pre><code>
sudo rm /usr/bin/java
sudo ln -s /Library/Java/JavaVirtualMachines/jdk1.7.0_71.jdk/Contents/Home/bin/java /usr/bin/java java -version
</code></pre>

It should output:
<pre><code>
java version "1.7.0_71"
Java(TM) SE Runtime Environment (build 1.7.0_71-b14)
Java HotSpot(TM) 64-Bit Server VM (build 24.71-b01, mixed mode)
</code><pre>

Now set your JAVA_HOME
<pre><code>
sudo rm /Library/Java/Home
sudo ln -s /Library/Java/JavaVirtualMachines/jdk1.7.0_71.jdk/Contents/Home /Library/Java/Home
</code></pre>

You will now be using Java SDK 7 instead of 6
