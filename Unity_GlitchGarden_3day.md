## Make a resource system
In this game, we have to make Resource system. Now, we have two kind of towers which one is `saboten` to attack enemy another is `trophy` to make our resource to build more tower faster.
First, we make a resouce scripts and some view as a `TEXT`.

## Resource script

```C# 
public class Resource : MonoBehaviour
{
    TextMeshProUGUI resourceText;
    private int resource;
    // Start is called before the first frame update
    void Start()
    {
        resourceText = GetComponent<TextMeshProUGUI>();
        resource = 500;
    }

    // Update is called once per frame
    void Update()
    {
        resourceText.text = resource.ToString();
    }

    public int GetResource()
    {
        return resource;
    }

    public void AddResource(int addition)
    {
        resource += addition;
    }

}
```

We can adjust resource by using two public methods.

## Parent and Child
Some object have childs we call parent object. `Parent - Child set` Fix some option of parent, child follow it. But adjust child, it just only work at child by itself. We can control all of child by adjust parent.

## ++ Instansiate by child
We use Instansiate to create new object. Sometimes, we need to create an object as a child object.
Below code can do that.

```C#
IEnumerator RespawnCrocodile()
{
    yield return new WaitForSeconds(Random.Range(1.0f, 5.0f));
    yLocation = Random.Range(minYLocation, maxYLocation);
    GameObject newobject = Instantiate(lizard, new Vector3(respawnXLocation, yLocation), Quaternion.identity);
    newobject.transform.parent = transform;
}
```

## Find the place where call a method
We can find by using `cmd + f`. But, if it called from animation? It can't appear just `cmd + f`. This case, we solve to add some options. `cmd + shift + f` on mac, we can change find location. change it to directory and select your project path. Then, it can find from all file, surly the method appear even it contain *.anim file.

