# Creality CR-6 MAX custom cura profile

**PLEASE NOTE: There is no warranty or guarantee that this will work for you. I did this for educational purposes and have decided to share my experience and observations.**

So, for a long time I went with the CR6 SE profile in CURA and then re-sized the plate after selecting it. 
It works fine for the most  part. However, something kept messing up with that and it still bugged me that it "Wasn't a MAX" profile. There were instances where the settings reverted to the default CR-6 SE profile and it messed things up royally when the bed thought it was the wrong size. It worked for the most part, but OCD kept bugging me that it wasn't a "MAX" profile. 

So i looked a bit into how profiles work in Cura and figured out that Cura uses a stacked profile system where different components/dependencies are slightly modified from a referenced "default profile" so to speak. If you run through the files in "resources" where cura is installed, and check it out, its enlightening how it works.

Here are the refs I found:

- https://github.com/Ultimaker/Cura/wiki/Definition-Files-Explained
- https://github.com/Ultimaker/Cura/wiki/Adding-new-machine-profiles-to-Cura
- https://github.com/Ultimaker/Cura/wiki/Profiles-&-Settings (this ones more education than useful i think)

The "Instructions" are geared more for printer manufacturers and state to do a pull request to have profile verified and stuff before it eventually gets published in the main releases. I'm not the manufacturer and nobody ever bothered to care to make anything for the max and honestly, im not confident enough (nor do I know how to) make the contribution myself.

I figured out that these profiles "Live" in `C:\Program Files\Ultimaker Cura 5.1.0\share\cura\resources\` and in various sub-directories. However you shouldn't use this for custom files, they will get erased in any update, iirc. 
I created a custom files after looking how the CR-6 SE profile works. And after some trial and error, i found out it requires a [printer]_0.2.inst.cfg for each nozzle size needed. So i just copied the same for the CR-6 SE profile and renamed and edited it as needed. Most of the work is done as it a lot references the creality_base profile. See further down on the layout of the custom files needed.

So instead of placing my custom printer profile in the base install I found that if you place them in `C:\Users\YOURUSERNAME\AppData\Roaming\cura\5.1\` there is an equivalent structure here where your settings, profiles, plugins and other stuff are saved as well. This is where custom versions of profiles can safely be placed for use.

I created the necessary base files for the MAX which I figured out were:

- creality_cr6max.def.json (in \definitions\)
- creality_cr6max_0.2.inst.cfg
- creality_cr6max_0.3.inst.cfg
- creality_cr6max_0.4.inst.cfg
- creality_cr6max_0.5.inst.cfg
- creality_cr6max_0.6.inst.cfg
- creality_cr6max_0.8.inst.cfg
- creality_cr6max_1.0.inst.cfg
(all of these in \variants\)

The only difference between the base CR-6 SE version and mine is the bed size and some custom gstart code. That code is based on another good read: 

https://damsteen.nl/blog/2021/02/11/creality-cr6-community-firmware-start-print-without-drooping

Also I HIGHLY recommend using the community firmware. https://github.com/CR6Community/Marlin
thank you Sebazzz!

Your custom files should be placed in %appdata%\Roaming\cura\5.1\ (or whatever versions were on now). 

**PLEASE NOTE: There is no warranty or guarantee that this will work for you. I did this for educational purposes and have decided to share my experience and observations.**
