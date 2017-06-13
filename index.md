# Section guide
### - Tasker - Automatic 2G/4G switching based on Wi-Fi connectivity [ROOT REQUIRED] 
### - Kernel - Various tweaks 
[TaskerLink](#Tasker - Automatic 2G/4G switching based on Wi-Fi connectivity [ROOT REQUIRED])

## Tasker - Automatic 2G/4G switching based on Wi-Fi connectivity [ROOT REQUIRED]
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

