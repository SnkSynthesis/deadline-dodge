# Player Movement Logic

This is the logic that takes input from the user and manipulates the position
of the player. There are 3 buttons that the user can press:

* LOAD button  - resets the position of the player
* Right button - moves player to the right
* Left button  - moves player to the left

**NOTE**: LOAD has higher priority than Right or Left, so if Right/Left is pressed
at the same time of the player, then the player position will be reset.

We achieved this by using 2 bi-direcitonal 4-bit shift registers driven by SOP logic.
We initially had an asynchronous movement system (independent from system clock)
but we encountered a lot of issues/bugginess with this, so we opted to make it synchronous instead
which proved to be a lot less buggy yet with similar responsiveness.

![Player Movement Logic Schematic](player_movement_schematic.png)

_Screenshot of player_movement_schematic.ms14_



