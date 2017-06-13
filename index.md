# Section guide
### - [Tasker - Automatic 2G/4G switching based on Wi-Fi connectivity (ROOT REQUIRED)](#Tasker2G)
### - [Kernel - Various tweaks](#kernelmisc)
### - [microG GmsCore - lightweight free software clone of Google Play Services](#microg)


## <a name="Tasker2G"></a> Tasker - Auto 2G/4G 
I had some serious battery drain when I had no 4G signal in my flat; using 2G helped a lot. I could still receive calls, and I had data from my Wifi.

Note: you will need these apps to use as Plugins in Tasker:
- [Cygergy's Toggle Network Type](https://forum.xda-developers.com/android/apps-games/widget-toggle-network-type-5-0-xda-t2945406)
- [Cygergy's Toggle Data](https://forum.xda-developers.com/android/apps-games/app-toggle-data-5-0-widget-to-toggle-t2937936)


Here is a [link to the Tasker profile]()

If you want to create the profile manually, here's how you can do this:

Tasker State:
```markdown
Wifi Connected
   ```
Tasker Task: "2G & No data" 
```markdown
   - Use the Plugin [Cygery's Toggle Network Type] and select "GSM only" in configuration
   OR
   - ! I want to know how to do this with Shell code (run as root)
    
    
   - Use the Plugin Cygery's Toggle Data and select "Switch off" in configuration
   OR
   - Use "Shell" code:
     setenforce permissive; svc data disable; setenforce enforcing
   ```
   
   
Tasker Exit-task (press and hold the task on the Profile screen -> add exit task): 
```markdown
   - Use the Plugin Cygery's Toggle Network Type and select "LTE, GSM/WCDMMA" in configuration
   OR
   - ! Want to know how to do this with Shell code (run as root)


   - Use the Plugin Cygery's Toggle Data and select "Switch on" in configuration
   OR
   - Use "Shell" code:
     setenforce permissive; svc data enable; setenforce enforcing
   ```



## <a name="kernelmisc"></a> Kernel tweaks 

I'm using stock kernel (no custom kernels released yet)

I'm using [ElementalX Kernel Manager (EX Kernel Manager)](https://play.google.com/store/apps/details?id=flar2.exkernelmanager&hl=en_GB)
[Kernel Adiutor Mod](https://forum.xda-developers.com/android/apps-games/kernel-adiutor-mod-singularity-kernel-t3333549) is free and pretty good. Hasn't been update for ~1 year though, so I'm not sure if anything important isn't up-to-date
Note: Make sure for the following settings the power symbol on the right is blue (apply on boot)
CPU interactive govenor, BUT with 
Glassfish 1.2 interactive governor profile (link) - there's a guide on the linked post.
Note: without a custom kernel, TouchBoost cannot be disabled - won't get full energy savings

Max CPU frequency 1689MHz
Min CPU frequency 652 MHz (can custom kernels make this even lower? [Bacon's Lighting Kernel](https://forum.xda-developers.com/oneplus-one/development/lightning-kernel-omni-rom-v01-t3245895) went down to 268MHz
- Don't notice a slowdown compared to 2016 MHz



CPUs 4 & 5 disabled
background: [SD625 has 8x A53 cores on 14nm fabrication process](https://www.qualcomm.com/products/snapdragon/processors/625)
                      cores 0-3 are "small" 
                      cores 4-7 are "big" (they're just different labels for the same thing)

- I'm a light user (few games, not graphically/computationally demanding)
- Don't notice a slowdown compared to all 8 cores being enabled 
- Disabling all 4 "big cores" gave lags when extra power was needed
- Will try disabling cores 4, 5, & 6
- Keeping cores 0-3 active seems important, might try disabling 1 (they seem to be "always active", whilst cores 4-7 become active under heavy loads)
- Governor seems to be giving too much of a boost to the "big" cores, hence disabling some "big cores"


wq_power_saving enabled (no idea what it is, couldn't find info about it.... sounds good though)


GPU
Max GPU frequency 320MHz 
Min GPU frequency 133MHz 
GPU initial frequency 133MHz 




Note: 
27 hours standby, 3h15m SoT, 73% battery (95% of the time signal is dark green, very strong). Very little wakelock bars shown when screen is not on

Wakelocks
1h from WeChat (462 counts) and Messenger (227 counts) EACH!





## <a name="microG"></a> Google Play Services open-source replacement, MicroG












### Markdown

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text
```

