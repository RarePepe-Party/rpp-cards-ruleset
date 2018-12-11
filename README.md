# rpp-cards-ruleset
Public repository of the cards ruleset and API

## Organization of rulesets

All files should be classified by collection on a subdirectory. I.e. RAREPEPE cards should be on a directory called `RAREPEPE`, SOG cards on a `SOG` directory, etc.

Each card should have one file representing their behaviour, this behaviour is a [lua] file with several predefined functions that get called by the runtime in order to execute card logic.

Rarepepe.Party uses [moonsharp] as Lua runtime, and all the inherent restrictions to it apply to rule scripts.

## Card lifecycle

_Overworld events_:

 * OvwCreate: The card is instantiated for Overwold gameplay. 
 * OvwDraw: The card got drawn into a play slot.
 * OvwActivate: The card got activated by the player.
 * OvwHeartbeat: The card reached a timeout for overworld interaction and can activate its ability.
 * OvwDeactivate: The card got deactivated by the player.
 * OvwShare: The card got shared to the team.

_PvP events_:

 * PvpCreate: The card is instantiated for PvP gameplay.
 * PvpShuffle: The card got inserted into the play deck.
 * PvpDraw: The card was drawn by the player.
 * PvpDiscard: The card got discarded from the hand.
 * PvpPlay: The card got played by the player.
 * PvpActivate: The card got activated by the player.
 * PvpStatsChange: The card got a basic stat changed by an event.
 * PvpDestroyed: The card got destroyed in the game area.
 * PvpGraveyard: The card entered the graveyard.
 * PvpOutOfGraveyard: The card got out of the graveyard.

_Team evetns_:

 * TeamCreate: The card is instantiated for team gameplay.
 * TeamUse: A user activated the card's team effect.
 * TeamHeartbeat: The card reached a timeout for team interaction and can activate its ability.
 * TeamDispel: The card's effect over the team ended and must clean up.

[lua]: https://www.lua.org
[moonsharp]: http://www.moonsharp.org/
