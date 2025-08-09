# Speed Logic

VERSION I 
Speed Logic
This circuitry controls the speed of the [LFSR-decoder logic](../lfsr-decoder-logic/) and, in turn, how fast the rocks fall in the game. It is a modular feature that introduces three distinct speed levels.

When the player survives for a set amount of time without triggering the Collision Logic (i.e., without losing), the Speed Logic activates, increasing the game speed and making the game progressively harder.

Operation
-Triggering the Speed Increase-
An AND gate detects the LFSR state 1111 (inputs: Qa, Qb, Qc, Qd), which occurs at regular intervals. This output increments a mod-6 counter (74LS163N). Although the counter is designed to count up to 6, it is forced to jump directly to its maximum count (1111). This sets the RCO pin high, triggering the next stage.

-Speed Level Control-
The next stage is another 74LS163N counter. Each time this counter is incremented, the game speed increases. After two speed increases, the counter locks at its highest setting so the final speed is maintained for the rest of the game.

-Speed Selection and Distribution-
The counter’s outputs are decoded with combinational logic to control a 74LS153 4-to-1 multiplexer (MUX).

The MUX selects between three clock inputs:

System clock (full speed)
Divide-by-2 clock
Divide-by-4 clock
The two divided clocks are generated from specific outputs of a counter driven by the system clock.

The MUX output determines the active game speed. This clock signal is fed back into the entire game so all elements operate in sync with the selected tempo.


VERSION II 
-This controls the speed of the [LFSR-decoder logic](../lfsr-decoder-logic/) and how fast the rocks fall down.
-The speed logic circuitry is a modular feature that introduces three different speed levels to the game. 
-When the player has played for a certain amount of time without triggering the Collision Logic (aka without losing), the Speed Logic is triggered and the game speeds up making it more challenging for the player. 

An AND gate was used to capture the LFSRR state 1111 which iterates regularly. (inputs: Qa, Qb, Qc, Qd). 
This signal was used to increment a mod-6 counter from a 74LS163N. The counter ticks 6 times total. However, instead of counting up to six, it jumps and is forced to its max count 1111 so that the RCO pin will go high triggering the next element. 

The next element is another 74LS163N counter that, when incremented, increases the speed of the game. This counter increases the game speed twice and then holds at that final speed forever. The outputs of this counter are decoded using combinational logic to trigger a 74LS153 4 to 1 Selector/Multiplexer.

The MUX has three input signals which are the three different speeds the game operates on. Three clock signals were used: 1 The system clock (full speed), 2 divide-by-2 clock speed, 3 divide-by-four clock speed. The two 'divide-by' signals were generated from the appropriate outputs of a counter driven by the system clock. 

The MUX clock speed selection determines the game speed. This clock speed is fed back into the entire game so all the elements operate on the same tempo. 
