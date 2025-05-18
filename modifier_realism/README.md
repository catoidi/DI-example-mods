# Example Mod - Difficulty Modifier - Realism
> [!NOTE]
> **A copy of DI: Debt is Inevitable (v0.12.1 or above) is required.**
 
This repo shows how you can add a custom Difficulty Modifier to the game.
Here's what this example mod does:
- Adds a new modifier called "Realism" to the game.
- The modifier will make the player take 3x DMG from all enemies, and give the player movement-based inaccuracy.
- In exchange for this, the player's high score will be increased by 25%.
- Unlocked by getting a final score of at least 5000 points in any level as any character.

It's best if you already have knowledge of modding GZDoom, but people new to modding might be able to follow along as well.

All files here, excluding the .png file, contains a plethora of comments to explain each line of code.

### "graphics/unlocks/example_unlock_mod_realism.png"
- This is the icon of the new Difficulty Modifier.
- This icon is used in both the New Game Menu and when the player unlocks the modifier for the first time.
### "zscript_mod_realism/"
- This is the folder containing most of the code for the Difficulty Modifier.
- The code was placed inside it's own folder, to reduce the chance of this addon's code being overwritten by another.
- Contained in this folder is "eventhandler.zsc" and "item.zsc".
- "eventhandler.zsc" is a new EventHandler added by this mod that simply checks if the player has the new modifier enabled, and then grants them a new item if it is.
- "item.zsc" is the item granted to the player when the modifier is enabled. This is the part that actually affects the player's stats and whatnot.
### DIGAME.txt
- This is the script file that adds the modifier to the New Game Menu screen.
### DISCORE.txt
- Used to add the modifier's score-based unlock condition.
### cvarinfo.txt
- Contains 2 console variables needed for the modifier to function.
### language.enu
- Contains all the strings of text related to the modifier that appear ingame.
### zscript.zsc
- Defines the minimum gzdoom version needed for this mod to work, and loads the scripts found in the "zscript_mod_realism" folder.
