My name is David Valdivia and I'm a student from the video games design and development degree at the Polytechnic University of Catalonia. In this website I'm going to be explaining the importance of balance in RTS video games (real time strategy games), which are the most important aspects to take in account in this subject, and some methods to reach the goal of balancing an RTS game.

Game balance is the concept and action of shaping a game’s rules with the object to make this game’s rules and systems effective. Game balancing is a really important aspect to take in account both in board games and in video games, because an unbalanced game; in other words, a game with poor and/or unfair mechanics and systems; is a boring game to play, at its best; and a frustrating and unfair game to play, at its worst.

Of course, this is no different to real-time-strategy ([RTS](https://en.wikipedia.org/wiki/Real-time_strategy)) video games. Balance in these types of games is extremely important because they are, as its name says, video games where the player has to ideate a strategy to complete a level or scenario, in individual 1 player RTS video games, and ideate an even more intricate and complex strategy to beat a human rival in competitive RTS video games.

In this research document I’ll be explaining some useful methods to make a balanced RTS video game, taking in account the most important systems and elements to balance in this genre. This systems that I’ll be tackling are; the unit system, technology trees (tech trees for short), artificial intelligence, and maps or stages.

# Unit balancing

Units and unit management is one of the core components of any RTS video game. To make the combat in RTS games engaging, it is important to have a balanced roster of units. Without a good unit balance, the strategy part of a real strategy game would fall flat, and the game would not feel as a strategy game, but something like a construction simulation game with units that eliminate each other.

## Intransitive mechanics and Rock-Paper-Scissors

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

**P = (- 1) * r + (+ 1) * p + 0 * s**

simplifying,

### R = s - p

### P = r - s

### S = p - r

This equations allow us to calculate which would be the best strategy against an opponent. For example, let’s say that a set of options for a rival is 1 (**r + p + s = 1**). If an opponent threw scissors two times (**s = 2/4**) more than they threw rock (**r = 1/4**) or paper (**p = 1/4**), we would be able to tell that the best strategy against them is to always throw rock (**R**), as this has a payoff of 1/4, having the other two options a payoff of 0 (**S**)  and -1/4 (**P**), choosing to throw paper, being actually harmful to our playstyle. The payoff of every equation represents the utility of each element and how often it should be used for an optimal playstile. It is for this reason that in this specific case, paper should be never used, as it payoff is a negative number.

But, let’s say we assume that in our game strategy for rock-paper-scissors we try to not stick too much to one of these three options as the three of them are perfectly valid, so we use rock, paper and scissors an equal amount of times. This would mean that any of our three options in the game has the same probability of winning or losing if our opponent acts the same way. This can be represented mathematically simply by equalizing our three options in this fashion: **R = P = S**.

In rock-paper-scissors and in any type of [zero-sum games](https://en.wikipedia.org/wiki/Zero-sum_game), the payoff for any play will always be zero. In other words, if we throw paper and our opponent throws scissors, we will have a score of “- 1”, and they will have a score of “+ 1”. If we calculate the payoff of the play, this would be: “(-1) + (+1)”, resulting in 0. This payoff will always be zero in any game of rock-paper-scissors in which we engage, because of this game’s nature. This means that any choice we take in rock-paper-scissors will ultimately finish in an aftermath of 0. We could express this using the same formula as before: **R = P = S = 0**.

As said earlier, considering that a set of options for our rival is equal to 1, and if we also consider the possibilities of our opponent throwing one of these three elements, what we know for sure is that they have a 100% chance of throwing one of these three elements. This could be represented mathematically as:
**r + p + s = 1**.

So taking in account these equations:

### R = P = S = 0

### r + p + s = 1

We can calculate the probabilities on how often they will use any element:

R = 0 = s - p -> **s = p**

P = 0 = r - s -> **r = s**

S = 0 = p - r -> **p = r**

Having r = p and r = s, and taking in account that r + p + s = 1, we can make a substitution in the equation so:

r + r + r = 1

3r = 1 -> **r = 1/3**

And as we know that r = s = p,

**p = 1/3**

**s = 1/3**

As this results show, the most probable strategy that the opponent will take will be to throw rock, paper and scissors an equal amount of times. This is pretty obvious as we use the same exact strategy, and it is intuïtive to adopt this strategy in this game, as it is the most unpredictable; but as we have more complex parameters in an RTS game than in rock-paper-scissors, this set of equations will be very useful to balance our game.

## Intransitive mechanics applied to an RTS game

Following with balancing an RTS, we should first define our three choices, or in this case types of units. What most RTS games do is have a melee attack ground type unit, a long range attack ground type unit, and an aerial type unit that attacks mid-distance. In our case let’s say we have swordsmen, gunmen and flying machines. Swordsmen defeat  gunmen, gunmen defeat flying machines and flying machines defeat swordsman.

*PHOTO*

In this case we will not work with points, but with **unit costs**. Every unit will have its cost, and an **additional damage index** will also be included to each unit. This index damage is the damage ratio a unit does, when it engages its counter unit. Let’s put it this way; a unit that is counteracted by another unit can attack the other unit, but it does less damage than the unit that is being counteracted by. Let’s say that a gunman has an additional damage index of 0.3 against a swordsman because of the damage it does when the swordsman is approaching it; a flying machine has an additional damage index of 0.5 against a gunman because of the damage the ship does to the gunman before being destroyed; and the swordsman has an index of 0, because a swordsman can’t attack an aerial unit. The cost of the unit is, of course, the cost that the player needs to create this unit; it can be represented in game as gold, wood, crystals; or whatever the designers find more suitable.

I'll put these values to the parameters we now have; and I will treat these three types of units as units on their own, for now.

<table>

<tr>
<td>Unit</td>
<td>Cost</td>
<td>Addit. dmg index</td>
</tr>

<tr>
<td>Swordsman</td>
<td>40</td>
<td>0</td>
</tr>

<tr>
<td>Gunman</td>
<td>60</td>
<td>0,3</td>
</tr>

<tr>
<td>F. Machine</td>
<td>80</td>
<td>0,5</td>
</tr>

</table>


I will now be calculating each cost of each unit respect of the unit it confronts. As we've seen with rock-paper-scissors, a negative cost in the cost table means that a unit wins against another unit, an so on. To calculate the costs I'll be subtracting the costs of every unit like this: **Rival unit's cost - player unit's cost**. The additional damage index will be multiplied to the rival cost, where it can be applicable.

So, after explaining these two concepts, let’s dive straight into what we will call from now on the **payoff table**, and the **probability calculations**.

<table>

<tr>
<td></td>
<td>s</td>
<td>g</td>
<td>f</td> 
</tr>

<tr>
<td>S</td>
<td>40 - 40</td>
<td>60 - (40 * 0,3)</td>
<td>(0 * 80)  - 40</td> 
</tr>

<tr>
<td>G</td>
<td>(40 * 0,3) - 60</td>
<td>60- 60</td>
<td>80 - (60 * 0,5)</td> 
</tr>

<tr>
<td>F</td>
<td>40 - (0 * 80)</td>
<td>(60 * 0,5) - 80</td>
<td>80 - 80</td> 
</tr>

</table> 

-> 

<table>

<tr>
<td></td>
<td>s</td>
<td>g</td>
<td>f</td> 
</tr>

<tr>
<td>S</td>
<td>0</td>
<td>48</td>
<td>- 40</td> 
</tr>

<tr>
<td>G</td>
<td>- 48</td>
<td>0</td>
<td>50</td> 
</tr>

<tr>
<td>F</td>
<td>40</td>
<td>- 50</td>
<td>0</td> 
</tr>

</table>

    S = 0 * s + (+48) * g + (-40) * f 
    G = (-48) * s + 0 * g + (+50) * f
    F = (+40) * s + (-50) * g + 0 * f

    S =  48g - 40f
    G = - 48s + 50f
    F = 40s -50g
    S = G = F = 0
    s + g + f = 1

    S = 0 = 48g - 40f -> 48g = 40f -> 6g = 5f
    G = 0 =  - 48s + 50g -> 48s = 50f -> 24s = 25f
    F = 0 = 40s -50g -> 40s = 50g -> 4s = 5g

    s + g + f = 1
    f = 24/25s
    g = 4/5s
    s  + 4/5s + 24/25s = 1
    69/25s = 1 -> s = 25/69 ≈ 0,36
    f = 600/1725 -> f = 8/23 ≈ 0,35
    g = 100/345 -> g = 20/69 ≈ 0,29

From the results of the probability calculation, it can be extrapolated that our theoretical RTS video game would actually be fairly balanced, being the three probabilities of the opponent utilizing the units rounding the 1/3, that as we’ve found with rock-paper-scissors, is the ideal rate for having a balanced game. The unit or unit type that would be most underutilized in this hypothetical RTS game would be  the gunmen. If the designer of this game prefered to make gunmen a more relevant unit, they would likely have to decrease the unit’s cost or additional damage index. 

This method is the base of balancing a game with intransitive mechanics, but RTS video games have more depth than just costs and what I've called “additional damage index”, that isn’t a real parameter that this type of games have. Aside from the unit cost, the most tangible variables of a unit to take in account are its life points or health points (HP), and the amount of damage it does, in other words, how strong this unit is.

One of the methods to calculate the payoff table taking these two parameters in account, (HP and damage) is to take the damage per second (DPS) that every unit would do to another unit and not the damage it would be done by the unit taking in account this unit alone. To put an example, a ground melee unit may do 40 units of dps to another ground unit, but 0 to an aerial unit. In this case we could have this three types of dps:

* Heavy dps: against ground melee units
* Light dps: against ground long range attack units
* Aerial dps: against aerial units

The “additional damage index” that I talked about earlier can be calculated by dividing the adient dps with the contrary unit’s hp. If we call our unit "A", and the rival's unit "B", these would be the formula for calculating this index:

**addit. dmg index = A dps / B hp && addit. dmg index = A dps / B hp**

So in order to calculate the payoff for the table it would be better to use this formula:

### B cost(A dps/B hp) - A cost(B dps/A hp)

<table>

<tr>
<td>Unit</td>
<td>Cost</td>
<td>HP</td>
<td>Heavy dps</td> 
<td>Light dps</td> 
<td>Aerial dps</td> 
</tr>

<tr>
<td>Swordsman</td>
<td>40</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>0</td>
</tr>

<tr>
<td>Gunman</td>
<td>60</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
</tr>

<tr>
<td>F. Machine</td>
<td>80</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
</tr>

</table>


////////////////////////////////////////

But it’s not always a good thing to have a game in perfect balance. A lot of unbalance makes a game frustrating and unfair, but a perfect balance makes a game stale. In the case of competitive games, this can turn off experienced players because of the stagnant nature the game has adopted, and also unexperienced players that can't addapt to the competitive, because of really grounded strategies, that they don’t let room for someone new to learn the basics. So when balancing units, it’s not the most effective to just make it perfectly balanced, but to try and see the importance of the unbalance in balanced games. 

Here you can watch a video from extra credits where they explain this concept in more depth.

<iframe width="560" height="315" src="https://www.youtube.com/embed/watch?v=e31OSVZF77w&feature=youtu.be" frameborder="0" allowfullscreen></iframe>





////////////////////////////////////////

You can find and edit (if you download it) a table that utilizes this last method explained in this [thread](https://www.gamedev.net/forums/topic/685693-rts-unit-balance/?tab=comments#comment-5329035). The table has been done by the user of this forum named "HappyCoder".

You can find an extensive explanation on the first part of this section, on how intransitive mechanics work and how to apply them to RTS and other types of games [here](https://gamebalanceconcepts.wordpress.com/2010/09/01/level-9-intransitive-mechanics/).

You can also find some more calculations about unit costs, taking in account more abstract unit parameters like speed and range in this [thread](http://zero-k.info/Forum/Thread/22670?page=1) of this [Zero-K forum](http://zero-k.info/Forum/). Calculations and graphics made by the user of the forum named "Brackman".

# Technology trees and build order

The first thing to take in account when building a tech tree are the elements that compose it:

* Buildings
* Units
* Upgrades
* Other

# AI

# Map structuring
