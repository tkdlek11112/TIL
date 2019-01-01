# Today..

I start to make new game like Plant vs Zombie. (Udemy lecture)

# Screen Size

There are a lot of different screens and devices but we can't fit all them. By using scale option, fit the canvas to maincamera and change render mode to world space.
(It called world space canvas) In order to use map(field) like a tile, calculate image size and camera size. It's so hard to understand first time lol.

# 2D Animation

There are two types anmation `Sprite sheet animation` and `Bone-based animation`.

Sprite shett animation is control the animation with many similar spreits. Bone-based is set the bone on the splite and change the bone to make animation.

# Animator, Animation state

The animator is a control object what animation sprite do. Make a object(sprite) and add animator, I can control what it do like walk, attack and jump.

# How can I get current animation state my sprite?

In programming, I face a problem that I want to make the sprite walk left on walk animation. So, I add the code `translate.Translate(Vector2)` in `Update()`. It works. But, the sprite move left on every animatins. The sprite has two animations one is walk the other is jump. I want to that it move left only walk animation but it move on both lol. So I need to know what animation it doing.

Add this code, I solve this problem.
    
    if(GetComponent<Animator>().GetCurrentAnimatorClipInfo(0)[0].clip.name == "Lizard Walk"

`GetCurrentAnimatorClipInfo(int index)` return array ( I don't know why it return array lol ). So I just user `[0]`, It works.
