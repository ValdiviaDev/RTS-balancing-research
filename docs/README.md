My name is David Valdivia and I'm a student from the video games design and development degree at the Polytechnic University of Catalonia (UPC), in the sub-delegation of the universitiiy called [CITM](https://www.citm.upc.edu/). In this website I'm going to be explaining the importance of balance in RTS video games (real time strategy games), which are the most important aspects to take in account in this subject, and some methods to reach the goal of balancing an RTS game.

Game balance is the concept and action of shaping a game’s rules with the object to make this game’s rules and systems effective. Game balancing is a really important aspect to take in account both in board games and in video games, because an unbalanced game; in other words, a game with poor and/or unfair mechanics and systems; is a boring game to play, at its best; and a frustrating and unfair game to play, at its worst.

Of course, this is no different to real-time-strategy ([RTS](https://en.wikipedia.org/wiki/Real-time_strategy)) video games. Balance in these types of games is extremely important because they are, as its name says, video games where the player has to ideate a strategy to complete a level or scenario, in individual 1 player RTS video games, and ideate an even more intricate and complex strategy to beat a human rival in competitive RTS video games.

In this research document I’ll be explaining some useful methods to make a balanced RTS video game, taking in account the most important systems and elements to balance in this genre. This systems that I’ll be tackling are; the **unit system**, **technology trees** (tech trees for short), **artificial intelligence**, and **maps or stages**.

If you are new to the genre and want to learn about the RTS genre and what is all about I encourage you to read this [article](https://waywardstrategist.com/2015/09/25/what-is-an-rts-game/). 

# Unit balancing

Units and unit management is one of the core components of any RTS video game. To make the combat in RTS games engaging, it is important to have a balanced roster of units. Without a good unit balance, the strategy part of a real strategy game would fall flat, and the game would not feel as a strategy game, but something like a construction simulation game with units that eliminate each other.

## Intransitive mechanics and Rock-Paper-Scissors

A really good way to design a balanced set of units in a strategy game, is to use intransitive mechanics. Intransitive mechanics consist on having a confrontation between three types of entities that contrarrest each other. To put it simple, it’s the same as with rock-paper-scissors: we have three types of entities, consisting of rock, paper and scissors; and these entities counteract each other: rock wins scissors, scissors wins paper and paper wins rock.

<img src="Images/UnitBalance/RockPaperScissors.png" width="400">

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

<img src="Images/UnitBalance/IntransitiveRTS.png" width="400">

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

One of the methods for calculating the payoff table taking these two parameters in account, (HP and damage) is to take the damage per second (DPS) that every unit would do to another unit, intead of the damage it would be done by the unit taking in account this unit alone. To put an example, a ground melee unit may do 40 units of DPS to another ground unit, but 0 to an aerial unit. In this case we could have this three types of dps:

* Heavy DPS: against ground melee units
* Light DPS: against ground long range attack units
* Aerial DPS: against aerial units

The “additional damage index” that I talked about earlier can be calculated by dividing the adient DPS with the contrary unit’s hp. If we call our unit "A", and the rival's unit "B", these would be the formula for calculating this index:

**addit. dmg index = A dps / B hp && addit. dmg index = A dps / B hp**

So in order to calculate the payoff for the table it would be better to use this formula:

### payoff = B cost(A dps/B hp) - A cost(B dps/A hp)

This table would give the same results in the probability calculations, as they did before, but using the formula from avobe.
/////////////////////DO THIS
<table>

<tr>
<td>Unit</td>
<td>Cost</td>
<td>HP</td>
<td>Heavy DPS</td> 
<td>Light DPS</td> 
<td>Aerial DPS</td> 
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

***You can find and edit (if you download it) a table that utilizes this last method explained in this [thread](https://www.gamedev.net/forums/topic/685693-rts-unit-balance/?tab=comments#comment-5329035). The table has been done by the user of this forum named "HappyCoder". This a really good table to use if you need to balance your units.***


### Other aspects to take in account

I've calculated the payoff table having only one cost, but in almost any RTS there's more than one parameter to consider when scouting a unit. These different parameters could be for example; gold, wood and oil; like in the 1995 [Blizzard](https://www.blizzard.com) game, [Warcraft II](https://en.wikipedia.org/wiki/Warcraft_II:_Tides_of_Darkness).
In this case, we should assign a **rarity index** to every  one of these three resources. A rarity index of 1 should be assigned to the most common resource of the game, and a index going from 1 to 2 to the more rare resources.
Let's say we only have these three resources to consider. I'll call them **a**, **b** and **c**; and I'll call every rarity index as the recource + RI. With this we can extrpolate this fromula for calculating a total unit's cost:

**cost =  a * aRI + b * bRI + c * cRI**

I'll talk more in depth about this aspect of an RTS [later](https://valdiviadev.github.io/RTS-balancing-research/#technology-trees-and-build-order).

Another important aspect that I didn't consider when making the **probability calculations** is that I only calculated them when we just had a payoff table of three units, (swordsman, gunman and flying machine) but these three units are just the tree unit types that we would be using a real RTS game. As you can see in the [table](https://www.gamedev.net/forums/topic/685693-rts-unit-balance/?tab=comments#comment-5329035) that I talked about before, there can of course be, more than three units on the payoff table, each one with its corresponding unit type. There could be two types of **probability calculations** that could be made:

* If you wanted to calculate every probability for every unit, you'd just have to calculate the probabilites for every one of the units. It is very useful to see how a theoretical RTS game in the making would be shaping up , but it is an extremely long calculation. For using it during the development of a game, it would be useful to implement an algorithm that made those calculations for you.

* If you wanted to calculate how good is every one of these three types, you would just need to sum upp all the payoffs of every unit with the ones of their same type, and then make the probability calculations.

As a reminder, these are the equations you should use for making the probability calculations (if taking in account three units, calling them "A", "B" and "C"):

     A = (payoff A_c)*c + (payoff A_b)*b
     B = (payoff B_a)*a + (payoff B_c)*c
     C = (payoff C_b)*b + (payoff C_a)*a
     A = B = C = 0
     a + b + c = 1

To finish with the unit balancing, I need to indeicate thet I've only taken in account really tangible parameters of a unit, like its HP or DPS, but there are other more intangible parameters to consider when balancing units, like their **speed** or **range**. One way of telling which range and speed a unit should have could be by commmon sense. For example, a more powerful unit in damage should be slower, or have less range; but you can also make some modifications to the formula I explained before. 

***You can find some more calculations about unit costs, taking in account these more abstract unit parameters in this [thread](http://zero-k.info/Forum/Thread/22670?page=1) of this [Zero-K forum](http://zero-k.info/Forum/). Calculations and graphics are made by the user of the forum named "Brackman".***

***You can also find an extensive explanation on the first part of this section, on how intransitive mechanics work and how to apply them to RTS and other types of games [here](https://gamebalanceconcepts.wordpress.com/2010/09/01/level-9-intransitive-mechanics/).***

## Interpreting the probability calculations

It’s not always a good thing to have a game in perfect balance. A lot of unbalance makes a game frustrating and unfair, but a perfect balance makes a game stale. In the case of competitive games, this can turn off experienced players because of the stagnant nature the game would have adopted; and unexperienced players wouldn't addapt to the game's [meta game](https://en.wikipedia.org/wiki/Metagaming), because of really grounded strategies in this meta, that wouldn't let room for someone new to learn the basics. So when balancing units, it maybe isn't the most effective balance strategy to just make them perfectly balanced. 

So when a designer calculates the probabilities on how useful every unit or type of unit would be, they shoudn't attempt to make them perfecty equal, but to try and see which implications would cause some small inbalance in the numbers of the probability calculations.

Here you can watch a video from _Extra Credits_ in which they explain this concept more in depth.

<iframe width="560" height="315" src="https://www.youtube.com/embed/e31OSVZF77w" frameborder="0" allowfullscreen></iframe>


# Technology trees and build order

The first thing to take in account when building a tech tree are the elements that compose it:

* Buildings
* Units
* Upgrades
* Other

# AI

# Map structuring

When balancing maps and how they should be structured in RTS games, the first thing to take in account is that when balancing maps from a competitive RTS videogame, it is very different to balance a map from a 1 player campaign mode, or a game that is strictly a 1 player RTS video game. Another thing to take in account is that, unlike previous sections, we are not working with numbers, but with the construction of a graphical terrain, so there wont be really precise methods or formulas for balancing a map. With all that said, let's start with the balance in competitive maps.
 
## Competitive Games

When making a competitive map for an RTS game there is one basic principle to take in account, and a principal pillar to return to, when struggling to make a map structuring decision:

* Symmetry

The most simple, yet most effective way to make a balanced RTS map for a competitive game is to make it symmetrical. It is very ovbious that a non-symetrical map can be extremly unbalanced, as one player would have advantage over the other in certain areas, like for example the traversing of the map being easier, or one player having more recouces to its disposition than the other.

As an example for explaining how an RTS competitive map should be, I'll be using the a Starcraft 2's map named [Blistering Sands](http://liquipedia.net/starcraft2/Blistering_Sands).

<img src="Images/Maps/Blistering_Sands11.jpg" width="800">

Of course, not everything in the map should be symmetrical, as it would beacame stale very quickly if it was this way, but the two main things to make symmetrical in a competitive map are:

* Gameplay elements
* Structure

These two aspects of the map need to be symmetrical, as I commented earlier, to avoid one player of having avantage over the other. As it can be seen in the image below; the two player's bases, the recouces' positions (minerals and gas geysers) and even the observatories that get crossed by the divisory line, are completly symmetrical.

<img src="Images/Maps/Blistering_Sands3.png" width="400">

As I mentioned earlier, not everything in a competitive map must be 100% symetrical. The one aspect of a map that can not, and shouldn't be symmetrical are **non gameplay elements**, like **textures or backgrounds**. When making these elements of the stage non-symetrical, you make sure that the map dosen't feel as artificial as its symmetry makes it feel. As we can see marked in green in the Blistering Sands map, the backrounds for the two sides are not the same; and although the stage's structure is the same, if looked closely, it can be observed that there are small deformations in the terrain that vary from one part of the scenary to the other.

<img src="Images/Maps/Blistering_Sands5.png" width="400">

Aside of making the map symmetrical in order to not give an advantage to one player over the other, when designing a competitive level, the designer of the map should set the recources in a certain way that the players are encouraged to slowly go towards each other. It is also important that these paths that the players are encouraged to take are divesre; in other words, there should be more than one way in which the players should encounter each other and engage in combat.

As it can be seen in the map, the resources of the game are disposed in a way that the player is encouraged to consequently set second and third bases where these resources are disposed in the map. This way of guiding the player and making them improve and **progress** is the main pillar for making a 1 player RTS map, that it is explaned [later](https://valdiviadev.github.io/RTS-balancing-research/#1-player-campaign) on this document.

<img src="Images/Maps/Blistering_Sands6.png" width="400">

There's not only one path in which the players can set their second and third bases, as they could go for the [rich mineral field](http://liquipedia.net/starcraft2/Rich_Mineral_Field) instead of the normal one to construct their third base. This could be considered a more risky option to take, as there's more probabilities that the rival would also want to go for the rich mineral field, thus making them confront early on, for the conquest of that field. Again, this is one of some of the posibilities for the two players to clash in this map. When designing a map, there should be taken in account several options that the players could carry out, and how a clash of strategies from both players would make them have to constantly addapt their strategy.

<img src="Images/Maps/Blistering_Sands7.png" width="400">

For achieving succesfully the crafting of a map, the most useful tools to use are **squetches** and **schemes**. Squetches are incredibly important to assure that the map and gameplay elements of the map are symmetrical, and for drawing the possible paths that players could take, like I've done in the last two photos. Schemes are mostly useful for this second part, as if you have a drawing or diagram with too much arrows and numbers it can become extremely confusing. 

This concept is really well explained in [this](https://waywardstrategist.com/2015/06/07/time-as-a-resource-part-2-multiplayer-map-design/) article about different ways of making map design in an RTS.

### Examples

## 1 player campaign

The main basic pilar to make a 1 player campaign for an RTS work is that of:

* Progression

Unlike maps for competitive modes that need to be symmetrical to avoid unbalance on any match of the game, 1 player RTS games or campaigns need to focus on the basic principle of progression. The player needs to feel that they improve in the level and that they are becoming better at conquering the game, although it may just be that the way of the designers of guiding the player through a level, is done in such a way that the player thinks that all the progression made in the level is thanks to their own skill. Of course, in every balanced game, the player becomes better thanks to the careful and non intrusive guidance that the game offers, linking up to the concept of player progression; but this is more of a general video game balancing aspect, than one of RTS maps.

### Examples

To explain more in detail how to make feel that the player progresses in the game through the map, I'm going to explain some examples from Blizzard's 1995 game, Warcraft 2.

[Here](http://www.ultimaratioregum.co.uk/game/tag/rts/) you can find an article that puts various examples of interesting ways that Command & Conquer aproaches their 1p levels.

You can find [here](https://waywardstrategist.com/2015/05/26/time-as-a-resource-part-1-single-player-map-design/) an article about balancing the progression in RTS maps, taking in account time as a gameplay component.


