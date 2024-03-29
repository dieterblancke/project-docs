# FAQ / Common Issues

# Using unicode causes weird characters to occur

In this case, you are most likely running your server on a Windows Machine.

However, there is a simple way to fix this:
1. Shutdown your BungeeCord server
1. Open your start script
1. Add -Dfile.encoding=UTF-8 in front of -jar
1. Start your BungeeCord server, all should be working fine now.

For MultiCraft, you should locate the .jar.conf file of your BungeeCord, and edit the command field with the same steps as mentioned above.
# I am getting a SSL warning

If the warning is similar to the one below, then open the main configuration file. Under storage, set useSSL to false.

```
Establishing SSL connection without server's identity verification is not recommended.
According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set.
For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'.
You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.
```

# I'm getting an error on startup
If you're getting an error on startup, just contact didjee2 on Spigot, MC-Market or Discord for help.

If the error contains the following:
`Caused by: java.lang.NoSuchMethodError: com.zaxxer.hikari.HikariConfig.setInitializationFailTimeout(J)V`

Then make sure to check for other plugins that use MySQL (specifically HikariCP) as their Hikari might be outdated.

# When I use one bold color code, the entire message becomes bold
This is a "bug" ever since BungeeUtilisalsX v2.3.5, although this is intended behaviour.

To avoid / fix this, please use the MiniMessage syntax for bold messages, or use the 'reset' color code when you want the bold text to stop.

For example:
```
This is &lsome bold text &rand this is some normal text.
```
or:
```
This is <bold>some bold text</bold> and this is some normal text.
```

# I am using LuckPerms and I gave the user/group the permission, but it still says they don't have the permission
This could be to do with using the wrong LuckPerms command, I am not sure as to why, but in previous cases when this happened,
make sure to use the command specific for BungeeCord / Velocity (which should be either /lpb or /lpv, not /lp).