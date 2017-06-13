## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/james-clark-5/RN4-Android-7.1.2-Max-Battery/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

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

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).





## Tasker Profiles
### Automatic 2G/4G switching based on Wi-Fi connectivity
I had some serious battery drain when I had no 4G signal in my flat; using 2G helped a lot. I could still receive calls, and I had data from my Wifi.

!link to profiles

If you want to create the profile manually, here's how you can do this:

Context
```markdown
State -> Wifi Connected
   ```
Task "2G & No data" 
```markdown
   To switch your mobile data connection type to 2G, you can either:
   - Use the Plugin [Cygergy's Toggle Network Type](https://forum.xda-developers.com/android/apps-games/widget-toggle-network-type-5-0-xda-t2945406) in Tasker and select "GSM only" in configuration
   OR
    ! I want to know how to do this with Shell code (run as root)
    
   To turn your mobile data off, you can either:
   - Cygergy #link Data Switcher
   OR
   - Shell code:
     !snippet (run as root)
   ```
Exit task (press and hold the task on the Profile screen -> add exit task) 
# 4G, data on
-  BOLD 4G
    Use the Plugin [Cygergy's Toggle Network Type](https://forum.xda-developers.com/android/apps-games/widget-toggle-network-type-5-0-xda-t2945406)  in Tasker and select "LTE, GSM/WCDMMA" in configuration
   OR
   ! Want to know how to do this with Shell code (run as root)
-  BOLD Data off
   Cygergy #link Data Switcher
   OR
   Shell code !snippet (run as root)








### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/james-clark-5/RN4-Android-7.1.2-Max-Battery/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
