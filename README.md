# NeoLinux
Custom C# based Linux masked operating system

# How to install
## Prep work
* Install *Alpine Linux* without a graphical interface.
  - Connecting to the internet will help you greatly
* Install .NET 10.0

## Install NeoLinux
* Download "Neo_linux1.0.0" from the releases page
* Move "Neo_linux1.0.0" to a USB drive
* Download both OnnxRuntime and OnnxRuntimeGenAI
* Move the runtimes into the same USB drive
* Rename "Neo_linux1.0.0" to "Neo"
* Connect a USB drive and run the following commands:

    > su -

    > mkdir -p /usr/local/bin
    
    > mount /dev/sda1 /mnt
    
    > cp /mnt/Neo /usr/local/bin/

    > cp /mnt/Microsoft.ML.OnnxRuntime.dll /usr/local/bin/

    > cp /mnt/Microsoft.ML.OnnxRuntimeGenAI.dll /usr/local/bin/
    
    > chmod +x /usr/local/bin/Neo
    
    > mkdir /lib64 && ln -s /lib/ld-musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2
    
    > apk add --no-cache libstdc++ libgcc libgomp
    
    > ldconfig /lib /usr/lib
    
    > rm -rf /lib64
    
    > apk add --no-cache gcompat
    
    > export DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=1
    
    > echo "export DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=1" >> /etc/profile
    
    > source /etc/profile
    
    > apk add --no-cache icu-libs
    
    > sed -i 's\|tty1::.*\|tty1::once:/bin/sh -c "/usr/local/bin/Neo; /sbin/poweroff"\|g' /etc/inittab


* Make sure to copy over the OnnxRuntime files into the same directory as Neo. 

  *ChronosEngine files will be added soon*

* Reboot and it should run straight into NeoOS
