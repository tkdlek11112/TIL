To-Do.  
- Create CardGenerator object to init cards.  
- Create Basic Player and Minion cards.  
- Make move method to move card.  
- Make attacDagame and healthPoint.  
- Add Logic that cards follow player card.  
- Add to CardGenerator generate card at empty space.  
- I need a 'turn' how many time player moved. One move add one turn (+1).
- devide up what to do according to Card.state.
- Make a EmptyCard Prefab to make generate function.
  - Minion Die
  - Minion Attack
  - Earn EXP, Gold
  - skill
  - more enemy
  - items
  

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

