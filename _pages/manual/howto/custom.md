---
permalink: /manual/custom
title: "Custom Systems"
sidebar:
  title: "Manual"
  nav: manual
---

In this section i will walk you through creating a custom system in CCBK. The system itself is not especially useful but it contains implementations of all the most important parts of the framework.  

A __completed, playable__ version can be found in the Custom folder of the CityBuilderManual project within the CCBK asset. 

## Building Component

We will start off with a pretty basic building component. 
All it will do is keep a building effective for a certain duration and then disrupt it until it is reset.  

Before actually creating the component let's add an interface for the component so we can easily add other components for the same purpose or switch out the implementation. This step can be skipped, using the component directly instead of an interface works too.

{% highlight csharp %}
public interface ICustomBuildingComponent : IBuildingComponent
{
    void DoSomething();
}
{% endhighlight %}

Next add a script that inherits from BuildingComponent and implements the interface.

{% highlight csharp %}
public class CustomBuildingComponent : BuildingComponent
{
    public override string Key => "CCO";

    public GameObject GoodVisual;
    public GameObject BadVisual;

    public float Duration;

    private float _time;

    private void Update()
    {
        if (_time > 0)
        {
            _time -= Time.deltaTime;
        }

        GoodVisual.SetActive(IsWorking);
        BadVisual.SetActive(!IsWorking);
    }

    public void DoSomething()
    {
        _time = Duration;
    }
}
{% endhighlight %}

As you can see i've added the reset logic and some GameObjects for visualization.
The Code is mandatory for building components and is used to identify the component in save/load.
We'll add the save logic next, put the following at the end of your script.

{% highlight csharp %}
#region Saving
[Serializable]
public class CustomComponentData
{
    public float Time;
}

public override string SaveData()
{
    return JsonUtility.ToJson(new CustomComponentData()
    {
        Time = _time
    });
}
public override void LoadData(string json)
{
    var data = JsonUtility.FromJson<CustomComponentData>(json);

    _time = data.Time;
}
#endregion
{% endhighlight %}

As you can see saving usually contains a data class that stores all the runtime data of the component. The building component base class provides overridable save and load methods that are called by the building. Saving is optional, if the methods are not overridden or return empty not data will be saved.  

The last thing we need is for the component to influence the buildings efficiency. We do this by implementing IEfficiencyFactor

{% highlight csharp %}
public class CustomBuildingComponent : BuildingComponent, ICustomBuildingComponent, IEfficiencyFactor
{
    public override string Key => "CCO";

    public bool IsWorking => _time > 0;
    public float Factor => _time > 0 ? 1 : 0;
...
{% endhighlight %}

## Building Trait

A BuildingTrait is a special BuildingComponent that always creates a Reference an is stored in a special collection within the BuildingManager. This is done so they can be retrieved without having to iterate through all the buildings on the map. The interface for it looks like this.

{% highlight csharp %}
public interface ICustomBuildingTrait : IBuildingTrait<ICustomBuildingTrait>
{
    float CustomValue { get; }

    void DoSomething();
}
{% endhighlight %}

The minimal implementation for the Trait is similar to a normal component.

{% highlight csharp %}
public class CustomBuildingTrait : BuildingComponent, ICustomBuildingTrait
{
    public override string Key => "CTR";

    public float CustomValue => 1;

    public BuildingComponentReference<ICustomBuildingTrait> Reference { get; set; }

    public override void InitializeComponent()
    {
        base.InitializeComponent();

        Reference = registerTrait<ICustomBuildingTrait>(this);
    }
    public override void OnReplacing(IBuilding replacement)
    {
        base.OnReplacing(replacement);

        var replacementTrait = replacement.GetBuildingComponent<ICustomBuildingTrait>();

        replaceTrait(this, replacementTrait);
    }
    public override void TerminateComponent()
    {
        base.TerminateComponent();

        deregisterTrait<ICustomBuildingTrait>(this);
    }

    public void DoSomething()
    {
        Debug.Log("Hello!");
    }
}
{% endhighlight %}

The major difference to normal components is that we have to manage a reference throughout the lifecycle of the component. It has to be created when the building is build, passed on when it is replaced and removed when the building gets demolished.

The purpose of the trait is to spawn walkers so we will return to it after creating some custom walkers.

## Walker

The first walker we will add is a roaming walker that resets every ICustomBuildingComponent it passes.
CCBK has a base class called BuildingComponentWalker<T> for exactly this purpose.

{% highlight csharp %}
public class CustomRoamingWalker : BuildingComponentWalker<ICustomBuildingComponent>
{
    protected override void onComponentEntered(ICustomBuildingComponent buildingComponent)
    {
        base.onComponentEntered(buildingComponent);

        buildingComponent.DoSomething();
    }
}
{% endhighlight %}

Thats it, whenever the walker passes a ICustomBuildingComponent onComponentEntered will be called. The base class also provides onComponentRemaining in case you want to do something as every frame the component is in reach instead of just the first one.  

The second most prevalent kind of walker in city builder are destination walkers.
The one we'll add is fairly simple since it gets its path passed to it from outside.
It will follow that path it is given and call a method on its target when it is finished.

{% highlight csharp %}
public class CustomDestinationWalker : Walker
{
    public enum CustomDestinationWalkerState
    {
        Inactive = 0,
        Walking = 1
    }

    private CustomDestinationWalkerState _state = CustomDestinationWalkerState.Inactive;
    private BuildingComponentReference<ICustomBuildingTrait> _target;

    public void StartWalker(BuildingComponentPath<ICustomBuildingTrait> customPath)
    {
        _state = CustomDestinationWalkerState.Walking;
        _target = customPath.Component;
        walk(customPath.Path);
    }

    protected override void onFinished()
    {
        if (_target.HasInstance)
            _target.Instance.DoSomething();

        base.onFinished();
    }

    #region Saving
    [Serializable]
    public class DeliveryWalkerData
    {
        public WalkerData WalkerData;
        public int State;
        public BuildingComponentReferenceData Target;
    }

    public override string SaveData()
    {
        return JsonUtility.ToJson(new DeliveryWalkerData()
        {
            WalkerData = savewalkerData(),
            State = (int)_state,
            Target = _target.GetData()
        });
    }
    public override void LoadData(string json)
    {
        var data = JsonUtility.FromJson<DeliveryWalkerData>(json);

        loadWalkerData(data.WalkerData);

        _state = (CustomDestinationWalkerState)data.State;
        _target = data.Target.GetReference<ICustomBuildingTrait>();

        switch (_state)
        {
            case CustomDestinationWalkerState.Walking:
                continueWalk();
                break;
        }
    }
    #endregion
}
{% endhighlight %}

The _state variable is only added so the walker can be correctly restored when loading. The _target is stored so the walker can call DoSomething on it when it is reached.  
The WalkerData field in the save data contains all the basic data of the walker like current position and path which enables you to just call continueWalk in Load.

## WalkerSpawner

To actually spawn walkers from buildings CCBK uses something called in WalkerSpawner.
These come in Cyclic, Pooled and Manual varieties and are serializable field that are added to building components.
In Unity versions prior to 2020.1 generic fields do not get serialized which which is why you will see concrete spawner implementations at the end of all the walker classes in CCBK. 
If you are using such a version add the spawners to the walkers.

{% highlight csharp %}
/// <summary>
/// concrete implementation for serialization, not needed starting unity 2020.1
/// </summary>
[Serializable]
public class ManualCustomRoamingWalkerSpawner : ManualWalkerSpawner<CustomRoamingWalker> { }
/// <summary>
/// concrete implementation for serialization, not needed starting unity 2020.1
/// </summary>
[Serializable]
public class CyclicCustomRoamingWalkerSpawner : CyclicWalkerSpawner<CustomRoamingWalker> { }
/// <summary>
/// concrete implementation for serialization, not needed starting unity 2020.1
/// </summary>
[Serializable]
public class PooledCustomRoamingWalkerSpawner : PooledWalkerSpawner<CustomRoamingWalker> { }
{% endhighlight %}

Now add the spawner to the building trait we created earlier.

{% highlight csharp %}
public CyclicCustomRoamingWalkerSpawner CustomRoamingWalkers;
public CyclicCustomDestinationWalkerSpawner CustomDestinationWalkers;

private void Awake()
{
    CustomRoamingWalkers.Initialize(Building);
    CustomDestinationWalkers.Initialize(Building, destinationWalkerSpawning);
}
private void Update()
{
    if (Building.IsWorking)
    {
        CustomRoamingWalkers.Update();
        CustomDestinationWalkers.Update();
    }
}

private bool destinationWalkerSpawning(CustomDestinationWalker walker)
{
    var path = Dependencies.Get<ICustomManager>().GetPath(Building.BuildingReference, walker.PathType, walker.PathTag);
    if (path == null)
        return false;
    walker.StartWalker(path);
    return true;
}
{% endhighlight %}

Initialization and updating of the spawners is handled by the owning building component. Finding a path for the destination walker could be done directly in the component but we'll move it out into a custom manager which we will create in the next chapter.

## Manager

Managers are central scripts meant to orchestrate different systematic behaviors. Once again we'll start by creating an interface.

{% highlight csharp %}
public interface ICustomManager
{
    float GetTotalValue();
    BuildingComponentPath<ICustomBuildingTrait> GetPath(BuildingReference home, PathType pathType);

    void Add(BuildingComponentReference<ICustomBuildingTrait> trait);
    void Remove(BuildingComponentReference<ICustomBuildingTrait> trait);
}
{% endhighlight %}

The manager will be responsible for calculating a total from the CustomValue field of our traits. It will also provide the paths for our destination walkers. Lastly it will be notified when oue of our traits gets built or demolished. Let' look at the implementation.

{% highlight csharp %}
public class CustomManager : MonoBehaviour, ICustomManager
{
    public float Multiplier;

    private void Awake()
    {
        Dependencies.Register<ICustomManager>(this);
    }

    public float GetTotalValue()
    {
        return Dependencies.Get<IBuildingManager>().GetBuildingTraits<ICustomBuildingTrait>().Sum(t => t.CustomValue) * Multiplier;
    }
    public BuildingComponentPath<ICustomBuildingTrait> GetPath(BuildingReference home, PathType pathType)
    {
        foreach (var other in Dependencies.Get<IBuildingManager>().GetBuildingTraitReferences<ICustomBuildingTrait>())
        {
            if (other.Instance.Building == home.Instance)
                continue;

            var path = PathHelper.FindPath(home.Instance, other.Instance.Building, pathType);
            if (path == null)
                continue;

            return new BuildingComponentPath<ICustomBuildingTrait>(other, path);
        }

        return null;
    }

    public void Add(BuildingComponentReference<ICustomBuildingTrait> trait)
    {
        Debug.Log("Custom Trait Added!");
    }
    public void Remove(BuildingComponentReference<ICustomBuildingTrait> trait)
    {
        Debug.Log("Custom Trait Removed");
    }
}
{% endhighlight %}

To calculate the total value the manager pulls all the traits from the BuildingManager and applies a Multiplier. As mentioned before BuildingManager keeps track of all traits for quick retrieval.  
For the path we just loop all traits and return the first one that PathHelper is able to calculate.  
The Add and Remove Methods don't have and function in this demonstration so we'll just log to check if they work. 

## Score

To be able to use the total value calculated by the manager in visuals and win conditions we will now create a score. Scores are pretty straightforward ScriptableObjects that are implemented like this.

{% highlight csharp %}
[CreateAssetMenu(menuName = "CityBuilder/Scores/" + nameof(CustomScore))]
public class CustomScore : Score
{
    public float Multiplier;

    public override int Calculate()
    {
        return Mathf.RoundToInt(Dependencies.Get<ICustomManager>().GetTotalValue() * Multiplier);
    }
}
{% endhighlight %}

To see the score add some kind of text to the scene in combination with a ScoreVisualizer. For the score to be calculated you need a ScoreCalculator in the scene. The ScoreCalculator pulls the Scores it has to calculated from a set of scores it retrieves from the Dependencies. To register your custom score for that add an ObjectRepository to the scene and give it a ScoreSet that contains the instance of score used in the visualizer.