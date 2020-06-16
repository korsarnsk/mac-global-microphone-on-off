# mac-global-microphone-on-off
MacOSX Automator script to mute / unmute master microphone globally for whole system.

## Use-case
In isolation we have lots of voice calls, and we need often put our microphone on Mute and back Unmute it.
It's a pain to look for the mute/unmute button to click it.

## Solution
So, the solution is to configure Hotkey to manage the case globally, i.e. independent on an application you use for communications.

Here is a good how-to article on Medium (https://medium.com/macoclock/how-in-the-bleep-do-i-mute-my-mic-anywhere-on-macos-d2fa1185b13) how to configure such script. 
But the script has an issue with the microphone status transparency, that's why I changed the script, which does the job. So, you should read the article and follow all the steps, but use script below:

```
 on getMicrophoneVolume()
   input volume of (get volume settings)
 end getMicrophoneVolume
 on disableMicrophone()
   set volume input volume 0
   display notification "Master microphone is on MUTE" with title "Global microphone settings" subtitle "OFF" sound name "Frog"
 end disableMicrophone
 on enableMicrophone()
   set volume input volume 100
   display notification "Master microphone is on UNmute" with title "Global microphone settings" subtitle "ON" sound name "Frog"
 end enableMicrophone
 
 if getMicrophoneVolume() is greater than 0 then
   disableMicrophone()
 else
   enableMicrophone()
 end if
```
