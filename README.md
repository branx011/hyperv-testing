# hyperv-testing Tool

    My testing tool for the hyperv drivers in the linux kernel,
    you'll need to make sure to compile your kernel using
    menuconfig to enable HYPERV_TESTING. NOTE* this is only available in
    kernel versions (5.5) and up. However I have added my original patch in this
    repository, should you not be on 5.5. Simply apply it and then you should
    be able to use the python tool after recompiling your kernel.
<div> 
<h3 style="font-family: monospace;"> Accepted patches in Mainline Kernel </h3>
</div>
<div>
    <p> <a href ="https://git.kernel.org/pub/scm/linux/kernel/git/hyperv/linux.git/commit/?h=hyperv-next&id=c48d8b04893afe35fd6f5ccbf339493bba277d43
"> Python Tool </a></p>
    <p> <a href ="https://git.kernel.org/pub/scm/linux/kernel/git/hyperv/linux.git/commit/?h=hyperv-next&id=af9ca6f9bb16e446a44393a797d0ae74d356a5c7"> Tap Mechanism </a></p> 
</div>

<h2> usage:  </h2>

    vmbus_testing delay [-e|-E] -t [value] [value] [-p] <debugfs-path>
    vmbus_testing [disable_single | d] -p <debugfs-path>
    vmbus_testing [disable_all    | D]  
    vmbus_testing [view_all       | V]
    vmbus_testing [view_single    | v] -p <debugfs-path>
    vmbus_testing --version  
  
<h3> positional arguments: </h3>  
  
    ddelay                 Delay the ring buffer interrupt or the ring buffer
                           message reads in microseconds.
    disable_all    (D)     Disable ALL testing on ALL vmbus devices.
    disable_single (d)     Disable ALL testing on a SINGLE vmbus device.
    view_all       (V)     View the test state for ALL vmbus devices.
    view_single    (v)     View the test values for a SINGLE vmbus device. 
  
<h4> optional arguments: </h4>  
  
    -h, --help             show this help message and exit
  
    --version              show program's version number and exit  
  
    -q, --quiet            silence none important test messages

<h4> optional arguments: Shared by test methods </h4> 
  
     -h, --help            show this help message and exit
     -E, --enable_all      Enable the specified test type on ALL vmbus devices.
     -e, --enable_single   Enable the specified test type on a SINGLE vmbus
                           device.
     -p, --path            Debugfs path to a vmbus device. The path must be the
                           absolute path to the device. **This option will also
                           be available to arguments postfixed with _single**
                           
<h4> optional arguments: 'delay' specific arguments </h4> 
     
      -t  , --delay_time   Set [buffer] & [message] delay time. Value
                           constraints: -1 == value or 0 < value <= 1000. Use -1
                           to keep the previous value for that delay type, or a
                           value > 0 <= 1000 to change the delay time.
