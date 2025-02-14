# Rogue: Exploring the Dungeons of Doom

This is a fork of the classic *Rogue* game from the 1980s, implemented in C and built using the Meson build system.

## Features
- Classic dungeon-crawling gameplay
- ASCII-based user interface
- Procedurally generated dungeons
- Permadeath mechanics
- Modernized build system using Meson

## Requirements

Ensure you have the following dependencies installed:

- **C Compiler** (GCC or Clang)
- **Meson** (>= 0.60)
- **Ninja** (build tool used by Meson)
- **curses** (for terminal-based UI rendering)

## Installation & Build

Clone the repository and build the project using Meson:

```bash
git clone https://github.com/nextdorf/rogue.git
cd rogue
meson setup build
meson compile -C build
```

## Running the Game

After a successful build, run the game:

```sh
./build/rogue
```

For a detailed guide see either `rogue.html` for scroll down on this README.

## License

This project is licensed under the BSD License. See the `LICENSE.TXT` file for details.

#


# A Guide to the Dungeons of Doom

    Michael C. Toy
    Kenneth C. R. C. Arnold
    Computer Systems Research Group
    Department of Electrical Engineering and Computer Science
    University of California
    Berkeley, California 94720

###

    Rogue is a visual CRT based fantasy game which runs under the UNIX timesharing system. This paper describes how to play rogue, and gives a few hints for those who might otherwise get lost in the Dungeons of Doom.

## 1. Introduction

You have just finished your years as a student at the local fighter’s guild. After much practice and sweat you have finally completed your training and are ready to embark upon a perilous adventure. As a test of your skills, the local guildmasters have sent you into the Dungeons of Doom. Your task is to return with the Amulet of Yendor. Your reward for the completion of this task will be a full membership in the local guild. In addition, you are allowed to keep all the loot you bring back from the dungeons.

In preparation for your journey, you are given an enchanted mace, a bow, and a quiver of arrows taken from a dragon’s hoard in the far off Dark Mountains. You are also outfitted with elf-crafted armor and given enough food to reach the dungeons. You say goodbye to family and friends for what may be the last time and head up the road.

You set out on your way to the dungeons and after several days of uneventful travel, you see the ancient ruins that mark the entrance to the Dungeons of Doom. It is late at night, so you make camp at the entrance and spend the night sleeping under the open skies. In the morning you gather your weapons, put on your armor, eat what is almost your last food, and enter the dungeons.

## 2. What is going on here?

You have just begun a game of rogue. Your goal is to grab as much treasure as you can, find the Amulet of Yendor, and get out of the Dungeons of Doom alive. On the screen, a map of where you have been and what you have seen on the current dungeon level is kept. As you explore more of the level, it appears on the screen in front of you.

Rogue differs from most computer fantasy games in that it is screen oriented. Commands are all one or two keystrokes[1] and the results of your commands are displayed graphically on the screen rather than being explained in words[2].

Another major difference between rogue and other computer fantasy games is that once you have solved all the puzzles in a standard fantasy game, it has lost most of its excitement and it ceases to be fun. Rogue, on the other hand, generates a new dungeon every time you play it and even the author finds it an entertaining and exciting game.

## 3. What do all those things on the screen mean?

In order to understand what is going on in rogue you have to first get some grasp of what rogue is doing with the screen. The rogue screen is intended to replace the “You can see ...” descriptions of standard fantasy games. Figure 1 is a sample of what a rogue screen might look like.

____


                        ------------
                        |..........+
                        |..@....]..|
                        |....B.....|
                        |..........|
                        -----+------



    Level: 1  Gold: 0      Hp: 12(12)  Str: 16(16)  Arm: 4  Exp: 1/0

                          Figure 1
____

### 3.1. The bottom line

At the bottom line of the screen are a few pieces of cryptic information describing your current status. Here is an explanation of what these things mean:
 

* __Level__: This number indicates how deep you have gone in the dungeon. It starts at one and goes up as you go deeper into the dungeon.

* __Gold__: The number of gold pieces you have managed to find and keep with you so far.

* __Hp__: Your current and maximum health points. Health points indicate how much damage you can take before you die. The more you get hit in a fight, the lower they get. You can regain health points by resting. The number in parentheses is the maximum number your health points can reach.

* __Str__: Your current strength and maximum ever strength. This can be any integer less than or equal to 31, or greater than or equal to three. The higher the num- ber, the stronger you are. The number in the parentheses is the maximum strength you have attained so far this game.

* __Arm__: Your current armor protection. This number indicates how effective your armor is in stopping blows from unfriendly creatures. The higher this number is, the more effective the armor.

* __Exp__: These two numbers give your current experience level and experience points. As you do things, you gain experience points. At certain experience point totals, you gain an experience level. The more experienced you are, the better you are able to fight and to withstand magical attacks.

### 3.2. The top line

The top line of the screen is reserved for printing messages that describe things that are impossible to represent visually. If you see a “--More--” on the top line, this means that rogue wants to print another message on the screen, but it wants to make certain that you have read the one that is there first. To read the next message, just type a space.

### 3.3. The rest of the screen

The rest of the screen is the map of the level as you have explored it so far. Each symbol on the screen repre- sents something. Here is a list of what the various symbols mean:

* __@__ represents you, the adventurer.

* __-__ and __|__ represent the walls of rooms.

* __+__ is a door to/from a room.

* __.__ is the floor of a room.

* __#__ is the floor of a passage between rooms.

* __*__ is a pile or pot of gold.

* __)__ is a weapon of some sort.

* __]__ is a piece of armor.

* __!__ is a flask containing a magic potion.

* __?__ is a piece of paper, usually a magic scroll.

* __=__ is a ring with magic properties

* __/__ is a magical staff or wand

* __^__ is a trap, watch out for these.

* __%__ is a staircase to other levels

* __:__ is a piece of food.

* __A-Z__, the uppercase letters represent the various inhabitants of the Dungeons of Doom. Watch out, they can be nasty and vicious.

## 4. Commands

Commands are given to rogue by typing one or two characters. Most commands can be preceded by a count to repeat them (e.g. typing `10s` will do ten searches). Commands for which counts make no sense have the count ignored. To cancel a count or a prefix, press the escape-key . The list of commands is rather long, but it can be read at any time during the game with the `?` command. Here it is for reference, with a short explanation of each command.


* __?__, the help command. Asks for a character to give help on. If you type a `*`, it will list all the commands, otherwise it will explain what the character you typed does.

* __/__, This is the _"What is that on the screen?"_ command. A `/` followed by any character that you see on the level, will tell you what that character is. For instance, typing `/@` will tell you that the `@` symbol represents you, the player.

* __h__, __H__, __^H  _(ctrl+h)___, Move left. You move one space to the left. If you use upper case 'h' (shift+h), you will continue to move left until you run into something. This works for all movement commands (e.g. `L` means run in direction `l`). If you use the '^h' (ctrl+h), you will continue moving in the specified direction until you pass something interesting or run into a wall. You should experiment with this, since it is a very useful command, but very difficult to describe. This also works for all movement commands.

* __j__ to move down.

* __k__ to move up.

* __l__ to move right.

* __y__ to move diagonally up and left.

* __u__ to move diagonally up and right.

* __b__ to move diagonally down and left.

* __n__ to move diagonally down and right.

* __t__ to throw an object. This is a prefix command. When followed with a direction it throws an object in the specified direction. (e.g. type “th” to throw something to the left.)

* __f__, fight until someone dies. When followed with a direction this will force you to fight the creature in that direction until either you or it bites the big one.

* __m__ to move onto something without picking it up. This will move you one space in the direction you specify and, if there is an object there you can pick up, it won't do it.

* __z__ is the zap prefix. Point a staff or wand in a given direction and fire it. Even non-directional staves must be pointed in some direction to be used.

* __^__, Identify trap command. If a trap is on your map and you can't remember what type it is, you can get rogue to remind you by getting next to it and typing `^` followed by the direction that would move you on top of it.

* __s__, Search for traps and secret doors. Examine each space immediately adjacent to you for the existence of a trap or secret door. There is a large chance that even if there is something there, you won�t find it, so you might have to search a while before you find something.

* __>__, Climb down a staircase to the next level. Not surprisingly, this can only be done if you are standing on staircase.

* __<__, Climb up a staircase to the level above. This can�t be done without the Amulet of Yendor in your possession.

* __.__ (dot) to rest. This is the �do nothing� command. This is good for waiting and healing.

* __,__ (semicolon) to pick up something. This picks up whatever you are currently standing on, if you are standing on anything at all.

* __i__ shows the inventory. List what you are carrying in your pack.

* __I__ shows a selective inventory. Tells you what a single item in your pack is.

* __q__, quaff one of the potions you are carrying.

* __r__, read one of the scrolls in your pack.

* __e__, eat food from your pack.

* __w__ to wield a weapon. Take a weapon out of your pack and carry it for use in combat, replacing the one you are currently using (if any).

* __W__ to wear armor. You can only wear one suit of armor at a time. This takes extra time.

* __T__ to take armor off. You can't remove armor that is cursed. This takes extra time.

* __P__ to put on a ring. You can wear only two rings at a time (one on each hand). If you aren't wearing any rings, this command will ask you which hand you want to wear it on, otherwise, it will place it on the unused hand. The program assumes that you wield your sword in your right hand.

* __R__ to remove a ring. If you are only wearing one ring, this command takes it off. If you are wearing two, it will ask you which one you wish to remove,

* __d__ to drop an object. Take something out of your pack and leave it lying on the floor. Only one object can occupy each space. You cannot drop a cursed object at all if you are wielding or wearing it.

* __c__ to call an object something. If you have a type of object in your pack which you wish to remember something about, you can use the call command to give a name to that type of object. This is usually used when you figure out what a potion, scroll, ring, or staff is after you pick it up, or when you want to remember which of those swords in your pack you were wielding.

* __D__ to print out which things you've discovered something about. This command will ask you what type of thing you are interested in. If you type the character for a given type of object (e.g. `!` for potion) it will tell you which kinds of that type of object you’ve discovered (i.e., figured out what they are). This command works for potions, scrolls, rings, and staves and wands.

* __o__ to examine and set options. This command is further explained in the section on options.

* __^R _(ctrl+r)___ redraws the screen. Useful if spurious messages or transmission errors have messed up the display.

* __^P _(ctrl+p)___ prints the last message. Useful when a message disappears before you can read it. This only repeats the last message that was not a mistyped command so that you don't loose anything by accidentally typing the wrong character instead of `^P`.

* __ESCAPE__, Cancel a command, prefix, or count.

* __!__, Escape to a shell for some commands.

* __Q__ to quit. Leave the game.

* __S__ to save the current game in a file. It will ask you whether you wish to use the default save file. Caveat: Rogue won’t let you start up a copy of a saved game, and it removes the save file as soon as you start up a restored game. This is to prevent people from saving a game just before a dangerous position and then restarting it if they die. To restore a saved game, give the file name as an argument to rogue. As in

    ```bash
    $> rogue save_file
    ```

    To restart from the default save file (see below), run

    ```bash
    % rogue -r
    ```
* __v__ prints the program version number.

* __)__ prints the weapon you are currently wielding

* __]__ prints the armor you are currently wearing

* __=__ prints the rings you are currently wearing

* __@__ reprints the status line on the message line

## 5. Rooms

Rooms in the dungeons are either lit or dark. If you walk into a lit room, the entire room will be drawn on the screen as soon as you enter. If you walk into a dark room, it will only be displayed as you explore it. Upon leaving a room, all monsters inside the room are erased from the screen. In the darkness you can only see one space in all directions around you. A corridor is always dark.

## 6. Fighting

If you see a monster and you wish to fight it, just attempt to run into it. Many times a monster you find will mind its own business unless you attack it. It is often the case that discretion is the better part of valor.

## 7. Objects you can find

When you find something in the dungeon, it is common to want to pick the object up. This is accomplished in rogue by walking over the object (unless you use the `m` prefix, see above). If you are carrying too many things, the pro- gram will tell you and it won’t pick up the object, other- wise it will add it to your pack and tell you what you just picked up.

Many of the commands that operate on objects must prompt you to find out which object you want to use. If you change your mind and don’t want to do that command after all, just type an `ESCAPE` and the command will be aborted.

Some objects, like armor and weapons, are easily dif- ferentiated. Others, like scrolls and potions, are given labels which vary according to type. During a game, any two of the same kind of object with the same label are the same type. However, the labels will vary from game to game.

When you use one of these labeled objects, if its effect is obvious, rogue will remember what it is for you. If it’s effect isn’t extremely obvious you will be asked what you want to scribble on it so you will recognize it later, or you can use the “call” command (see above).

### 7.1. Weapons

Some weapons, like arrows, come in bunches, but most come one at a time. In order to use a weapon, you must wield it. To fire an arrow out of a bow, you must first wield the bow, then throw the arrow. You can only wield one weapon at a time, but you can’t change weapons if the one you are currently wielding is cursed. The commands to use weapons are `w` (wield) and `t` (throw).

### 7.2. Armor

There are various sorts of armor lying around in the dungeon. Some of it is enchanted, some is cursed, and some is just normal. Different armor types have different armor protection. The higher the armor protection, the more protection the armor affords against the blows of monsters. Here is a list of the various armor types and their normal armor protection:

| Type                        | Protection |
|:----------------------------|:----------:|
| None                        |      0     |
| Leather armor               |      2     |
| Studded leather / Ring mail |      3     |
| Scale mail                  |      4     |
| Chain mail                  |      5     |
| Banded mail / Splint mail   |      6     |
| Plate mail                  |      7     |

If a piece of armor is enchanted, its armor protection will be higher than normal. If a suit of armor is cursed, its armor protection will be lower, and you will not be able to remove it. However, not all armor with a protection that is lower than normal is cursed.

The commands to use weapons are `W` (wear) and `T` (take off).

### 7.3. Scrolls

Scrolls come with titles in an unknown tongue [3]. After you read a scroll, it disappears from your pack. The com mand to use a scroll is `r` (read).

### 7.4. Potions

Potions are labeled by the color of the liquid inside the flask. They disappear after being quaffed. The command to use a scroll is `q` (quaff).

### 7.5. Staves and Wands

Staves and wands do the same kinds of things. Staves are identified by a type of wood; wands by a type of metal or bone. They are generally things you want to do to some- thing over a long distance, so you must point them at what you wish to affect to use them. Some staves are not affected by the direction they are pointed, though. Staves come with multiple magic charges, the number being random, and when they are used up, the staff is just a piece of wood or metal.

The command to use a wand or staff is `z` (zap)

### 7.6. Rings

Rings are very useful items, since they are relatively permanent magic, unlike the usually fleeting effects of potions, scrolls, and staves. Of course, the bad rings are also more powerful. Most rings also cause you to use up food more rapidly, the rate varying with the type of ring. Rings are differentiated by their stone settings. The com- mands to use rings are `P` (put on) and `R` (remove).

### 7.7. Food

Food is necessary to keep you going. If you go too long without eating you will faint, and eventually die of starvation. The command to use food is `e` (eat).

## 8. Options

Due to variations in personal tastes and conceptions of the way rogue should do things, there are a set of options you can set that cause rogue to behave in various different ways.

### 8.1 Setting the options

There are two ways to set the options. The first is with the `o` command of rogue; the second is with the `ROGUEOPTS` environment variable.

#### 8.1.1. Using the `o` command

When you type `o` in rogue, it clears the screen and displays the current settings for all the options. It then places the cursor by the value of the first option and waits for you to type. You can type a `RETURN` which means to go to the next option, a `-` which means to go to the previous option, an `ESCAPE` which means to return to the game, or you can give the option a value. For boolean options this merely involves typing `t` for true or `f` for false. For string options, type the new value followed by a `RETURN` .

#### 8.1.2. Using the `ROGUEOPTS` variable

The `ROGUEOPTS` variable is a string containing a comma separated list of initial values for the various options. Boolean variables can be turned on by listing their name or turned off by putting a “no” in front of the name. Thus to set up an environment variable so that jump is on, terse is off, and the name is set to “Blue Meanie”, use the command[4]

```bash
$> setenv ROGUEOPTS "jump,noterse,name=Blue Meanie"
```


### 8.2. Option list
Here is a list of the options and an explanation of what each one is for. The default value for each is enclosed in square brackets. For character string options, input over fifty characters will be ignored.

* __terse [noterse]__

    Useful for those who are tired of the sometimes lengthy messages of rogue. This is a useful option for playing on slow terminals, so this option defaults to terse if you are on a slow (1200 baud or under) terminal.

* __jump [nojump]__

    If this option is set, running moves will not be displayed until you reach the end of the move. This saves considerable cpu and display time. This option defaults to jump if you are using a slow terminal.

* __flush [noflush]__

    All typeahead is thrown away after each round of battle. This is useful for those who type far ahead and then watch in dismay as a Bat kills them.

* __seefloor [seefloor]__

    Display the floor around you on the screen as you move through dark rooms. Due to the amount of characters generated, this option defaults to noseefloor if you are using a slow terminal.

* __passgo [nopassgo]__

    Follow turnings in passageways. If you run in a pas- sage and you run into stone or a wall, rogue will see if it can turn to the right or left. If it can only turn one way, it will turn that way. If it can turn either or neither, it will stop. This algorithm can sometimes lead to slightly confusing occurrences which is why it defaults to nopassgo.

* __tombstone [tombstone]__

    Print out the tombstone at the end if you get killed. This is nice but slow, so you can turn it off if you like.

* __inven [overwrite]__

    Inventory type. This can have one of three values: overwrite, slow, or clear. With overwrite the top lines of the map are overwritten with the list when inventory is requested or when “Which item do you wish to . . .? ” questions are answered with a “*”. How- ever, if the list is longer than a screenful, the screen is cleared. With slow, lists are displayed one item at a time on the top of the screen, and with clear, the screen is cleared, the list is displayed, and then the dungeon level is re-displayed. Due to speed considerations, clear is the default for terminals without clear-to-end-of-line capabilities.

* __name [account name]__

    This is the name of your character. It is used if you get on the top ten scorer’s list.

* __fruit [slime-mold]__

    This should hold the name of a fruit that you enjoy eating. It is basically a whimsy that rogue uses in a couple of places.

* __file [~/rogue.save]__

    The default file name for saving the game. If your phone is hung up by accident, rogue will automatically save the game in this file. The file name may start with the special character “~” which expands to be your home directory.

## 9. Scoring

Rogue usually maintains a list of the top scoring people or scores on your machine. Depending on how it is set up, it can post either the top scores or the top players. In the latter case, each account on the machine can post only one non-winning score on this list. If you score higher than someone else on this list, or better your previous score on the list, you will be inserted in the proper place under your current name. How many scores are kept can also be set up by whoever installs it on your machine.

If you quit the game, you get out with all of your gold intact. If, however, you get killed in the Dungeons of Doom, your body is forwarded to your next-of-kin, along with 90% of your gold; ten percent of your gold is kept by the Dungeons’ wizard as a fee[5]. This should make you consider whether you want to take one last hit at that monster and possibly live, or quit and thus stop with whatever you have. If you quit, you do get all your gold, but if you swing and live, you might find more.

If you just want to see what the current top players/games list is, you can type
```bash
$> rogue −s
```

## 10. Acknowledgements

Rogue was originally conceived of by Glenn Wichman and Michael Toy. Ken Arnold and Michael Toy then smoothed out the user interface, and added jillions of new features. We would like to thank Bob Arnold, Michelle Busch, Andy Hatcher, Kipp Hickman, Mark Horton, Daniel Jensen, Bill Joy, Joe Kalash, Steve Maurer, Marty McNary, Jan Miller, and Scott Nelson for their ideas and assistance; and also the teeming multitudes who graciously ignored work, school, and social life to play rogue and send us bugs, complaints, suggestions, and just plain flames. And also Mom.

    UNIX is a registered trademark of The Open Group

_Footnotes:_
1) As opposed to pseudo English sentences.
2) A minimum screen size of 24 lines by 80 columns is required. If the screen is larger, only the 24x80 section will be used for the map.
3) Actually, it's a dialect spoken only by the twenty-seven members of a tribe in Outer Mongolia, but you're not supposed to know that.
4) For those of you who use the Bourne shell sh (1), the commands would be
    ```bash
    $> ROGUEOPTS="jump,noterse,name=Blue Meanie"
    $> export ROGUEOPTS
    ``` 
5) The Dungeon's wizard is named Wally the Wonder Badger. Invocations should be accompanied by a sizable donation.
