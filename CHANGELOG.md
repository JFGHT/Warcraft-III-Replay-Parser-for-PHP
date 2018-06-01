2.5 (01.06.18) - WAR 1.29
- fixed: updated colors for the new 24 players.
- fixed: global total players in cleanup function.
- fixed: bug parsing custom games.

2.4 (07.08.10)
- fixed: handling of 0x54 command block (problems with some custom map replays, thanks to Mike Plichta)
- fixed: handling of 0x60 action (resulting in less errors in DOTA replays)
- fixed: handling of computer players (got rid of 'Argument #1 is not an array' message, now all computer players are listed)
- changed: now if the script finds an unknown action it skips the whole CommandData block
- changed: time no longer serves as indices in errors array (multiple errors possible within one TimeSlot block)
- fixed: wrong paths to Battle.net player profiles and map images (old Battle.net paths now begin with http://classic.battle.net/)
- fixed: [example] using urlencode() for replay URLs (thanks to Mike Plichta)

2.3 (06.01.08)
- fixed: problems with replays with modified chatlog ('Incomplete replay file' error, e.g. from Replays.net; thanks to Michael Fortier)
- fixed: issues on machines using big endian byte order, e.g. Macs (changed all machine byte order codes to little endian byte order codes in unpack() functions)
- fixed: Destroyers counting issues (I hope it's OK now...)
- fixed: convert_ai() was never returning Insane
- fixed: [example] if the winner is unknown it shows unknown for all teams
- fixed: [example] Rain of Fire icon name (was reignoffire.gif)
- changed: [example] the script works with register_globals = off by default
- - added: the name of the player who paused/resumed the game

2.2 (25.05.05)

- fixed: hero abilities after using a Tome of Retraining (not 100% perfect but should work in most cases)
- fixed: units from 2 or more rax counted once (there are still some minor issues left but it should work better now)
- fixed: generally units should be counted a bit more precisely now (but the numbers still aren't 100% correct)
- fixed: not counting Destroyers, now Obsidian Statues are statues which haven't been morphed (so Destroyers + Obsidian Statues = total statues)
- fixed: not counting Incinerate ability in 1.18 replays
- fixed: not counting high level Tinker's abilities
- fixed: in replays saved by Waaagh!TV users there were sometimes unnecessary player records which shouldn't have been shown (thanks to Nagger)
- fixed: problems with actions in tournament replays from Battle.net website
- fixed: [example] got rid of some of the notices
- changed: boolean values are no longer converted to Yes/No (convert_yesno() changed to convert_bool())
- changed: [example] private names in chatlog are now shown instead of numbers
- added: hotkeys array for each player containing the number of each group hotkey assigments and uses (and an interpretation in example.php)
- added: handling Select subgroup actions (TAB key, etc.) for 1.14b and higher replays (up to these days, we were able to count them only in older replays but I think I've figured out the algorithm; APM is a bit higher now)
- added: [example] additional items in General information
- added: "[number] [unit name]" in units order arrays, where number is the number of units trained at one click; -1 means that the unit was cancelled
- added: support for RoC replays older than 1.03 patch ;)
- added: support for computer players

2.1 (12.11.04):

- fixed: not showing all chat messages when the game was paused (this change has also a little influence on example.php)
- fixed: wrong interpreting of rare chat blocks with flag = 16
- fixed: [example] Blood Mage and Dreadlord ultimate's icons
- fixed: [example] nothing happened when submitting "Check your own replay!"
- fixed: [example] don't show units when the amount < 0
- added: [example] the code for register_globals = off

2.0 (21.09.04):

PLEASE READ THE CHANGES CAREFULLY as the new version may not work with your own frontend based on an older version of the parser.
- fixed: too high hero levels/abilities in some replays
- fixed: too many upgrades in some replays
- fixed: probably Frost Armor ability and Troll Berserkers (Trolls made after the Berserker upgrade) weren't counted at all
- fixed: no names of players (Player X) in FFA replays
- fixed: minor code issues
- fixed: a few spelling mistakes
- fixed: [example] warnings when a player was disconnected at the beginning
- changed: there is no players array anymore - no need of duplicating the data that is sorted in teams array (so the database files are smaller now)
- changed: there is no color_html property for players anymore, color names have also changed a bit, html colors are now defined in style.css (this change also applies to the example)
- changed: handling unknown actions - now the script will try to parse the replay to the end even if it encounters an unknown action (those actions and additionally unknown Item IDs are now stored in errors array)
- changed: $max_datablock to 1500, new record of block size is a bit over 1000, so the previous value wasn't enough
- changed: [example] shorter ids for layers (using player_id instead of name)
- added: 1.17 heroes support (Firelord and Goblin Alchemist)
- added: saver_name property in game array
- added: [example] icons for hero abilities (thanks to Franck)
- added: [example] a notification if errors array is non-empty
- added: [example] a link to the homepage

1.9 (15.05.04):

- fixed: now detecting 1.14a/1.14b replays by the build not by the version
- added: support for 1.15 replays (Goblin Tinker; thx to Dylan Smith and Shadowflare forum members)
- added: [example] proper message if replay directory contains no replays
- changed: removed @ before gzinflate() so now you should get a proper error if you don't have zlib support

1.8c (14.01.04):

- added: 1.14 support (mainly Custom Games; big thx to Mike)

1.8b (07.01.04):

- fixed: little APM counting issues (thx Nagger)

1.8 (04.01.04):

- fixed: APM counting (strictly based on w3g_actions.txt 0.96)
- fixed: showing wrong names of some items (e.g. Amulet of Recall instead of true item's name)
- added: actions 0x1A and 0x75 ("Only in scenarios, maybe a trigger-related command")
- added: [example] spaces (newlines) when players stopped chatting in chatlog

1.7 (21.12.03):

please use updated conversion functions in order to gain full performance boost
- fixed: parsing performance improved (up to 0.3 second less now thanks to miscellanous code optimizations)
- fixed: initiator index gave the opposite value
- fixed: [example] don't show units which were cancelled and finally never made by player
- added: support for 1.13 replays
- added: initiator variable in player array (is true for the first player who entered the game - usually creator, same as host in w3g_format)
- added: error message on unknown command block (never found such but just in case)
- added: flock() when reading replay file (just in case as well)
- changed: APM counting (now strictly based on w3g_actions 0.95, only 0x16 action changed resulting in few more APM for each player)
- changed: default max_datablock to 1000 (it doesn't make the script slower but seems to be more secure)

1.6 (14.12.03):

- fixed: no Obsidian Statues/Destroyers counting (conversion functions, pure unmorphed Obsidian Statues = Obsidian Statues - Destroyers)
- fixed: winner/loser detection (almost strictly based on w3g_format)
- fixed: weird values in chat array => proper treatment of 0x10 flag
- fixed: [example] dot in the name of a player caused JS error
- fixed: [example] if there was a tie it shows a tie
- changed: [example] creator is now host

1.5 (30.11.03):

please use updated conversion functions
- fixed: counting units (maybe heroes and other things too) even if their training was cancelled
- fixed: weird values in chat array when chat block with length below 6 was found (I have one such replay)
- fixed: replays in which game was saved were probably causing errors
- added: counting each action type separately (actions_details array)

1.4 (21.11.03):

please use updated conversion functions, many changes in this version!
- fixed: I guess winner detection should work better now...
- fixed: strange APM counting behavior in replays with observers (counting APM for all people, even observers or not counting at all)
- fixed: problems with APM counting in battle.net website replays
- fixed: wrong Spirit Walkers counting (sometimes they weren't counted or they weren't counted at all)
- added: more info about heroes - their level and learned skills (and levels of those skills), each hero is represented by an array now,
- added: items bought by each player, upgrades made by each player and buildings built by each player ;)
- added: map settings such as if referees mode was on, if the teams were fixed, etc.

1.3 (06.11.03):

- fixed: no time for players in replays without LeaveGame blocks (thanks to mrONLINE)
- fixed: counting time for players when there was one or more pauses in the game
- fixed: wrong APM counting in replays from battle.net website
- added: counting each hero revives+trainings and each unit trainings (please use updated conversion functions)
- added: proper error messages when replay file is incomplete or isn't a replay file at all
- changed: actions are now counted following Nagger's advices (http://shadowflare.gameproc.com/cgi-bin/yabb/YaBB.cgi?board=dev;action=display;num=1064821043)
- changed: max_datablock increased to 500 from 400 (400 wasn't enough for one replay I encountered)
- changed: default HTML colours in convert_color() to some nicer values

1.2 (29.10.03):

- fixed: wrong race conversion in custom games (please use new convert_race() function)
- fixed: few other bugs which caused warnings and errors in some replays
- added: detecting the winner/loser (game['winner_team'] and game['loser_team']), may not work for more than 2 teams
- added: detecting random race (remember to use new version of function provided with this version)
- added: convert_time() function to additional functions (it is not used in the main script, but you can use it in your frontend if you wish)
better support for tournament replays from battle.net website

1.1 (27.10.03):

- fixed: reading empty slots info
- fixed: counting APM for observers/referees
- changed: conversions funtions moved to separate file (for easier configuration)
- changed: 'time_played' is now simply 'time' (observers and referees don't play the game ;)
