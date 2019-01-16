## Make Player Animation
1. Make gameobject
2. Make animator controller, animations

## Make projectile
1. Make gameobject as projectile
2. Make scirpt of projectile which has speed, damage, etc..

## Set Collision
1. Add rigidbody and collider to gameObject 
2. Adjust projectsetting - Layer Collider matrix
3. Add `OnCollisionEnter2D` or `OnTriggerEnter2D` to sciprt

## make VFX
__VFX__ is also a gameObject. I can create effect by using instansiate.
~~__BUT__ The gameobject which has effect system doesn't have sort layer option. Because gameobjects which have sprite renderer only have sort layer option. So, to show my effect(particle), I must adjust it's z axis.~~

__OH I FOUND SORT ORDER IN PARTICLE SYSTEM__ We can find sort order in render option on particle system.

## Build defender where i click
In this game, we have to create (build) some thing like a tower or turret, because it's defence game! Before I see the lecture, I made build system by using `gamemanager`. It is watching whether you click or not by using `update()`, if you click, it detect the postion where you click and build a saboten which is my tower. But in lecture, they make a area we can create tower and add collider. If we add collider, we can use call-back method like `OnMouseButtonDown`. It's more simlpe than mine.

> ! We have to change mouse position to world space.

## Make a button
Make a button which help player select tower they want to build.

```C# public class DefenderButton : MonoBehaviour
{
    private void OnMouseDown()
    {
        var ButtonList = FindObjectsOfType<DefenderButton>();
        foreach( DefenderButton button in ButtonList)
        {
            button.GetComponent<SpriteRenderer>().color = new Color32(36, 36, 36, 255);
        }
        GetComponent<SpriteRenderer>().color = Color.white;
    }
}
```

Wow. I can get all of game object which they use same scirpts(or component).


## Build a tower which I select
When I click to build tower, we hope that it build what I selected. To do it, it has to have what tower we selected. I just add some code a button scirpts.

```C# public class DefenderButton : MonoBehaviour
{
    private void OnMouseDown()
    {
        var ButtonList = FindObjectsOfType<DefenderButton>();
        foreach( DefenderButton button in ButtonList)
        {
            button.GetComponent<SpriteRenderer>().color = new Color32(36, 36, 36, 255);
        }
        GetComponent<SpriteRenderer>().color = Color.white;
        FindObjectOfType<TurretArea>().SetDefender(defender);
    }
}
```

