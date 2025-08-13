# Speed Logic

This circuitry controls the speed of the [lfsr-decoder-logic](../lfsr-decoder-logic/) and, in turn, how fast the rocks fall in the game. It is a modular feature that introduces three distinct speed levels.

When the player survives for a set amount of time without triggering any collision (i.e., without losing), the speed logic increases the speed at which rocks spawn and fall and making the game progressively harder.

## Operation

### Triggering the Speed Increase
An AND gate detects the LFSR state 1111 (inputs: Qa, Qb, Qc, Qd), which occurs at regular intervals. This output increments a mod-6 counter (74LS163N). Although the counter is designed to count up to 6, it is forced to jump to its maximum count (1111) in order to set the RCO pin high, triggering the next stage. The mod-6 counter was an arbitrary choice, which makes the game speed increase after the LFSR has reached state 1111, six times. 
#### How the counter works 
The counter begins it count at 0001 and continues its count through 0011, at which time the LOAD-condition-NAND gate goes Low and triggers the LOAD making the counter jump to count 1100, (see [Timing Diagram For Jump](./Timing_For_Jump.png)). Then the counter continues its count. The counter's RCO pin goes high when the counter reaches 1111 and rolls over. The RCO pin triggers the next stage.  

### Speed Level Control
The next stage is another 74LS163N counter. Each time the RCO pin goes high on the previous stage, this counter is incremented and the game speed increases. Once the second-stage-counter is inremented it must wait for the first-stage-counter's RCO pin to go high before it increments again. See [RCO Speed Increase Diagram](./RCO_Speed_Increase_Diagram.png). After two speed increases, this counter continues to count up, but combinational logic downstream makes all counts 0010 and above lock the game at its highest speed setting. 

### Speed Selection and Distribution
The counter’s outputs are decoded with combinational logic to control a 74LS153 4-to-1 multiplexer (MUX).

The MUX selects between three clock inputs:
System clock (full speed),
Divide-by-2 clock,
Divide-by-4 clock.
The two divided clocks are generated from specific outputs of a counter driven by the system clock.

The MUX output determines the active game speed. This clock signal is fed back into the entire game so all elements operate in sync with the selected tempo.
