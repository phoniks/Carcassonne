# Carcassonne
A blockchain clone of the Carcassone board game designed by Klaus-Jürgen Wrede

The purpose of this repository is to gain practice implementing Ethereum (Solidity)smart-contracts by creating a digital version of the board game Carcassone.  

## Components

72 land tiles showing *roads*, *cities*, *fields*, *monastaries*.
12 River tiles which can be *riverhead*, *lake* ,*straight*, *curved*,. Each has an orientation which 
7 Followers per player (this implementation allows for just 2 players)
1 Scorecard


## Setup

The system places the riverhead tile in the center of the board with a random orientation.    Youngest player (Player 1) draws a tile from the river card stack and places it so that the orientation matches the riverhead.  Oldest player (Player 2) follows suit afterwards, and so on until all the tiles are laid, taking care that two curves never go in the same direction.  
Once the stack is depleted the system places the lake tile and shuffles and distributes the land tiles evenly between both players before play begins.

## Gameplay

Players take turns beginning with Player 1.  Each turn cosists of 3 phases: 
1. Draw and place a tile,
2. (Optional) Place *one* follower on the tile placed this turn.
3. Score any points earned for completing a road, monastary, or city.

Each phase is explained in detail following this section.  Gameplay ends when all tiles have been placed.

## Placing Land Tiles
Each player MUST draw and place one land tile per turn. When placing a tile it must border an already played tile on at least one side(not on a diagonal). New tiles should always continue existing roads, cities, and/or fields. If a tile drawn cannot be placed that tile is removed from the game and the player draws a new tile. 

## Placing Followers
Each player MAY place a follower according to these rules: 
1. One follower per turn.
2. The follower must come from the player's supply.
3. The follwer must be played on the tile the player placed this turn.
4. Followers can be placed on cities, roads, monasteries, and fields.
5. Followers can not be place on a road, city, or field section adjacent to a section of the same time that is already occupied by a follower.

If a player runs out of followers they continue placing tiles.  Followers can never be recalled. Followers are returned to the players supply when the section they occupy is scored. 

## Scoring 

Scoring takes place when road, city or monastary that a follower is occupying is completed.  In the case of Fields they are scored at the end of the game along with any incomplete roads cities, or monasteries.  Completion rules are as follows:

Roads: When both ends of the road are connected to a crossroad (including the originating crossroad), city and/or monasteries.
(1pt/section)
Cities: When all sections are enclosed by walls. (2pts/section & 2pts/banner)
Monastaries: When the tile on which the monastery lies is surrounded by tiles on all sides (including diagonals)
(9pts)

