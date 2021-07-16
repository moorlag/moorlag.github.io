---
title: "Let's automate the F* out of G Suite with GAM and Bulk operations"
date: "2018-01-03"
categories: 
  - "computer-science"
  - "inspiration"
  - "learning"
coverImage: "arthur-osipyan-455426.jpg"
---

# Yes, this is a long overdue update G Suite.

Yesterday I was called by the lovely people of Google. I started transferring a Google Apps for business /G Suite installation from one URL to a different URL and I got stuck. Glenn from the support desk saw that I left an installation not finished and reached out to me. And what a great service I got. There was a small problem with the MX records in the Direct Admin panel. How I hate the Direct Admin / MX/DNS records is an entirely different blog... but it's working.

Long story short, the backend of my domain is now run on Google Apps. It's so convenient and easy to work with. After finishing the transfer I needed to find a way to remove a lot of mock users from a previous project. The solution was GAM (short for Google Administration?). A command prompt interface (no GUI!) to edit an entire domain. It's scary at first, but very easy to learn. The startup guide on Github is easy to follow and I've had my GAM running in no time. Let's automate the F\* out of G Suite ?. Que Bulk operations

## Tips for easy but complex Bulk operations.

Doing a lot with little .... use batch files!

- Use a spreadsheet
- Compiling a long list of changing data? Use the fill tool!
- Combine different items with " = A1 & " " & B1
- The " " is for the space between two different commands
- Copy the list with combined commands in a txt-file and
- With GAM batch <filename> you can execute the magic

![G suite profile picture](images/hipster-150x150.png)

Icons made by [Smashicons](https://www.flaticon.com/authors/smashicons "Smashicons") from [www.flaticon.com](https://www.flaticon.com/ "Flaticon") is licensed by [CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/ "Creative Commons BY 3.0")

### To do list

The following items are done or still in progress.

- Remove old user accounts (DONE)
- Adding all services for Google (DONE)
- Adding [Google Home](https://support.google.com/googlehome/answer/7571892?co=GENIE.Platform%3DAndroid&hl=en) (NOT DONE)
- Enjoying the ' I did it all myself'-feeling (partially DONE).

UPDATE: Yes, I am in love ❤️with [GAM](https://github.com/jay0lee/GAM). Automatic update every Google Profile picture (the icon on the right) with this command; gam user wordpress update photo hipster.png.The hipster.png is courtesy of Smashicons. GAM is also very friendly with batch commands. With the batch commands, I have a different email account for every different service (facebook@, xbox@, ect).

![GAM Command prompt G suite](images/Downloads_—_-bash_—_80×24-300x140.png)

What is Google Apps / G Suite? This mysterious video says it all. This is how it could be. **When your apps begin with a G.**

<iframe src="https://www.youtube.com/embed/EZmXEFGFeNA" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
