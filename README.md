# Actor Spawner
## By Chickensaver (Bahlph#0486)

### Basic Info:
This new Actor Spawner has the ability to spawn any actor in the game with any arrangement of nybbles 1-12.  It works by pulling nybble information from a corresponding Actor Spawner in Data Bank mode.

This code is set up to work with the original Newer source code (not NSMBWer or more-sprites).  If you'd like a variant for NSMBWer or more-sprites, feel free to contact me!  Additionally, if there are any features you've always wanted in the Actor Spawner, tell me about them!

### Set-Up:
To use this actor, you'll have to do the following:
1. Edit `makeNewerKP.yaml` (or create your own project) that does not include the original `spritespawner` file.  Instead, include `ActorSpawner.yaml`.
2. Move the files from the `Kamek` folder supplied here to their respective locations in your filesystem.
3. Open `game.h` and find `u16 spriteFlagNum;` and `u64 spriteFlagMask;`.  Replace those two lines with the following:
```
union {
    u16 spriteFlagNum;

    struct {
        u8 eventId2; // nybble 1-2
        u8 eventId1; // nybble 3-4
    };
};
u64 spriteFlagMask; // 0 if both eventId2 and eventId1 are 0, otherwise "1ULL << ((eventId2 ? eventId2 : eventId1) - 1)"
```

Now the code should be good to go!  Feel free to contact me if you have any problems.

### Extras:
The edited version of the NewerGEM `spritedata.xml` can be used to make editing the sprite in Reggie easier.  Simply add it to `reggiedata/patches/NewerGEM/` and restart Reggie.  There is also a testing level that that includes comments viewable in Reggie on how to set up the Actor Spawner in various ways.

### Thank You!
Thanks to everyone on the Horizon and NHD Discord servers!  Your comments and help were always appreciated!