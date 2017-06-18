# Section guide
### - [Tasker - Automatic 2G/4G switching based on Wi-Fi connectivity (ROOT REQUIRED)](#Tasker2G)
### - [Kernel - Various tweaks](#kernelmisc)
### - [microG GmsCore - lightweight free software clone of Google Play Services](#microg)

TODO
- Try adding [Naptime: Super Doze mode](https://play.google.com/store/apps/details?id=com.franco.doze&hl=en_GB) by Francisco Franco to my MicroG + Tasker 2G Auto setup, see if it controls the Messenger and WeChat wakelocks (~10% awake time, 1h each app in a litte over 1 day) and helps battery.
- Try and build a custom kernel with extra features (CPUs online when screen of, max screen off freq, finely tuned GlassFish1.2-styled interactive govenor profile,....)
- Implement 2G resetting when cell signal drops completely (not sure why this happens) 

## <a name="Tasker2G"></a> Tasker - Auto 2G/4G 
I had some serious battery drain when I had no 4G signal in my flat; using 2G helped a lot. I could still receive calls, and I had data from my Wifi.

Note: you will need these apps to use as Plugins in Tasker:
- [Cygergy's Toggle Network Type](https://forum.xda-developers.com/android/apps-games/widget-toggle-network-type-5-0-xda-t2945406)
- [Cygergy's Toggle Data](https://forum.xda-developers.com/android/apps-games/app-toggle-data-5-0-widget-to-toggle-t2937936)


Here is a [link to the Tasker profile](Tasker2G_4G_Auto.xml). To install it:
- Place it in "/Tasker/configs/user/"
- In Tasker, hit 3 dots at top -> Data -> Restore -> User Local Backup -> Press on filename.xml

If you want to create the profile manually, here's how you can do this:

Tasker State:
```markdown
Wifi Connected
   ```
Tasker Task: "2G & No data" 
```markdown
   - Use the Plugin [Cygery's Toggle Network Type] and select "GSM only" in configuration
   OR
   - ! Use this Shell code (run as root) :
   settings put global preferred_network_mode1 1



   - Use the Plugin Cygery's Toggle Data and select "Switch off" in configuration
   OR
   - Use "Shell" code:
     setenforce permissive; svc data disable; setenforce enforcing
   ```
   
   
Tasker Exit-task (press and hold the task on the Profile screen -> add exit task): 
```markdown
   - Use the Plugin Cygery's Toggle Network Type and select "LTE, GSM/WCDMMA" in configuration
   OR
   settings put global preferred_network_mode1 10
   

   - Use the Plugin Cygery's Toggle Data and select "Switch on" in configuration
   OR
   - Use this Shell code (run as Root
     setenforce permissive; svc data enable; setenforce enforcing
   ```

TODO:
- Make Tasker profile: When cell signal dies, launch 2G task

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





## <a name="microg"></a> Google Play Services open-source replacement, MicroG


I tried both [xiaomi.eu's MIUI](https://xiaomi.eu/community/threads/7-6-8-10.40358/) and [AEX](https://forum.xda-developers.com/redmi-note-4/xiaomi-redmi-note-4-snapdragon-roms-kernels-recoveries--other-development/rom-aospextended-rom-v3-3-t35784770)

- marginally better standby on MIUI (still about 2day total, 10h SoT)
- MIUI taking up RAM and wakelocks annoyed me (froze some with TitaniumBackup though)

- Found that [AEX has "Signature Spoofing"](https://github.com/microg/android_packages_apps_GmsCore/wiki/Signature-Spoofing), so I could try out [MicroG GMS Core (Google play services replacement)](https://github.com/microg). Didn't see much benefit from it on my OPO (bacon) a while ago, but I'm willing to try it again.

Unfortunately, Ijust moved back home where there is much better mobile signal (solid green bars on 2G)
 - so I can't say whether cell signal or MicroG seems to be doubling my standby and adding 20% more SoT

I have MicroG set do GCM (Google Cloud Messaging) every 10 minutes on Wifi. Not sure exactly what that is (pulls for every selected app, in addition to instantaneous pushes..?)

Fortunately though, it doesn't matter to me if any Google apps don't work; I'll be in China for about a year, starting August. You'll have to do some research on what works and what doesn't. [Shadow53 has some helpful files to get basic things like Contacts and Calendar working.](https://shadow53.com/no-gapps/downloads/)






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

