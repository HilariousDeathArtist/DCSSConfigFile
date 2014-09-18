DCSSConfigFile
==============

This is the Dungeon Crawl Stone Soup config file used by HilariousDeathArtist. I usually play on http://crawl.s-z.org/

It's still being updated regularly, and since it's started getting spread around I thought it would be good to put up on Github.

Warning: including the rc file with the following instructions may get you nothing or even previous versions of the files if you are not playing on CSZO (trunk or .15)

There are a few ways to use this in your own game, the simplest being to add the following line to your config:

    include += HilariousDeathArtist.rc

This will ensure you get updates regularly without having to check back.

The other option is to make a branch and then copy and paste the whole thing (including any changes you want) into your config file.

I recommend reading through HilariousDeathArtist.txt at least once, and trying to get an understanding of the various sections.

You can include individual features by including specific files:

    # For just the damage announcements
    include += HDamage.rc

    # For just the ===HDAtravel autotravel replacement macro
    include += HDAtravel.rc

    # For just the monster warning messages
    include += SpoilerAlerts.rc

    # For both the Message colors and Item colors
    include += HDAColors.rc
    # For just the Message colors
    include += HDAMessageColors.rc
    # For just the Item colors
    include += HDAItemColors.rc

    # For just the Force More prompts
    include += HDAForceMore.rc

Here is a basic summary of the features:

## SpoilerAlert
Adds a function which writes various warning messages based on which enemies are on screen.
* This works by matching a string with the name of each monster and printing its warning message.
* Features various color levels based on amount of enemies and shortens the message for very large numbers of enemies.

## AnnounceDamage
Adds a function which writes a message at the end of turn announcing changes in how much health and magic you have.
* Features various color levels based on amount of current hp/mp and whether you gain or lose health.
* Currently doesn't alert when you gain 1 hp or mp to reduce span

## HDAtravel
Adds a function called HDAtravel which is intended as a replacement for autoexplore
* You must create a macro with the command '===HDAtravel' to use this feature
* Rests up to at least 75% hp (or missing at least 30hp) and 50% mp (or missing at least 20mp)
* Travels to the nearest corpse if we have no chunks and are at Very Hungry or Hungry or using Gourmand and not Engorged
* Automatically chops valid corpses if we are standing on them and we have no chunks
** This still has issues with poisonous corpses, you must either chop or pray them away
* Will stop autotravel at Near Starving, forcing player interaction before Starving.
* Prompt comes up for you to eat a ration at Near Starving/Starving
* Will cast regen if you are missing more than 10hp and have spare chunks
* Will autowield chunks and cast sublimation of blood if are missing more than 5mp
* Will autowield staff of energy and channel if missing more than 5mp and have spare chunks
* Will channel mp with Sif if missing more than 5mp and have spare chunks
* Will switch back to main weapon if wielding chunks or staff of energy
* Will use Animate Skeleton instead of chopping when appropriate, or when already standing on a skeleton

## Auto Fight
Features include throwing items, and stopping autofight at 60% health

## Auto Pickup
Currently overly greedy and includes many items
* Useful features include autopickup secondary armour when you have none, autopickup artifacts
* Experimental feature to autopickup weapons based on your skills

## Spell Slots
Defines which letters to assign spells to when memorizing

## Auto Exclude
Adds an exclusion to dangerous monsters and uniques when you happen upon them unaware

## Autotravel
Stops for most dungeon features and ego items
* Will autopickup and continue travel for items/consumables you already have
* Autotravel will automatically sacrifice items to gods when its possible
* Autotravel will automatically eat chunks when you are hungry
* Autotravel will ignore a couple of minor messages
* Autotravel will stop for a few bad situations and spell expiration warnings

## Force Prompts
Forces you to hit enter when any of a huge number of messages occur.
* This works with the mob warnings function, and currently includes a force-more when you see a monster than can cast torment
* Prompts for dungeon features, translocations, enemy consumable use, various bad/unexpected situations, hell effects, and a few others.
* Prompts when dangerous or unique monsters come into view or use very dangerous abilities

## Interface
Changes include easy butchering, hp/mp text coloring, smaller force-more messages, opens skill menu on turn 1, and changes the turn display to player turns

## Message coloring
A huge overhaul of message text colors based on message contents

#### Standard colors that I've attempted to be used for various situations:
    $danger        = lightred       - For messages you should most likely pay attention to
    $item_dmg      = red            - For messages about health or item destruction, or other very bad things
    $warning       = yellow         - For messages you should probably pay attention to, includes when stuff makes noise
    $boring        = darkgrey       - For messages you probably don't need to pay attention to
    $negative      = brown          - For messages that describe damage to you or an ally
    $good          = lightblue      - For messages that describe you or an ally doing damage to an enemy
    $positive      = green          - For messages that describe a beneficial effect that doesn't do damage
    $verypositive  = lightgreen     - For messages that describe when something dies or something good occurs
    $awesome       = lightmagenta   - For messages that describe gaining good mutations
    $interface     = cyan           - For messages that describe something to the player
    $takesaction   = blue           - For messages that describe when either you or an enemy attacks/casts
    $godaction     = magenta        - For messages relating to Gods
    MUTED  - Default HP/MP restored messages replaced with function, monster health notifications, and a few minor messages.

## Item coloring
An attempt at bringing some meaning from the above colors into the item menus

## Autoinscriptions
Inscribes useful items with messages to stop you from dropping them and reminding what they do.
* Autoinscribe fruit with a prompt when you worship Fedhas.

## Character dump
Adds a few tables to the end of the dump, adds more of your previous messages, and adds some notes to the dump.