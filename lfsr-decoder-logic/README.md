# LFSR + decoder logic
This is the logic that decides which column to spawn rocks in.

![LFSR Diagram](Falling_Lights_example.png)

The schematic shows the LFSR being decoded by a 3-to-8 decoder. 3 of 4 taps are used on the LFSR so the falling rocks have a longer sequence (see below). The decoder "chooses" a column (shift register) to send a rock down on each clock cycle. The image shows 2 of 8 shift registers, column F5 and column F7 (for demonstration purposes). The image demonstrates an example of the overall function and logic of the falling rocks - not the full game.

The decoded sequence is as follows:

<img alt="LFSR Sequence" src="Decoded_Sequence.png" width="20%" height="20%"> 
