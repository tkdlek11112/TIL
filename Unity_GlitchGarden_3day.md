## Make a resource system
In this game, we have to make Resource system. Now, we have two kind of towers which one is `saboten` to attack enemy another is `trophy` to make our resource to build more tower faster.
First, we make a resouce scripts and some view as a `TEXT`.

## Resource script

```C# public class Resource : MonoBehaviour
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
