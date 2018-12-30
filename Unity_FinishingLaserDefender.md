# UNITY FINISH LASER DEFENDER

## SCORE
ScoreText is basic obeject which all games have one or more. In LaserDefender which is a shooting game I made, I have to keep a score-text all level scenes. So I need to make a `singleton design`.

hm.. I foget how connect a script to the textmeshpro lol. Oh I got it. ( I saw my last project - Block Breaker - )

If we use a textmeshpro in a script, we import TMPro.


    using TMPro;
    TextMeshProUGUI scoreText;
    
    scoreText.text = "Hello World!";  // it works
    scoreText.SetText("Hello World!";  // it works, too.
    
