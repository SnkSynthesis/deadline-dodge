# LFSR + decoder logic
This is the logic that decides which column to spawn rocks in.

![LFSR Diagram](Falling_Lights_example.png)

The schematic shows the LFSR being decoded by a 3-8 decoder. 3 of 4 taps are used on the LFSR so the falling rocks have a longer sequence, (See (See [LFSR_Sequence.png](LFSR_Sequence.png).)
). The decoder "chooses" a shift register column to send a rock down on each clock cycle. The image shows 2 of 8 shift registers, column F5 and column F7, (for the purpose of the example). The image demonstrates an example of the overall function and logic of the falling rocks - not the full game.
