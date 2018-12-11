# rpp-cards-ruleset
Public repository of the cards ruleset and API

## Organization of rulesets

All files should be classified by collection on a subdirectory. I.e. RAREPEPE cards should be on a directory called `RAREPEPE`, SOG cards on a `SOG` directory, etc.

Each card should have one file representing their behaviour, this behaviour is a [lua] file with several predefined functions that get called by the runtime in order to execute card logic.

Rarepepe.Party uses [moonsharp] as Lua runtime, and all the inherent restrictions to it apply to rule scripts.

## Git functionality for game rules

Git provides a full set of versioning, milestone, tags and branches. This functionality will be fully support by Rarepepe.party for ruleset specification as follows:

 * _Branches_: Branches will be treated as different variants of the game. Each branch should change its `descriptor.json` file to state what this ruleset variant does.
 * _Tags_: Tags specify the version of the variant. Only tagged commits will be treated as valid versions (besides HEAD which will be treated as Beta version of the branch).
 * _Forks_: Forked repos are treated as universes. There's only one official universe (RarePepe-Party/rpp-cards-ruleset) but user made universes are encouraged and will be actively promoted as long as the Github API provides fork inspection.

## Game modes

The game has 3 modes where the cards can be used: Overworld, PvP and Team.

### Overworld

In this mode the players move freely in a two dimensional map as part of a team, with resources available to be gathered by the activation of certain cards with sources that are engulfed by each team's territory. These resources are of a certain type, and can only be extracted by the use of certain cards.

### PvP

In this mode the players confront each other taking turns at activating their cards' abilities and using utility cards to gain an edge over the other player. Certain cards spawn "creatures" into the gameplay area and other cards create effects over cards, gameplay conditions or the other player.

A game mechanic where players can help others in PvP is being developed and will be filled in in this space when developed.

### Team

In this mode the cards create effects over all the players in the team continuously or depending on certain conditions. These effects should be better the rarer the card.

Cards played as "team cards" can potentially have upkeep costs for the whole team and each player should balance how much of these cards are in use at any time.

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
