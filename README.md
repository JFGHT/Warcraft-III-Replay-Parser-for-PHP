# Warcraft-III-Replay-Parser-for-PHP

Warcraft III Replay Parser? What is that? Maybe you know or maybe not that Warcraft III (strategy video game) replay files (*.w3g) have much information inside. Almost everything can be pulled out of them: players accounts, races, colours, heroes and units made by each player, chat log and many more. If you are a webmaster of Warcraft III replay site or clan page you know how boring adding new replays can be without automation. This PHP script helps you provide as much information about replays on your site as possible without all the hard work.

You can find the old version here: http://w3rep.sourceforge.net/

Couldn't be possible without the help of: http://w3g.deepnode.de/

# Current supported w3 version

1.29

# Changelog

https://github.com/JFGHT/Warcraft-III-Replay-Parser-for-PHP/blob/master/CHANGELOG.md


# TODO

- add map checksum
- add traded resources
- prevent alien heroes (skills chosen by team mates)?
- winner detection needs some improvements (it isn't 100% correct)
- counting units needs to be checked (duplicate actions, multiple buildings under one hotkey, ESC pressed) investigate 0x19 select subgroup thoroughly, also regarding unit_multiplier add APM chart (mb as another variable in the class, e.g. $replay->apmchart, mime-type: image/png; http://evoluted.net/community/code/imageeditor.php ?)
- add players' starting positions on the map image?
- possibly DOTA support (http://shadowflare.samods.org/cgi-bin/yabb/YaBB.cgi?board=dev;action=display;num=1186677656 ?) (http://forums.dota-allstars.com/index.php?showtopic=181408)
