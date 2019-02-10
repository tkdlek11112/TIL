DEV Log - RaidLike
==================

## 1Day
1. Make a project "RaidLike", 3D.
2. Set a Project Settings, `Default Behavior Mode` 2D.
3. Make Tilemap and DungeonTiles.
4. Import LPC-Character-Sheet.
5. Make Web-Server to place Character Generator program.
6. Set Aspect 1920x1080. 16:9 has a pixcel problem in tile system. (It ramdomly adds auto pixcel!)

## 2Day
1. Tile Spirte need to set Filter Mode : Point(no filter). If use filter, outline of tile will crack.
2. Make AWS Server to get LPC-Sprite [link](http://ec2-13-125-227-66.ap-northeast-2.compute.amazonaws.com/)

## 3Day
1. Create Custom Editor to create animations from sprite.
2. I make a naming rule about animation. ex) body_dark_spell_up, weapon_dagger_slash_up

## 4Day
1. I found the way to make `gear system`. The animation will be changed what part we equip.
2. reference is follow utube. [link](https://youtu.be/wyyuYX25tBU)
3. I faced an issue that is my animations unsync each other. This means... My body and Weapon didn't start at same time. Actually, it start randomly for each. It looks so bad.
4. To solve this problem, there are some solution in google. Someone recommand use `StartPlayBack` method on animator. But, I didn't work in my case. 
5. But `Play` method works. To sync my animations, I have to start that at once from 0 frame. Because unsync problem comes from animations start random frame for each. So, if all animations start 0 frame, it will be sync!!.
6. animator.play(0,-1,0) first param is stateName. maybe 0 means current state. Second param is Layer number. If put -1, it start from first layer. Last param is a time offset what you want to start.  
7. Create a method that character move to click position from current position. `Vector3.MoveTowards`
8. I need to add find the correct way to target position. 

## 5Day
1. I do `Nav Mesh` is a pathfinding library in unity on my project. But it only allow X-Z plane. My project is top-down tilemap project with X-Y plane.
2. I try change X-Y to X-Z. But if it changes, All sprites and animations rotate x 90 degree.
3. Try searching other things. A* pathfinding looks good. But it will take long time to learn and use.
4. `Nav Mesh Surface` is a library like `Nav Mesh` but it can do on X-Y plane. [Link](https://github.com/Unity-Technologies/NavMeshComponents) and [Link2](http://www.spacebumfuzzle.com/runtime-generation-of-unity-navmesh-on-the-xy-plane-with-2d-physics/) 

## 6Day
1. Finally I finished doing navmesh!!
2. I make a empty GameObject and make a child with plane object. Than Rotate the empty object we can use navmesh baking!!
3. But there is another problem that my sprite rotate. I add a solution code in update() `transform.rotation = Quaternion.identity;`
4. I don't know this code where good or not for performance. I will find some example.

# To-do list 
1. Make prototype game has functions move and attack.

# Issue
1. If characters move to one point, they start to dance. XD I have to make a exception when they collide each other.
