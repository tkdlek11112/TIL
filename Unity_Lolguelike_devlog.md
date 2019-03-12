To-Do.  
- Create CardGenerator object to init cards.  
- Create Basic Player and Minion cards.  
- Make move method to move card.  
- Make attacDagame and healthPoint.  
- Add Logic that cards follow player card.  
  - Add to CardGenerator generate card at empty space.  

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

