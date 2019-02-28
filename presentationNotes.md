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

# Tweening example

- here's our first TweenMax.to example
- I'm grabbing the node element `document.querySelector('.box')`
- then I'm saying `TweenMax.to`
- then I'm passing in my node element
- Q: what does 2 represent? A: 2s
- Q: what does `{x: 400}` represent? A: destination via transform: translateX
- because we're saying .to, whatever is in the parameters is where it's going to

# Tweening your turn

- you're essentially copying my code on the slide
- click on my codepen, I've already included TweenMax
- give you 1 minute for that OR ask a person to say what the code is
- once coded, take a step back and see how short/elegant this 1 line of code is compared to other CSS/jQuery solutions you may have done in the past
