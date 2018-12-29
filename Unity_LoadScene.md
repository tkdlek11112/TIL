# UNITY - LOADSCENE

## LoadScene() 사용법

    using UnityEngine.SceneManagement; 
    SceneManager.LoadScene([index/string sceneName]);

Scene index나 Scene 이름이 올 수 있다. scene index는 프로젝트 빌드 옵션에서 scene순서로 정해진다.
to get index of current scene use `SceneManager.GetActiveScene().buildIndex`.


## 게임 종료하기

    Application.Quit();
    
게임을 종료한다. 

## 로딩화면 넣기

데이터를 많이 불러와야해서 Scene 이동시 화면이 멈추거나 로딩 시간이 필요할 경우, 코루틴을 사용해서 해결.

[참조사이트](http://myriadgamesstudio.com/how-to-use-the-unity-scenemanager/)

    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;

    public class SceneLoaderAsync : Singleton<SceneLoaderAsync> {

    // Loading Progress: private setter, public getter
    private float _loadingProgress;
    public float LoadingProgress { get { return _loadingProgress; } }

    public void LoadScene()
    {
        // kick-off the one co-routine to rule them all
        StartCoroutine(LoadScenesInOrder());
    }

    private IEnumerator LoadScenesInOrder()
    {
        // LoadSceneAsync() returns an AsyncOperation, 
        // so will only continue past this point when the Operation has finished
        yield return SceneManager.LoadSceneAsync("Loading");

        // as soon as we've finished loading the loading screen, start loading the game scene
        yield return StartCoroutine(LoadScene("Game"));
    }

    private IEnumerator LoadScene(string sceneName)
    {
        var asyncScene = SceneManager.LoadSceneAsync(sceneName);

        // this value stops the scene from displaying when it's finished loading
        asyncScene.allowSceneActivation = false;

        while (!asyncScene.isDone)
        {
            // loading bar progress
            _loadingProgress = Mathf.Clamp01(asyncScene.progress / 0.9f) * 100;

            // scene has loaded as much as possible, the last 10% can't be multi-threaded
            if (asyncScene.progress >= 0.9f)
            {
                // we finally show the scene
                asyncScene.allowSceneActivation = true;
            }

            yield return null;
        }
    }

## EASY USE STYLISH FONT 

1. in Unity, We can use Stylish fond by using `TextMeshPro`.
2. Download a font from dafont.com and install lib `TextMeshPro`.
3. Click Window->TextMeshPro->Font Asset Creator to create the font we can use.
4. Import a font to use in game (this must be your Asset Folder) and click Generate Font Atlas.
5. After it finished, save the font file into your Fonts Folder(or somewhere you created).
6. Create `TextMeshPro` object and set Font Asset you saved.

DONE!

## Button

SIMPLE BUTTON CREATE. `CREATE -> UI -> BUTTON`

I used to make a button just add component `button` to `sprite` or `text`. It works as Button!

There is `on Click()` property in `button component`. __It help you set what you do when you click the button__

## Collision Matrix

Sometimes, or often, we want to make a collision. For example, if player collides something(ex missile, enemy ...) player is gonna die.
But if player colides something ground or stone using background object, collision must not be happend. We adjust this situation by using layer collision matrix.
`Edit -> Project Setting -> Physics` You can see the matrix made by layers list. Check the box what you make available collision between two layers.

I wonder whether using Layer Collision Matrix is better than using CompareTag. So I tried to find this issue on google, no one consider that.
X)

## USE SINGLETONE DESIGN

We have to keep a parameter or a character while move scenes. But when we move to other scene from old scene, all object are destroyed by unity (OMG!).
So, it's the time to use __single tone design__. The basic concept is below.

    if(FindObjectsByType(objectType).length > 1) // check there is a same object what we will make this scene.
    {
        Destroy(gameObject); // if there is, destroy it.
    }
    else
    {
        DontDestroyOnLoad(gameObject); // if there isn't, make gameobject with don't destroy option. 
    }
    
Obejct with DontDestroyOnLoad will not destory when move scenes.
