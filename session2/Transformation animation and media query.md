# CCS3

## Transformations & Transistions

There is lot of difference betweent Transformations and Transitions.

**Transform:** The transform property applies a 2D or 3D transformation to an element. This property allows you to rotate, scale, move, skew, etc., elements. 

**Transition:** CSS transitions allows you to change property values smoothly (from one value to another), over a given duration.

### Transform: 

**Syntax**:
`transform: none|transform-functions|initial|inherit;`

![](https://ibin.co/w800/3sS7NqHBUMRH.png)

## Transition
CSS transitions allows you to change property values smoothly (from one value to another), over a given duration.

To create a transition effect, you must specify two things:
- the CSS property you want to add an effect to
- the duration of the effect

> Note: If the duration part is not specified, the transition will have no effect, because the default value is 0.

### transition-timing-function
The transition-timing-function property specifies the speed curve of the transition effect.

some of the Transition timing functions are :
- ease
- linear
- ease-in
- ease-out
- ease-in-out
- cubic-bezier(n,n,n,n)

# Animations 

CSS animations allows animation of most HTML elements without using JavaScript or Flash!

An animation lets an element gradually change from one style to another. You can change as many CSS properties you want, as many times you want. To use CSS animation, you must first specify some keyframes for the animation. Keyframes hold what styles the element will have at certain times.

When you specify CSS styles inside the ***@keyframes*** rule, the animation will gradually change from the current style to the new style at certain times.

    /* The animation code */
	@keyframes example {
	    from {background-color: red;}
	    to {background-color: yellow;}
	}

	/* The element to apply the animation to */
	div {
	    width: 100px;
	    height: 100px;
	    background-color: red;
	    animation-name: example;
	    animation-duration: 4s;
	}

* The **animation-delay** property specifies a delay for the start of an animation.
> Note: Negative values are also allowed in animation delay. If using negative values, the animation will start as if it had already been playing for N seconds.

* The **animation-iteration-count** property specifies the number of times an animation should run.

* The **animation-duration** property defines how long time an animation should take to complete. If the **animation-duration** property is not specified, no animation will occur, because the default value is 0s (0 seconds). 

* The **animation-direction** property specifies whether an animation should be played forwards, backwards or in alternate cycles.

>  The animation-direction property can have the following values, normal, reverse, alternate, alternate-reverse

* **animation-timing-function** Same as for transition

## Media Query

Media query is a CSS technique introduced in CSS3.

It uses the **@media** rule to include a block of CSS properties only if a certain condition is true.

Example :
If the browser window is 500px or smaller, the background color will be lightblue:

    @media only screen and (max-width: 500px) {
	    body {
	        background-color: lightblue;
	    }
	}

