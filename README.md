# Dice-game
//this is a school project for UC Davis do not reuse for the purpose of plagiarising, this should be a learnign to and go 
//ahead and play with this program as long as its not summited for a grade.

//also U need Quartos in order to be able to properly open this files. I recommend to create a new project and the open this files after wards instead of just drag and drop in existing project since it might not work. 


/*
fallowing are the guidelines of the project

UNIVERSITY OF CALIFORNIA, DAVIS
Department of Electrical and Computer Engineering
EEC180A
DIGITAL SYSTEMS I
FALL
2018
LAB 6: DESIGNPROJECT: 15
Objective:
In this lab, you will design a die game called 15. The object of the game is to score 
exactly 15points in as few rolls of the die as possible. After each roll, the player can choose to 
add the current die value to his or her score or not, unless the die value is six, in which case it 
is automatically added to the player’s score. If the player’s score exceeds 15, the player loses. If the 
player’s score is equal to 15, the player wins. Play continues until the player reaches or exceeds 15 points.

Determine the chips you will use for the data path, or more specifically, the Adder, Score 
register and the 
Turn counter.DescriptionTo start the game, the playerresets the system using the reset switch.The score will be set to 
zero and both the Win and Lose LEDs will be turned off.The player then rolls the die byplacing the Rb switch in
the Roll position. The die counter should operate with a clock frequency of 50 MHz so that the player cannot controlthe outcome of a roll. After about a second or more, the player
restores the Rb switch to its off positionto end the roll. (You can use a pushbutton or a slideswitch for Rb. However, it is important that the switch is debounced. 
The slide switches on the DE10-Lite board are notdebounced.)The Turn Counter should be incremented to indicate that the player has taken aroll. 
If the player rolled a six, it is automatically added to his or her score.Otherwise, the player can togglethe Add 
switchto add thedie value to his or her score or the player can toggle the Pass switchto leave the score unchanged. After each roll, the score will 
be greater than, less than or equal to 15. If the score is equal to 15, the player wins –the Win LED should be turned on 
and remain on until the system is reset for a new game. If the score is greater than 15, the player loses –the Lose LED should be turned on and remain on until the 
system is reset. Once the player has won or lost, the player cannot roll the die again until the 
system is reset. (The Rb switch willnot have any effect in these states.) If the score is less than 15, the player will roll again. After each roll, the player 
toggleseither the Add switchor the Pass switch(unless a six is rolled) before the die can be rolled again. Play continues until the player’s score equals or exceeds 15.
Ablock diagram of the system is shown in Figure 1 and a flowchart is given in Figure 2. 



Logic / 7-segment Displays1-to-6 Die CounterAdderScore RegisterDisplay(LEDs)ControlRollReset switchRb switchAdd switchPass switchLED
LED50 MHz ClockLoadWinLoseTurn CounterEnableLogic / 7-segment DisplaysClockClockClockSix
Figure 1. Block diagram of die gameIncrement Turn Count6
Pass
Add
Load new 
score
>
15
=
15
Lose
Win
N
N
N
Y
Y
Y
Y
N
Roll Die
Y
N
Figure 2. Flowchart for die game
Design 
Requirements
1.
Use the counting sequence assigned to you 
in the previous lab
for your die. The die circuit 
must only operate in the proper states in this game. For example, a player cannot roll a
gain 
after a roll until either the Add or Pass button is 
toggled
, unless a six is rolled. Also, the player 
cannot roll the die when the Win or Lose indicator is on. Therefore, your counter circuit from 
the previous lab
will need to be linked to your new st
ate machine for this game. 
Display
the 
die output on one of the seven
-
segment displays, such as HEX0.







2.
All
clocked devices such as flip
-
flops and counters must use the same system clock, which will 
operate  at  50  MHz. The clock signal cannot be “gated”. Tha
t is, a single clock must directly 
clock all flip
-
flops and counters in the circuit. 
3.
The  Reset,  Rb,  Add  and  Pass  switch  inputs  must  be 
synchronized
to  the  system  clock  in 
order to prevent race conditions and to reduce the risk of metastability. You can a
ssume that 
the   activ
e
-
low   pushbutton   switches,   KEY[1
..
0],   are   bounceless   since   the
y   have   been 
debounced  on  the  DE10
-
Lite
board 
using  a  Schmitt  trigger  circuit.  However  the  SW[]  slide 
switches are 
notdebounced.
4.
Display  the  number  of  turns in decimalon  two  7
-segment  displays.  You mustbe  able  to display  any  number  of  turns  from  00  to  99.  The  score will
be  displayed  inbinaryon  five LEDs, LEDR[4..0]. You mustdisplay scores up to the highest losing score.
(What is it?)
You also need some kind of display, s
uch as turning on an LED or a seven-segment display, when a  player  either  wins  or  loses  the  game.All  unused LEDs  must  be
turned  off.However,  you can display state information on extra LEDs to help in debugging.
5.
Your game must operate reliably even if the Add and Pass switch inputs are not debounced. For example, there should never be a case in which the same roll of the die is added to the 
player’s score more than once.
6.
Make sure that your game is 
well-behavedwhen Add and Pass are activated
at the sametimefollowing a roll. Based on the flowchart in Figure 2, the Pass switch should have priority over 
the Add switch so that if Pass is pressed, the state machine should transition
directly to a new roll statewithout updating the scoreeven if the Add switch is also pressedsimultaneously. 
7.
Implement your design in a Quartusschematic with
onlythe following components: Basic logic gates (AND, OR, NAND, NOR, NOT, etc.), DFF, DFFE, 7447, 7474, 7483, 74163, 74190, 
WIRE, INPUT, OUTPUT.Demonstrate your working circuit to your TA and have him or her sign your verification sheet.Design Guidelines
1.
Do a careful evaluation of design alternatives. For example, determine if you will 
implement your control circuit as a Mealy or a Moore finite state machine. Also,
determine which state assignment encoding will be optimal from choices such as one-hot, binary or other encodings.Note that using a one-
hot encoding can greatly simplify the design process and the fact that it uses extra flip-flops doesn’t matter since you are 
implementing your design in an FPGA with more than enough resources.
2.
Use LEDs for debugging your design. For example, many of your state register output bits 
can drive an LED so that you always know what state your system is in. Other signals can also be connected to LEDs for debugging purposes.
3.
If your design doesn’t work and you cannot debug it by using LEDs on the state register 
outputs and other signals, you can try manually clocking it with a debounced switch.

4.
You should design and test your system by breaking it into small modules and testing them 
individually, as needed. For example, you might want to test your Die counter circuit from the previous lab and add the decimal Turn counter. As an option, you could also simulate 
your design in ModelSim.
5.
Rememberto import the pin assignments after you add all your input and output components!



*/
