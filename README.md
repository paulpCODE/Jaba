# Jaba

You are to develop in Java a board game between two players, the White and the Black. 
The board consists of four “Houses” (H1, …, H4), which are common to both players and are initially empty. The players play interchangeably and you may consider that the White always plays first. Every time a player plays, a random number from 1 up to 15 is generated and the player decides on which House to place the number with the aim of completing a sum of the 31 in the House. 
When a player places the number on a House and completes a sum of 31 in the House, the House becomes empty, the player gains 50 points, and the game continues (Fig. 1). If the player cannot complete a 31 in a House, they place the number in whichever House they wish and the game continues (Fig. 2). Finally, if the number is placed on a House where the sum of 31 is exceeded, the House becomes “closed” from this point on and can no longer be used in the game. Note that, ideally, a player should not be allowed to close a House if they have another option, i.e. another House where 31 is not exceeded. 
The game finishes when all Houses are “closed” and the winner is the player with the most points.
