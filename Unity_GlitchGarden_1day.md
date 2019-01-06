 What the... I lost MY file.

# AnyWay Make a defense game.

I have to make a respawner to create crocodile on ilnes (randomly). The respawner works random period and space. Luckly, I can choose the space where crocodile appear by using world location (x, y). 

I make a respawner by using two coroutine. In first try, I used `update()`, but I can't control period between respawns. So, I bring the code to `Start()`. First coroutine just call second coroutine. Second coroutine create gameobject in `while(true)`. See below.

	void Start () {
        StartCoroutine(Respawn());
    }

    IEnumerator Respawn()
    {
        while (true)
        {
            yield return StartCoroutine(RespawnCrocodile());
        }
    }

    IEnumerator RespawnCrocodile()
    {
        yield return new WaitForSeconds(Random.Range(4.0f, 7.0f));
        yLocation = Random.Range(minYLocation, maxYLocation);
        Instantiate(lizard, new Vector3(respawnXLocation, yLocation), Quaternion.identity);

    }

It works well.


# Make Start() as a Coroutine

I shocked while watching lecture. Because I made two coroutine, It's same, but I made two dedicated method and call in the `Start()`. But they chagne the `Start()` to `IEnumerator Start()`. Wow, It can be... shot my head.

# Event from Animation

In Unity, Animation can call method with parameter!

AnimationEvent() contain blow components.

	(int/float/string/object)Parameter // call function with parameter. can choice int, float, string and object
	time // time when it called
	functionName // Name of function
	
Can make animation event on script. Refer to blow source.

// Add an Animation Event to a GameObject that has an Animator
using UnityEngine;
using System.Collections;

```
public class Example : MonoBehaviour
{
    public void Start()
    {
        // existing components on the GameObject
        AnimationClip clip;
        Animator anim;

        // new event created
        AnimationEvent evt;
        evt = new AnimationEvent();

        // put some parameters on the AnimationEvent
        //  - call the function called PrintEvent()
        //  - the animation on this object lasts 2 seconds
        //    and the new animation created here is
        //    set up to happen 1.3s into the animation
        evt.intParameter = 12345;
        evt.time = 1.3f;
        evt.functionName = "PrintEvent";

        // get the animation clip and add the AnimationEvent
        anim = GetComponent<Animator>();
        clip = anim.runtimeAnimatorController.animationClips[0];
        clip.AddEvent(evt);
    }

    // the function to be called as an event
    public void PrintEvent(int i)
    {
        print("PrintEvent: " + i + " called at: " + Time.time);
    }
}
```

# Don't forget make a sprite to anim

1. Import a image to unity.
2. Change sprite option to multi from single.
3. slide and make a anim
