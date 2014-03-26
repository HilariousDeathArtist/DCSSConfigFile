DCSSConfigFile
==============

This is the Dungeon Crawl Stone Soup config file used by HilariousDeathArtist.

It's still being updated regularly, and since it's started getting spread around I thought it would be good to put up on Github.

There are a few ways to use this in your own game, the simplest being to add the following line to your config:
    include = HilariousDeathArtist.rc

This will ensure you get updates regularly without having to check back.

The other option is to make a branch and then copy and paste the whole thing (including any changes you want) into your config file.
I reccomend reading through the file at least once, and trying to get an understanding of the various sections.

Here is a basic summary of the features:

## SpoilerAlert
Adds a function which writes various warning messages based on which enemies are on screen.
* This works by matching a string with the name of each monster and printing its warning message.
* Features various color levels based on amount of enemies and shortens the message for very large numbers of enemies.

## AnnounceDamage
Adds a function which writes a message at the end of turn announcing changes in how much health and magic you have.
* Features various color levels based on amount of current hp/mp and whether you gain or lose health.
* Currently doesn't alert when you gain 1 hp or mp to reduce span

## Autofight 
Features include throwing items, and stopping autofight at 75% health

## Autopickup 
Currently overly greedy and includes many items
* Useful features include autopickup secondary armour when you have none, autopickup artifacts

## Spell Slots 
Defines which letters to assign spells to when memorizing

## Autoexlude 
Adds an exlusion to dangerous monsters and uniques when you happen upon them unaware

## Autotravel 
Stops for most dungeon features and ego items
* Will autopickup and continue travel for items/consumables you already have
* Autotravel will automatically sacrifce items to gods when its possible
* Autotravel will automatically eat chunks when you are hungry
* Autotravel will ignore a couple of minor messages
* Autotravel will stop for a few bad situations and spell expiration warnings

## Force Prompts 
Forces you to hit enter when any of a huge number of messages occur.
* This works with the mob warnings function, and currently includes a force-more when you see a monster than can cast torment
* Prompts for dungeon features, translocations, enemy consumable use, various bad/unexpected situations, hell effects, and a few others.
* Prompts when dangerous or unique monsters come into view or use very dangerous abilities

## Interface 
Changes include easy butchering, hp/mp text coloring, smaller force-more messages, and changes the turn display to player turns

## Message coloring 
A huge overhaul of message text colors based on message contents

#### Standard colors that I've attempted to be used for various situations:
    $danger        = lightred  - For messages you should most likely pay attention to
    $item_dmg      = red       - For messages about health or item desctuction, or other very bad things
    $warning       = yellow    - For messages you should probably pay attention to, includes when stuff makes noise
    $boring        = darkgrey  - For messages you probably don't need to pay attention to
    $negative      = brown     - For messages that describe damage to you or an ally   
    $good          = lightblue - For messages that describe you or an ally doing damage to an enemy
    $positive      = blue      - For messages that describe a benefecial effect that doesn't do damage
    $verypositive  = green     - For messages that describe when something dies or something good occurs
    $awesome       = lightgreen -For messages that describe gaining good mutations
    $interface     = cyan      - For messages that describe something to the player
    $takesaction   = lightmagenta  - For messages that describe when either you or an enemy
    $godaction     = magenta   - For messages relating to Gods
    MUTED  - Default HP/MP restored messages replaced with function, monster health notifications, and a few minor messages.

## Item coloring 
An attempt at bringing some meaning from the above colors into the item menus

## Autoinsriptions 
Insribes useful items with messages to stop you from dropping them and reminding what they do.
* Autoinsribes fruit with a prompt when you worship Fedhas.

## Character dump 
Adds a few tables to the end of the dump, adds more of your previous messages, and adds some notes to the dump.