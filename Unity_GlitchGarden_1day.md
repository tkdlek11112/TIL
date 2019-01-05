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
