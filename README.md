# Rakcheat anticheat

This anticheat is based on [Nex-AC](https://github.com/NexiusTailer/Nex-AC) and integrates checks from [rakcheat](https://github.com/f0Re3t/rakcheat).  
All checks and protections from rakcheat have been optimized and additional methods have been added.  

**Important:** to use this you need a localization file (which can be taken from the main anticheat repository), and Pawn.RakNet is heavily utilized by the new checks, so it is highly recommended to include it as a dependency.

Below are the main differences from the original Nex-AC.

## External functions

An additional parameter "code2" has been added to OnCheatDetected. It is now declared as follows:

```pawn
forward OnCheatDetected(playerid, ip_address[], type, code, code2);
```

This parameter is identical to the one in OnCheatWarning and is intended to help identify which specific check within the anticheat code was triggered.

## Default settings

Support for most single-player mechanics has been disabled, as well as the output of statistics when the server is shut down and the reading/writing of an external configuration file. Additionally, support for NPC is disabled by default, but if you use them on your server, you can enable it (in the same way as in the base anticheat):

```pawn
#define AC_USE_NPC true
#include <rakcheat>
```

Other changes include:
* The maximum number of incoming players from a single IP address has been increased from 1 to 3.
* The maximum number of failed RCON login attempts has been increased from 1 to 3.

## Anticheat codes

A new code 53 (Anti-Fast movement) has been added. Other changes and improvements have been integrated into existing anticheat codes. All of them have a subcode (code2), which allows you to determine that a new check from rakcheat was triggered, even if it shares the same code as in the base anticheat.

If you are configuring the anticheat using the "nex-ac_settings.cfg" file, it is recommended to delete it from the "scriptfiles" folder and generate a new one, if the previous one was created by the original Nex-AC (due to changes in the number of anticheat codes).

For those who need more detailed technical information about all the added checks, what they add and how they work, use a diff checker to compare it with the base anticheat. I hope this might be useful for some.

Blasthack thread: https://www.blast.hk/threads/46756/
