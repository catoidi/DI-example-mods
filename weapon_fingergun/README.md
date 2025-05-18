# DI-bonus
> [!NOTE]
> **This requires a copy of "DI: Debt is Inevitable" v0.8.1 or above to run.**
 
This repo all of the code related to the weapon, "Finger Gun". This weapon is unlocked via reaching Swag Level 8.

[DI's Steam page can be found here.](https://store.steampowered.com/app/2318300/DI_Debt_is_Inevitable/)

[DI's source code can be found here.](https://github.com/catoidi/DI-game) *(does not contain all content needed to play game.)*

Designed to give aspiring modders a helping hand on making their own custom weapons. To make use of this, it's best if you already have knowledge of modding GZDoom, including things like ZScript, Weapon States, the Inventory system, CVar's, and interpreting custom-made lumps.

## "zscript_finger" contains the code for the actual weapon.
- The code was placed inside it's own folder, to reduce the chance of this addon's code being overwritten by another.
- All weapons in DI inherit from a Parent class called "DI_Weapon". To make use of all DI features, it is highly recommended to use this for your own weapons.
- DI_Weapon comes with many custom features. Documentation of each feature is currently very limited.
- If confused on the purpose behind a variable or function, you may need to open the DI.ipk3 file, and find the ``zscript_DI/weapons/base.zsc`` file to find out directly from the source.

## "DISHOP.txt" contains the code that adds the weapon to the Shop Item Pool.
The DISHOP file is structured like this:
1. Name the pool the item is assigned to. Some examples of pools are "NormalWeapon", "StartingWeapon", "Consumable", and "PermaPassive". We will be using "NormalWeapon", so the weapon can spawn in the same locations as other weapons like the Double Shotgun. See the DISHOP.txt in the main DI.ipk3 file for more details.
2. Name the actual item you're adding. In our case, the name is "FingerGun".
3. Name the sprite that will be displayed in the shop to represent this item. This requires the four letter sprite name and the frame, but not it's rotation. For our use case, we use "FINGZ".
4. (OPTIONALLY!) You can also assign a rarity to the item. This is between 1/256, with 256 being guaranteed to spawn. If the chance fails, the item is simply not added to that specific shop's item pool. Note that multiple shops with the same pool can have different items because of this mechanic.
5. (OPTIONALLY!) You can also set a Boolean CVAR here that is required to be true in order to add this item to the shop pool. Designed to be used alongside the "DIUNLOCK.txt" file for full integration with the game's unlock mechanics. Note that the 4th argument must be defined to use the this one as well.

## "DIWIPE.txt" contains the code that ensures the weapon can get properly removed from your inventory for rental shops.
- Adding things like Weapons and Passives to this list is required.
- Some items make use of secondary inventory items, like ammo for weapons. These are not required to be added, but may be desirable to do so.
- Powerups and Consumables are intended to carry over between waves, and should NEVER be added to this list, unless you specifically desire your consumable to be wiped upon wave completion.
- The game already natively differentiates between regular items and "permanent" items.

## "DIUNLOCK.txt" is what adds our item to the Unlocks Menu. Read the comments inside the file for more details.
- Adding the item to DIUNLOCK is required if you want the item to be visible inside the Unlocks menu.
- Graphics used in DIUNLOCK.txt must be placed inside the "graphics/unlocks/" folder, and named after the item's associated CVar, to avoid potential conflicts.

## "DISWAG.txt" integrates our item with the Swag Level system, automatically unlocking our item upon reaching Swag Level 8.
- Using DISWAG is not a requirement for any unlockable items.
- If we wanted to have a custom unlock condition, it's as simple as sending "diunlock_CVAR", with "CVAR" being replaced by our custom CVar, via an Interface Event.
- Here's what that could look like: ``if (unlock == true) {eventhandler.sendinterfaceevent(consoleplayer, "diunlock_di_unlock_item_fingergun");}``
