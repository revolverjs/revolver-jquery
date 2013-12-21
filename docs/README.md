# Documentation

## Installation

The recommended way to install Revolver is with [Bower](http://bower.io/).

```shell
bower install revolverjs
```

It will resolve all of Revolver's dependencies for you, no need to go and download those separately. If you are unfamiliar with it, I highly recommend you take a look!

Of course, you can still take the ol' fashioned approach and [download](https://github.com/johnnyfreeman/revolverjs/archive/master.zip) and unzip it anywhere in your project. Just make sure you also do the same for Revolver's hard dependencies: [Lodash](http://lodash.com/) and [Bean](https://github.com/fat/bean).

## Usage

There are only two things that are required to instantiate Revolver: The css selectors to the container and slides.

```javascript
var mySlider = new Revolver({containerSelector: '#slidesContainer', slideSelector: '.slide'});
```

Or, the actual container and slides themselves.

```javascript
var mySlideContainer = document.getElementById('slidesContainer');
var mySlides = mySlideContainer.getElementsByClassName('slide');
var mySlider = new Revolver({container: mySlideContainer, slides: mySlides});
```

Or any combination of the two.

## Options

Revolver's defaults can be overwritten upon instantiation (as the second argument to the constructor) or at any time there-after (through the [setOptions()](methods/setoptions.md) method).

* [**autoPlay**](options/autoplay.md): Dictates whethor or not Revolver will begin playing immediately.
* [**container**](options/container.md): Dom element that wraps all slide elements.
* [**containerSelector**](options/containerselector.md): String selector used to find the container element.
* [**slides**](options/slides.md): Array of dom elements (slides).
* [**slidesSelector**](options/slidesselector.md): String selector used to find slides dom elements.
* [**onPause()**](options/onpause.md): A callback that is executed every time the pause() method is called.
* [**onPlay()**](options/onplay.md): A callback that is executed every time the play() method is called.
* [**onReady()**](options/onready.md): A callback that is executed as soon as Revolver is completely setup and ready to go.
* [**onRestart()**](options/onrestart.md): A callback that is executed every time the restart() method is called.
* [**onStop()**](options/onstop.md): A callback that is executed every time the stop() method is called.
* [**rotationSpeed**](options/rotationspeed.md): The number of milliseconds to stay on each slide before transitioning to the next.
* [**transition**](options/transition.md): The transition option is just a namespace for the options that are specific to the transition itself.
  * [**name**](options/transition.name.md): The type of transition to use for all transitions. See here for the full list of available transitions.
  * [**onComplete()**](options/transition.oncomplete.md): A callback that is executed every time the transition's animation has completed.
  * [**onStart()**](options/transition.onstart.md): A callback that is executed every time the transition's animation has started.

## Events

Revolver emits important events and exposes an event api so that you can hook into the core without actually having to hardcode your changes directly into the core.

* [**pause**](events/pause.md): Fired every time the pause() method is called.
* [**play**](events/play.md): Fired every time the play() method is called.
* [**ready**](events/ready.md): Fired after instantiation as soon as Revolver is completely setup and ready to go.
* [**restart**](events/restart.md): Fired every time the restart() method is called.
* [**stop**](events/stop.md): Fired every time the stop() method is called.
* [**transitionStart**](events/transitionstart.md): Fired every time the transition's animation has started.
* [**transitionComplete**](events/transitioncomplete.md): Fired every time the transition's animation has completed.

## Instance Methods

Once you have instantiated Revolver, as shown [here](#usage), you then have access to all these methods.

* [**addSlide()**](methods/addslide.md): Add a new slide to the [slides](props/slides.md) array.
* [**first()**](methods/first.md): Transition immediately to the first slide.
* [**goTo()**](methods/goto.md): Transition immediately to any given slide.
* [**last()**](methods/last.md): Transition immediately to the last (not previous) slide.
* [**next()**](methods/next.md): Transition immediately to the next slide.
* [**pause()**](methods/pause.md): Stops the slider but remembers it's position.
* [**play()**](methods/play.md): Creates a continuous loop where the slider transitions to the next slide at the given interval.
* [**previous()**](methods/previous.md): Transition immediately to the previous slide.
* [**reset()**](methods/reset.md): Queues up the first slide to be next without forcing the transition to happen immediately.
* [**restart()**](methods/restart.md): This is the functional equivalent to calling stop() and then play() consecutively.
* [**off()**](methods/off.md): Removes a previously registered event listener.
* [**on()**](methods/on.md): Registers an event listener.
* [**one()**](methods/one.md): Alias for `on()` except that the handler will removed after the first execution.
* [**setOptions()**](methods/setoptions.md): Merge new options with the existing options object.
* [**stop()**](methods/stop.md): Stops the slider from transitioning to the next slide, and resets the slider.
* [**trigger()**](methods/trigger.md): Executes all listeners for the given event.

## Instance Properties

Once you have instantiated Revolver, as shown [here](#usage), you then have access to all these properties.

* [**currentSlide**](props/currentslide.md): Holds the index number for the current slide.
* [**disabled**](props/disabled.md): Used internally to disable all functionality within a Revolver instance.
* [**intervalId**](props/intervalid.md): The ID that Revolver uses to when stopping or pausing playback.
* [**isAnimating**](props/isanimating.md): Equal to true if Revolver is currently animating, false if not.
* [**iteration**](props/iteration.md): A running count of how many times Revolver has transitioned.
* [**lastSlide**](props/lastslide.md): Holds the index key of the last (not previous) slide in the slider.
* [**nextSlide**](props/nextslide.md): Holds the index key of the next slide in the slider.
* [**numSlides**](props/numslides.md): A count of the total number of slides that Revolver is acting upon.
* [**options**](props/options.md): A congegation of all user-defined options, plugin-defined options, and Revolver's defaults.
* [**previousSlide**](props/previousslide.md): Holds the index key of the slide that was last in transition (before the current one).
* [**slides**](props/slides.md): Houses all the individual slides that Revolver is acting upon.
* [**status**](props/status.md): The current status of the Revolver instance, whether it is "stopped", "paused", or "playing".

## Static Methods

Certiain methods do not need access to a specific instance of Revolver and can be called on the `Revolver` object itself.

* [**setSelectorEngine()**](methods/setselectorengine.md): Revolver uses `querySelectorAll` be default, which should work great on all modern browsers. If you need support for old browsers you can make Revolver us a third-party selector engine such as Qwery, Sel, Sizzle, NWMatcher, etc.
* [**registerTransition()**](methods/registertransition.md): Register a custom transition with Revolver.