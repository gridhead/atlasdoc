# Enabling the Performance CPU Governor on System Boot

The set CPU governor are likely to be resetted back on boot. The following steps would ensure that the settings you decide, would stay put across system restarts.

1.  Navigate to   
    ``` bash
    /usr/local/bin/
    ```
2.  Create a shell script file named `perf-prof.sh` here with the following content.  
    ``` bash
    #!/bin/bash
    
    echo performance | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    ```
3.  Make the script executable by running the following command
    ``` bash
    sudo chmod 744 /usr/local/bin/perf-prof.sh
    ```
4.  Navigate to
    ``` bash
    /etc/systemd/system/
    ```
5.  Create a systemd service file named `perf-prof.service` here with the following content.
    ``` bash
    [Unit]
    After=network.target
    
    [Service]
    ExecStart=/usr/local/bin/perf-prof.sh
    
    [Install]
    WantedBy=default.target
    ```
6.  Set permissions for the systemd service file by running the following command.
    ``` bash
    sudo chmod 664 /etc/systemd/system/perf-prof.service
    ```
7.  Reload the systemd daemon by running the following command.
    ``` bash
    sudo systemctl daemon-reload
    ```
8.  Enable the service which you just created
    ``` bash
    sudo systemctl enable perf-prof.service
    ```
9.  Start the service
    ``` bash
    sudo systemctl start perf-prof.service
    ```
10. Check your current CPU governor - if it is `performance`, you were successfully able to set up the script.
    ``` bash
    cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
    ```

You can use the similar instructions for switching up to any CPU governor of your liking on boot. Just switch the CPU governor name in the shellscript file mentioned in step #2.

---

This is a draft writeup for a candidate entry in Quick Docs - an issue for which you can find [here](https://pagure.io/fedora-docs/quick-docs/issue/292), awaiting triage.