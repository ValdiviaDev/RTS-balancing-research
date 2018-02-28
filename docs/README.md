My name is David Valdivia and I'm a student from the video games design and development degree at the Polytechnic University of Catalonia. In this website I'm going to be explaining the importance of balance in RTS video games (real time strategy games), which are the most important aspects to take in account in this subject, and some methods to reach the goal of balancing an RTS game.

Game balance is the concept and action of shaping a game’s rules with the object to make this game’s rules and systems effective. Game balancing is a really important aspect to take in account both in board games and in video games, because an unbalanced game; in other words, a game with poor and/or unfair mechanics and systems; is a boring game to play, at its best; and a frustrating and unfair game to play, at its worst.

Of course, this is no different to real-time-strategy ([RTS](https://en.wikipedia.org/wiki/Real-time_strategy)) video games. Balance in these types of games is extremely important because they are, as its name says, video games where the player has to ideate a strategy to complete a level or scenario, in individual 1 player RTS video games, and ideate an even more intricate and complex strategy to beat a human rival in competitive RTS video games.

In this research document I’ll be explaining some useful methods to make a balanced RTS video game, taking in account the most important systems and elements to balance in this genre. This systems that I’ll be tackling are; the unit system, technology trees (tech trees for short), artificial intelligence, and maps or stages.

# Unit balancing

Units and unit management is one of the core components of any RTS video game. To make the combat in RTS games engaging, it is important to have a balanced roster of units. Without a good unit balance, the strategy part of a real strategy game would fall flat, and the game would not feel as a strategy game, but something like a construction simulation game with units that eliminate each other.

A really good way to design a balanced set of units in a strategy game, is to use intransitive mechanics. Intransitive mechanics consist on having a confrontation between three types of entities that contrarrest each other. To put it simple, it’s the same as with rock-paper-scissors: we have three types of entities, consisting of rock, paper and scissors; and these entities counteract each other: rock wins scissors, scissors wins paper and paper wins rock.

This mechanic in an RTS game allows us to have a dynamic approach to combat, as well as being easier for a designer to balance a combat unit set. But of course, an RTS video game is not as simple as rock-paper-scissors, as there are more parameters to take in account, like the cost of each unit, its health or the damage it does.

But let’s talk about rock-paper-scissors first, to start simple. We could compose a small table consisting of these three entities; being “R”, “P” and “S”, our rock, paper and scissors, and our rival’s being “r”, “p” and “s”. The results of the table show our outcome in the game, given any of these nine possible situations. If we interpret the results of this table as points, for winning a game, we would obtain + 1 point, for losing -1 points, and for a tie we would obtain 0 points. Of course, this same table for our rival would be symmetrical, as they would obtain 1 point if we lost and -1 when if we won.


<table>

<tr>
<td></td>
<td>r</td>
<td>p</td>
<td>s</td>
</tr>

<tr>
<td>R</td>
<td>0</td>
<td>-1</td>
<td>1</td>
</tr>

<tr>
<td>P</td>
<td>1</td>
<td> 0</td>
<td>-1</td>
</tr>

<tr>
<td>S</td>
<td>-1</td>
<td>1</td>
<td>0</td>
</tr>

</table>

Taking this table, and treating the outcomes of each game as points, we could treat “r”, “p” and “s” as probabilities and calculate which are the best options we have against an opponent’s strategy if we consider these set of three equations.

**R = 0 * r + (- 1) * p + (+ 1) * s**

**P = (+ 1) * r + 0 * p + (- 1) * s**

**P = (- 1) * r + (+ 1) * p + 0*s**

simplifying,

**R = s - p**

**P = r - s**

**S = p - r**

**STUFF MISSING HERE**

You can find and edit (if you download it) a table that utilizes this last method explained in this [thread](https://www.gamedev.net/forums/topic/685693-rts-unit-balance/?tab=comments#comment-5329035). The table has been done by the user of this forum named "HappyCoder".

You can find an extensive explanation on how intransitive mechanics work and how to apply them to RTS and other types of games [here](https://gamebalanceconcepts.wordpress.com/2010/09/01/level-9-intransitive-mechanics/).

You can also find some more calculations about unit costs, taking in account more abstract unit parameters like speed and range in this [thread](http://zero-k.info/Forum/Thread/22670?page=1) of this [Zero-K forum](http://zero-k.info/Forum/). Calculations and graphics made by the user of the forum named "Brackman".


# Technology trees and build order

# AI

# Map structuring
