# Improving GNOME Performance Using CPU Governors

<p align="justify">GNOME can be slow and laggy at times. With the onset of Wayland though, the problem has more than resolved for folks but even then, if the problem seems to have stayed back for you - the following tips might help you fix it to have an overall faster GNOME performance with smoother animations.</p>

1.  **Before getting into modifying it, what is a CPU governor?**  
    <p align="justify">A CPU governor decides how the CPU raises and lowers its clock speed in response to the demands the applications place on the system. They can help in striking a balance between performance and battery efficiency or to be inclined towards either.</p>

1.  **How do you check the list of available governors for your CPU?**  
    Simply execute the following command,  
    ``` bash
    cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
    ```
    This should list the available governors for your CPU -that you can choose from. 
    Following is an example output.  
    ![](pics/blog/cpunb/cpunbpc0.png)  

2.  **How do I know which governor is currently active on my CPU, should I have more than one of them?**  
    Simply execute the following command,
    ``` bash
    cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
    ```
    This should display the governor that is currently enabled on your CPU.  
    Following is an example output.  
    ![](pics/blog/cpunb/cpunbpc1.png) 

3.  **How do I increase make the CPU perform better using the governor?**  
    Simply execute the following command,  
    ``` bash
    echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    ```
    Following is an example output.  
    ![](pics/blog/cpunb/cpunbpc2.png)  
    This sets all the cores to work on the performance governor and the CPU cycles would have an affinity towards higher clock limit.
    * **Advantages**
        - GNOME would now perform significantly faster and the animations would be smoother. 
        - You would notice less artifacts on the GNOME panel and other applets that you use.
    * **Disadvantages**
        - The device is likely to slightly heat up due to active CPU usage and fans would be rolling.
        - There would be a slight impact on battery life if the CPU constantly stays on this governor.

4.  **How do I make the battery life better using the governor?**  
    Simply execute the following command,  
    ``` bash
    echo powersave | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    ```
    Following is an example output.  
    ![](pics/blog/cpunb/cpunbpc3.png)  
    This sets all the cores to work on the powersave governor and the CPU cycles would have an affinity towards lower clock limit.
    * **Advantages**
        - The device is likely to stay cooler due to minimal CPU load and fans would not be used.
        - The battery life would stay the same for a long time if the CPU constantly stays on this governor.
    * **Disadvantages**
        - GNOME's performance would be adversely affected and animations would be choppier.
        - You would notice more artifacts on the GNOME panel and other applets that you use.

5.  **What other CPU governors are likely to be available on my CPU?**  
    <p align="justify">The command specified in point #1 would list the available governors for your CPU but allow me to explain what each does so that you can pick the right one as per your requirement.</p>
    * <p align="justify">**`conservative`** - This makes the CPU stick to the lowest possible clock speed as much as possible but would raise it promptly, once a larger and more persistent load is placed on the CPU. This can strike a good balance between battery life and performance - being slightly more inclined towards battery life.</p>
    * <p align="justify">**`userspace`** - This allows any program to be executed by the user to decide what CPU's operating clock speed should be.  The best example is when there is a performance profile application installed by the users which needs elevated privileges to control how the CPU clock speeds scale.</p>
    * <p align="justify">**`powersave`** - This makes the CPU stick to the lower clock speed limit, thus saving a huge chunk of battery level and improving battery life but adversely affecting the performance as a result - so every applications would execute significantly slower and animations would be choppier.</p>
    * <p align="justify">**`ondemand`** - This makes the CPU boost to higher clock speeds, once a large load is placed on the CPU and slowly reduces the clock speeds once the load is removed. This can strike a good balance between battery life and performance - being slightly more inclined towards performance.</p>
    * <p align="justify">**`performance`** - This makes the CPU stick to the higher clock speed limit, thus increasing the performance significantly and making the animations smooth, however ends up adversely affecting the thermal performance, battery level as well as battery life (in a long run).</p>

---

This is a draft writeup for a candidate entry in Quick Docs - an issue for which you can find [here](https://pagure.io/fedora-docs/quick-docs/issue/292), awaiting triage.