# Language System

To integrate your own language system with BungeeUtilisalsX Language Messages, please check [this section on our Developer Api Page](api.md#custom-language-integration)!

## What is it?
BungeeUtilisalsX is designed with configurability in mind. While it may be confusing sometimes, it allows for maximum customization for your server.
Every message that is sent by BungeeUtilisalsX is configurable in the language files, a list of languages can be set up in the languages/config.yml file.

## languages/config.yml
By default, this file is as follows:
```yaml
languages:
  en_US:
    # If default is true, this language will be default for new users, if false, users will be able to select it.
    default: true
```

To add a new language, all you need to do is add it to this config and copy paste the default en_US.yml file to your new language name, for example for Dutch:
```yaml
languages:
  en_US:
    # If default is true, this language will be default for new users, if false, users will be able to select it.
    default: true
  nl_BE:
    default: false
```

## Color support
Yes, BungeeUtilisalsX **does support** hex color codes, but only with BungeeCord versions that support 1.16 and higher. These colors can be used by using the following format:
`<#HEX_COLOR>`. For example, `<#FF0000>` will give you dark red, `<#FFFF00>` will result in yellow, `<#00FFFF>` results in light blue and so on ....

### Gradient colors
BungeeUtilisalsX also has support for "gradient colors", all the text in between two gradient colors will have the first color slowly fade into the second color.

The format for gradient colors is as follows: `<gradient:[color1]:[color...]:[phase]>text</gradient>`. For example, if we set these gradient colors on the no-permission message as follows:
```yaml
no-permission: '<gradient:FF0000:FFAE00>You do not have the permission to do this!</gradient>'
```
This will result in your no permission message be/ing displayed as follows: <br />
![](https://i.imgur.com/NXh1Fby.png)

## MiniMessage
Since BungeeUtilisalsX v2.3.5, it now uses / supports MiniMessage. Old color codes (with the & format) are still supported (BungeeUtilisalsX has a translation layer for this).

MiniMessage allows you to do amazing things with your messages, feel free to check out the [documentation over here.](https://docs.adventure.kyori.net/minimessage/format.html)

The usage of MiniMessage is being recommended, although not required, as you can see below, the old colors and Text Section systems are still available and supported throughout!

## Text section messages
A text section message is a message that allows you to create a message with multiple layer sections that can each have their own hover or click event.
These type of messages can be used in 90+ % of the messages. There are only a select few messages that do not really support it.

An example of a text section messages **with a single text section** (friend list format):
```yaml
friends:
  list:
    format:
      text: '- &b{friendName} - &7{lastOnline}'
      hover:
        - '&eOnline: &b{online}'
        - '&eFriends since: &b{friendSince}'
        - '&eLast seen: &b{lastOnline}'
      click:
        # OPEN_URL, RUN_COMMAND, SUGGEST_COMMAND
        # RUN_COMMAND will only work for BungeeCord commands.
        type: 'SUGGEST_COMMAND'
        action: '/friend msg {friendName} '
```

An example of a text section message **with multiple text sections** (friend requests header):
```yaml
friends:
  requests:
    head:
      text:
        - text: '&6<- '
          click:
            type: 'RUN_COMMAND'
            action: '/friends requests {previousPage}'
        - text: '&e{type} Requests List &b({currentPage} of {maxPages})'
        - text: ' &6->'
          click:
            type: 'RUN_COMMAND'
            action: '/friends requests {nextPage}'
```

In the second example there is a parent section "text:" which contains a list of other text sections while in the first example the "text:" section only has a string as value.
Both will work, but the second example will allow for custom hover and click events for each section you define while the first example only allows a hover and click event for the entire message.

### Text section message sounds
Each text section can also be assigned a sound that should be played when the message is built.

This is just a "sound" section on the same level as text, hover and click and is optional. For this to work, you need to have the plugin "[Protocolize](https://www.spigotmc.org/resources/protocolize-protocollib-for-bungeecord-waterfall-velocity.63778/)" installed.

A list of sounds can be found online, on sites like [these](https://www.andre601.ch/Spigot-Sounds/), just make sure to type both the sound and the category in UPPER CASE.
The following categories can be used: MASTER, MUSIC, RECORDS, WEATHER, BLOCKS, HOSTILE, NEUTRAL, PLAYERS, AMBIENT, VOICE

Sound example:
```yaml
friends:
  list:
    format:
      text: '- &b{friendName} - &7{lastOnline}'
      hover:
        - '&eOnline: &b{online}'
        - '&eFriends since: &b{friendSince}'
        - '&eLast seen: &b{lastOnline}'
      click:
        # OPEN_URL, RUN_COMMAND, SUGGEST_COMMAND
        # RUN_COMMAND will only work for BungeeCord commands.
        type: 'SUGGEST_COMMAND'
        action: '/friend msg {friendName} '
      sound:
        sound: BLOCK_NOTE_BLOCK_PLING
        category: MASTER
        volume: 20
        pitch: 1
```

Or, what also works if you want to use the master category with volume and pitch on 1:
```yaml
friends:
  list:
    format:
      text: '- &b{friendName} - &7{lastOnline}'
      hover:
        - '&eOnline: &b{online}'
        - '&eFriends since: &b{friendSince}'
        - '&eLast seen: &b{lastOnline}'
      click:
        # OPEN_URL, RUN_COMMAND, SUGGEST_COMMAND
        # RUN_COMMAND will only work for BungeeCord commands.
        type: 'SUGGEST_COMMAND'
        action: '/friend msg {friendName} '
      sound: BLOCK_NOTE_BLOCK_PLING
```
