---
title: "Row Your Kart"
layout: post
---

A 3D kart racing game built by `Unity` game engine and `C#`. <a href="https://github.com/hezitaooOO/row_your_kart">Github Repo</a>

<img src="/assets/project_photos/row_your_kart/game.png" alt="Image" width="600" height="400">

<a href="https://simmer.io/@baoya_uncle/row-your-kart">
  <img src="/assets/images/play-online-badge.png" alt="Image" width="200" height="100">
</a>



Unity has some default methods for MonoBehaviour base class (most classes many scripts derive from). For example the `void Start()` method is called whenever a object is instantiated from a class.  `void Update()` is the method that is called every time the game frame gets updated. `void OnTriggerEnte()` executtes whenever the object collide (physics is handled by Unity engine) with another object.

An example is the class that is used to count the laps the player has finished:

{% highlight C# %}

public class LapsCounter : MonoBehaviour
{
    private int elapsedLaps = 0;
    private Boolean isColliding = false;
    public bool backwardWallActivated = true;
    //initialize something before frame is rendered
    void Start()
    {
      //some codes here
    }
    // Update is called once per frame
    void Update()
    {
        isColliding = false;
    }
    // when the object collides with another object, trigger the script
    private void OnTriggerEnter(Collider other)
    {
        if (other.tag == "Finish")
        {
            if (isColliding) return;
            isColliding = true;
            elapsedLaps++;
        }
        else if (other.tag == "FinishCheck")
        {
            backwardWallActivated = false;
        }
    }
    // any other utility methods
    public void resetLaps()
    {
        elapsedLaps = 0;
    }
    // more methods...
}
{% endhighlight %}
