Complete. 
- Create CardGenerator object to init cards.  
- Create Basic Player and Minion cards.  
- Make move method to move card.  
- Make attacDagame and healthPoint.  
- Add Logic that cards follow player card.  
- Add to CardGenerator generate card at empty space.  
- I need a 'turn' how many time player moved. One move add one turn (+1).
- devide up what to do according to Card.state.
- Make a EmptyCard Prefab to make generate function.
- Move Animation
- Create, Disappear Animation
- Minion Die
- Minion Attack
- BushCard
- Bush Effect
- Earn Gold


To-Do. 
  - Finish Skill logic (cooltime, queue etc..)
  - Earn EXP
  - skill
  - more enemy
  - items

## 2019.09.06 Fri
with more and more sources, I need some document that import whole thing about game. It define skills, champs, systems, enemies and so on. like planning document. If not, I forgot everything what should I do.
Today, I will fix the way display skill cooltime. At first, when skill is on cooltime, skill image is to be blur. It notice player it is not ready. And next, I show up skill use count on skill icon image. Riven can use her broken wings 3 times, so we need to show how many time we use and remain.
Actually I was going to emphasize skill is on Active, I didn't. I think, It didn't help player know what skills are able or not.

## 2019.08.30 Fri
Today, I start coding from at 2pm. I need to finish skill system. I'm going to make some animations to attach Player Animator. It will act when PlayerCard attack enemy or use skill. I have an idea to make it. My plan is make two kind of category about animations. one is common animmation, the other one is special animation. Common animation is used in any situation or case. For example, there is a animation that player jump a little, it can be used "jump" and some attackskill, even it can be used in a situation that hit from an enemy. 


## 2019.08.28
Delayed To-Do
2. make queues to check skill before move or attack. (2019.08.23)

To-Do
1. ~~AttackNormalAnimation~~

## 2019.08.23
To-Do
1. ~~playerCard init() method. set Player's champ and sprite image.~~
2. make queues to check skill before move or attack.

## 2019.08.20
1. Complete Skill CoolTime down.

## 2019.08.18
To-Do
1. Finish Skill logic (cooltime, queue etc..) - Delay


## 2019.08.11
1. Finish initSkill. 
2. We need many initiator before start game :(

## 2019.06.27
1. `InitGame()` in CardGanerator.cs make random card {MINION, GOLD, WHITE BUSH}
2. Make a bush effect.
### 3. Render Bush img on Player or set Alpha Value at Player. Which one is better? -> Bush on the Player!

![image](https://user-images.githubusercontent.com/14961794/60269834-292cf880-992a-11e9-8b23-ae3a2b880d63.png)
![image](https://user-images.githubusercontent.com/14961794/60273973-33eb8b80-9932-11e9-8819-86652d8ccc6a.png)

## 2019.06.26
1. ADD BushCard
2. In Bush, Champ get a few HealthPoint and something special bonus. (ex. Champ can attack minion with no counter)

## 2019.06.23
1. RIVEN, MINION IMAGE
2. Change Card Color to More dark. it's better imo.

## 2019.06.20
1. Itembar, Skillbar
2. Need to define skillset for champs

## 2019.06.18
1. Skill 64px, Item 40px
2. Draw outline 4px

## 2019.06.17
1. Make Skill UI and adjust All UI Canvas.

## 2019.06.14
1. Set Random HealthPoint.

## 2019.06.07
1. Make AP(AtackPoint) on Player

## 2019.04.28
1. Make LOOTCARD, WITHECARD, EMPTYCARD
2. NOTE : I NEED TO MAKE CARD LIFE CYCLE

## 2019.04.25
1. Make All animations.

## 2019.04.16
1. Make MoveRightCardAnim and MoveRightEndCardAnim. It can be controlled animator param [Right, Left, Up, Down] 

## 2019.04.14
1. Change CardCube -> CardQuad (Player, Minion)
2. Make MoveAnimation.

## 2019.04.07
1. Change CardObject. Cube -> Quad x 6. Because put different color each side.

## 2019.04.01
1. If minion die, create item card while destroy minion card. 
2. Add Common Animator has CreateSpin Animation and DestroySpin Animation.
3. Minion Die --animation--> Switch SpaceCard -> Player Move

## 2019.03.26
1. I change the cards move system, only one card move per one move turn. I make a List<Card> as queue.  
2. through CardGenerator.AddCard(a Card), I'm able to add card to queue.
3. I define the card state { MOVE, GENERATE, NONE }, In CardGenerate.Update(), it can check Card.state and know what this card to do.

## 2019.03.15
1. Make TextMeshPro.

## 2019.03.14
1. Make CardGenerate function.

## 2019.03.12
1. Make function that let all cards move one direction.


## 2019.03.11
1. Create Super Method __`Card`__. 
2. Two class `PlayerCard` and `Minion` extend `Card`.
3. Now, Card has below list of method.
```C#
protected void Start();
protected void Update();
public void UpdatePositionTag();
public void MoveLeft();
public void MoveRight();
public void MoveUp();
public void MoveDown();
```

<img width="417" alt="스크린샷 2019-03-11 오후 11 52 32" src="https://user-images.githubusercontent.com/14961794/54133071-c25a0100-4458-11e9-8986-3524e46d95c9.png">

