# Intro to Greensock (GSAP)

- this is the platform to use
- animation experts like Sarah Drasner, Val Head -- they all recommend this
- play video on their homepage
- read it
- 20x more performant than native js

# TweenMax and TimelineMax

- read it
- so depending on the size and features you want, you can choose whichever library you want
- click CDN link - you can select "Copy Script tag" which actually gives you script html code

# What's a tween?

- read first sentence
- so in Greensock, you'll always have this kind of syntax where you say `TweenMax.` and some kind of method
- and inside you're passing in the DOM element, how long it is, and options
- let's look at the first one: method
- .method = there are 4 basic ones, .set, .from, .to, .fromTo
- element = read it
- duration = read it
- vars = read it

# GSAP Methods

- read it

# GSAP Vars

- read it - but there's a catch - naming convention
- rotation - notice there's no deg for degrees
- read bottom sentence - so try your best to stick to transform and opacity, you can do a lot with just those 2

# Tweening .to

- here's our first TweenMax.to example
- I'm grabbing the node element `document.querySelector('.box')`
- then I'm saying `TweenMax.to`
- then I'm passing in my node element
- Q: what does 2 represent? A: 2s
- Q: what does `{x: 400}` represent? A: destination via transform: translateX
- because we're saying .to, whatever is in the parameters is where it's going to

# .to

- you're essentially copying my code on the slide
- click on my codepen, I've already included TweenMax
- give you 1 minute for that OR ask a person to say what the code is
- once coded, take a step back and see how short/elegant this 1 line of code is compared to other CSS/jQuery solutions you may have done in the past

# Tweening .from

- read it

# .from

```js
// STEP 1 - 'Grab' the DOM node and store it in 'ball'.
const ball = document.querySelector(".ball");

// STEP 2 - make ball enter from bottom of the screen, fading in
TweenMax.from(ball, 2, {
  y: 1000,
  opacity: 0,
  ease: Elastic.easeOut
});
```

# Timing functions

- Greensock provides a bunch of timing functions via Power0-4
- Greensock provides other functions that you can't get via cubic-bezier: Bounce, Elastic

# Easing visualizer

- However, you can actually make your own timing functions
- Greensock provides you a tool called Easing Visualizer
- [click link]
- so here you have Power0-4, Bounce, Elastic, Slo-mo, Custom
- in addition you can click these underlined keywords and select something else: like from easeOut to easeIn
- and it shows you with the ball how it's going to run
- So take a couple minutes and experiment with your own easing and apply it to a previous codepen

# Multiple tweens

- read it

# Make ball bounce

```js
// STEP 3
TweenMax.to(ball, 2, {
  y: 200,
  ease: Bounce.easeOut
});

// STEP 4 - create another tween (thus using multiple tweens) to make ball bounce down and across all while rotating
TweenMax.to(ball, 3, {
  x: 400,
  rotation: 720,
  transformOrigin: "50% 50%",
  ease: "Power1.easeOut"
});
```

- Note that the Bounce easing looks way better than what we could probably come up with using custom cubic-bezier

# Break

# Why SVG

- there are a lot of reasons why modern websites are using svg
- crisp: whether it's using the new retina screens or whether the image is blown up/shrunk down, it'll be crisp
- responsive: unlike bitmap images, svg images are drawn with mathematics, so it'll always be sharp no matter screen size
- is like HTML in a sense that it has a DOM structure
- [click Example svgs] to show Amazon svg code
- less HTTP requests - so instead of your website having to do 3 roundtrips for 3 images, you can have one roundtrip
- small filesize (5MB of images vs less for SVG)
- accessible

# Use inline SVG to support animation and interaction

- the secret is to use svg INLINE
- don't use <img src="whatever.svg"> since animation won't work with that

# Path Data / Curve commands

-

# Changing SVG attributes with TweenMax

```html
<svg width="600" height="400" viewBox="0 0 600 400">
  <path
    id="tail"
    d="M 300 200 Q 400 200 500 150"
    stroke="#000"
    fill="none"
    stroke-width="10"
  ></path>
</svg>

<!--
M 300 200 Q 400 200 500 250 
-->
```

```js
const tail = document.querySelector("#tail");

TweenMax.to(tail, 0.3, {
  attr: { d: "M 300 200 Q 400 200 500 250 " },
  repeat: Infinity,
  yoyo: true,
  ease: Elastic.ease
});
```

# Changing tweens to TimelineMax

- this feature is what all the animation experts are loving
- use `tl` as a shortform for timeline
- once you've created that timeline, you treat that new tl variable as if it TweenMax and continue doing what you were doing previously
- whatever you consecutively put after, that's your timeline
- whereas before, where we had to use callback functions in jQuery, now you don't, which is a more natural way of thinking of things
- so here in our example it's moving 200px to the right then 200px down
- imagine if you were to try to accomplish the same thing in jQuery, you'd have to use callback functions to move it down after the first animation completed
- so I can see Greensock's attractiveness to their syntax

# Codepen exercise

```js
// STEP 1 - Declare new Timeline
const tl = new TimelineMax({});
tl.add("start");
// STEP 2 - Convert all TweenMax to your timeline variable
tl.to(ball, 3, {
  x: 600,
  rotation: 720,
  transformOrigin: "50% 50%",
  ease: "Power1.easeOut"
});

// STEP 3 - animation has sequentially changed.  make it look as it did before by adding
// a label via tl.add('myLabel'), then refer to it as the 4th parameter in your tl
tl.to(
  ball,
  2,
  {
    y: 400,
    ease: "Bounce.easeOut"
  },
  "start"
);
```

# staggerFrom

- read it

# Experiment stagger codepen

```js
TweenMax.staggerFrom(
  "p",
  0.3,
  { opacity: 0, scale: 0.5, x: -80, ease: Back.easeOut.config(3) },
  0.1
);
```
