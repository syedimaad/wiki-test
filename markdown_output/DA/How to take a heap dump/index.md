**Summary:** Heap dump (.hprof file) can be used to analyze OOMs,
looking for leaks and large objects.

note

Prerequisites:

- android device connected to laptop with usb debugging enabled

- debuggable build installed on the device.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
Prerequisites:

- android device connected to laptop with usb debugging enabled

- debuggable build installed on the device.
:::
::::

**Follow these steps to extract heap dump**

1.  make sure device is connected

    adb devices

2.  find out the process id for the app (**21621** in the below)

    adb shell ps \| grep \"com.eterno\"

3.  use that process id in the dumpheap command

    adb shell am dumpheap 21621 /data/local/tmp/dump1.hprof

<!-- -->

4.  pull the file from the device

    adb pull /data/local/tmp/dump1.hprof Desktop
