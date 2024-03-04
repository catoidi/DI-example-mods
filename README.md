# DI-bonus
Bonus content made for DI: Debt is Inevitable.

Designed to give aspiring modders a helping hand on making their own custom weapons.

"zscript_finger" contains the code for the actual weapon.

"DISHOP.txt" contains the code that adds the weapon to the Shop Item Pool.

The DISHOP file is structured like this:
1. Name the pool the item is assigned to. Some examples of pools are "NormalWeapon", "StartingWeapon", "Consumable", and "PermaPassive". We will be using "NormalWeapon", so the weapon can spawn in the same locations as other weapons like the Double Shotgun. See the DISHOP.txt in the main DI.ipk3 file for more details.
2. Name the actual item you're adding. In our case, the name is "FingerGun".
3. Name the sprite that will be displayed in the shop to represent this item. This requires the four letter sprite name and the frame, but not it's rotation. For our use case, we use "FINGZ".
4. (OPTIONALLY!) You can also assign a rarity to the item. This is between 1/256, with 256 being guaranteed to spawn. If the chance fails, the item is simply not added to that specific shop's item pool. Note that multiple shops with the same pool can have different items because of this mechanic.
5. (OPTIONALLY!) You can also set a Boolean CVAR here that is required to be true in order to add this item to the shop pool. Designed to be used alongside the "DIUNLOCK.txt" file for full integration with the game's unlock mechanics. Note that the 4th argument must be defined to use the this one as well.

"DIWIPE.txt" contains the code that ensures the weapon can get properly removed from your inventory for rental shops.

"DIUNLOCK.txt" is what adds our item to the Unlocks Menu. Read the comments inside the file for more details.

"DISWAG.txt" integrates our item with the Swag Level system, automatically unlocking our item upon reaching Swag Level 8.
- If we wanted to have a custom unlock condition, it's as simple as sending "diunlock_CVAR", with "CVAR" being replaced by our custom CVar, via an Interface Event.
- Here's what that could look like:
- ``if (unlock == true) {eventhandler.sendinterfaceevent(consoleplayer, "diunlock_di_unlock_item_fingergun");}``
