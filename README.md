# minecraft_runner
Tools to make running a home minecraft server a little simpler

# runner

Runs one or more minecraft servers.  Full help included.  Each positional argument is the name of a section of the config file, and describes a minecraft server to run.  All servers will be announced on the LAN.

# runner.conf

Default name of the configuration file (can be overridden by options).  This is a bog-standard .ini file.

Each section defines a minecraft server.  A minimal configration would be a bare section with no options.  That will launch server.jar in $PWD/minecraft.  There are a number of valid options.

## title

The name of the minecraft server.  This will be broadcast as-is to the LAN, and used as the name of the tmux window.  Defaults to `uname -n`

## port

The port used by Minecraft.  Defaults to 25565.  Obviously this needs to be different for each defined server if you plan to run them simultaneously.

## memory

Amount of RAM to allocated to the JVM.  Uses standard JVM notation.  Defaults to 3G.

## options

Any options you desire to pass to the JVM.  Defaults to 
```
-XX:+UseG1GC -XX:+UseNUMA -XX:+AggressiveOpts -XX:+DisableExplicitGC -XX:+OptimizeStringConcat -XX:MaxGCPauseMillis=400 -XX:PermSize=256m
```
Use "" to remove them all.

## java

Full path to the java binary.  Defaults to /usr/bin/java.

## jarfile

Server jar to be launched.  Defaults to server.jar.

## directory

Directory (relative to $PWD) where the Minecraft installation lives.

## command

This is the full command to use (with or without substitutions from the above properties).  The default is in the code.  You probably shouldn't change it, and if you're going to, you better be familiar with what the code is doing with it.
