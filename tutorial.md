# Section 1 of 3: What is py5?

Py5 is a creative coding framework for Python. Its use and functionality is analogous to the widely used [Processing](https://processing.org/) framework. It is a Python version of [Processing](https://processing.org/). Both tools allow users to use code to create visually-oriented products, or "sketches," with or without animation.

Internally, py5 uses [Processing](https://processing.org/)’s core libraries, which are written in Java, while providing the end user with a (mostly) seamless Python programming experience.

## how do we use py5?

When we’re instructing a computer to run code, we cannot use regular human language. Instead, code takes the form of an algorithm or a series of algorithms which are handed to the computer. Although the word algorithm has had a lot of complex recent use, at its simplest form, an algorithm is just a set of rules or instructions for a computer to follow. Unlike most humans, if a computer is given unclear instructions, it can’t problem-solve its way out of the situation - it will simply stop in its tracks.

This means that small errors in the syntax (grammatical structure) of your code will cause many of the problems you run into, and it will get easier as time goes on to anticipate and correct them.

Get familiar with the [py5 reference](https://py5coding.org/reference/summary.html) – this will serve as your glossary for the functions, methods, and data types we discuss here.

Firstly, you'll learn about how a py5 sketch is set up. We will split code up into blocks labeled with functions like `setup()` and `draw()`, which will eventually allow us to create programs with animation and user interaction. For now, though, we'll start simple, with static (non-moving) sketches.

You’ll also notice that the reference seems to be starting a lot of functions and arguments with `py5.` because these functions are built into py5 itself, rather than being a feature of regular Python code.

---

# Section 2 of 3: Understanding program structure

### Understand Program Structure

In this class, every py5 program uses standard imported Python syntax with three core functions:

* **`py5.settings()`**: (Runs 1 time): Sets up structural window configurations before the graphics engine initializes (most notably setting the window size with py5.size()).
* **`py5.setup()`**: (Runs 1 time): Executes immediately after settings(). This is where you set initial states that don't change often, such as background colors, frame rates, or loading images.
* **`py5.draw()`**: (Runs continuously in a loop): Executes repeatedly (60 times per second by default) right after setup() finishes. This is where active drawing and animation take place.

> **Important Rule:** Every program must import `py5` at the top, prefix all library functions with `py5.`, and include `py5.run_sketch()` at the bottom to execute. You'll see more of this as you move through the tutorials.

---

# Section 3 of 3: Drawing basic elements

Although it’s based on Python, which is a general-use or multi-purpose coding language, py5 is made for producing visual output, so you won’t be surprised to learn that there are a variety of built-in functions to draw and color 2D shapes. The most basic shapes you can produce will be familiar to pretty much everyone - rectangles (and squares), uneven quadrilateral shapes, ellipses (ovals or circles), triangles, points, and lines. We call these basic shapes *primitives*. In addition to drawing primitives, this page will go into detail on color and controlling outlines in py5.

## color

If you’ve done any work with graphics editing software like Photoshop or GIMP, you might be familiar with some of the different ways of digitally defining color. For example, you can break a color down into its RGB (Red, Green, and Blue) values, or its HSB (Hue, Saturation, and Brightness). These can both be used in py5 to great effect - for now, we’re using RGB values, in particular represented by a *hexadecimal color code* like \#FF0000.

In a hexadecimal (or hex, for short) code like this, each pair of letters or numbers represents a color. The hexadecimal system, instead of only using numbers from 0-9, has an extended counting system where A follows 9, and the highest possible single digit is F. Knowing this demystifies color codes quite a bit. For example, we can tell \#FF0000 will be red because the first two digits (R) are at their highest possible value, while the G and B sets of digits are at their lowest possible value. Just like mixing light in a prism, \#FFFFFF (RGB all at their highest value) is white, and \#000000 is black.

When you’re drawing a picture, you might do the linework and then fill it in with color afterwards. In py5, you do this in reverse - you tell the program what color something will be *before* you create it. The analogy to drawing a physical picture is that you pick up the color you want to draw with _before_ you start drawing, and you continue using that marker until you switch it out for a marker of a different color.

As an example, let’s create a red rectangle in our sketch. To do this, we will use the `fill()` function and the `rect()` function, which take the following arguments:

`fill(color)`: The function `fill()` will begin filling elements in your sketch with color if supplied with a color as its argument.

`rect(x_coordinate, y_coordinate, width, height)`: `rect()` will draw a rectangle on your screen - the x coordinate is how far it is from the left edge of the screen, the y coordinate is how far it is from the top edge, and the width and height are simply its dimensions in pixels. Put together, and with those arguments swapped out, your code might look something like this:

> An argument is a piece of information you put inside a function’s parentheses to tell it what to do. Different functions take different numbers of arguments. Some functions behave differently depending on how many arguments you provide, and some arguments have default values that are used when you leave them out. We’ll explore those possibilities later.

It's time to test out some code. Locate the file called playground.py and adjust it so it includes the following:

    # Giving our program access to py5 tools
    import py5

    def settings():
      # Sizing our sketch to 500 by 500 pixels
      py5.size(500,500)

    def draw():
      py5.fill('#FF0000')
      py5.rect(100, 150, 200, 300)

    py5.run_sketch()

![](https://py5coding.org/_images/0350156caea0826c05842a3fef65c048acfe64f282583c5e3aeaba216a6f0744.png)

> Save your program, then run it to see if the image matches the image above:
> 1. Open the terminal in VS Code. Navigate so that you are inside the directory containing the file you want to run: playground.py.
> 2. In the command line, type **python playground.py** and press Enter. You should see a window pop up with some graphics.

This system of positioning by coordinates is common in many digital spaces, and you’ll get your head around it quickly if you haven’t already. You can see exactly how it works in this diagram, which has marked the distance between the top-left corner of our `rect()` and the edges of the screen.

> Note that the x coordinates work much as they do in the [Cartesian coordinate system](https://en.wikipedia.org/wiki/Cartesian_coordinate_system). The y coordinates, however, are reversed from what you may be used to: numbers at the top of the canvas are smaller, increasing as you move down.

![](https://py5coding.org/tutorials/images/drawing_2d_primitives/colour-fill-rect.png)

The `fill()` function will last until you tell it to stop - no matter how many shapes you draw beneath it, all will have the color you specified. If you’d like to end your `fill()` without replacing it with a different color, to have empty shapes entirely, you use a different function - `no_fill()`. It doesn’t take any arguments at all.

    import py5

    def settings():
      # Sizing our sketch to 500 by 500 pixels
      py5.size(500,500)

    def draw():
       # red rectangles
      py5.fill('#FF0000')
      py5.rect(100,150, 200,300)
      py5.rect(10,15, 20,30)

       # orange square
      py5.fill('#FF9900')
      py5.rect(50,100, 150,150)
  
      # fill-less square
      py5.no_fill()
      py5.rect(250,100, 150,150)

    py5.run_sketch()

   

![](https://py5coding.org/_images/80524a8a310e731898a0116fe8c9a591af993ca69f18f01d78426915e44c288d.png)

By now you’ve probably noticed that all of these rectangles have a black outline. This outline can also be called a *stroke*, and that’s what we call it in py5. Exactly like `fill()`, we can use `stroke()` with a color to change all subsequent outlines to that color. You can also change how big the outline is with `stroke_weight()` or entirely remove it with `no_stroke()`. Add a white stroke with a `stroke_weight()` of 3 above your rectangles to see how it works:

    def settings():
        py5.size(500,500)

    def draw():
        # setting our stroke color and width!
        py5.stroke('#FFFFFF')
        py5.stroke_weight(3)
    
        # red rectangles
        py5.fill('#FF0000')
        py5.rect(100,150, 200,300)
        rpy5.ect(10,15, 20,30)
    
        # orange square
        py5.fill('#FF9900')
        py5.rect(50,100, 150,150)
    
        # fill-less square
        py5.no_fill()
        py5.rect(250,100, 150,150)

    py5.run_sketch()

![](https://py5coding.org/tutorials/images/drawing_2d_primitives/colour-stroke.png)

There’s a few more ways to fine-tune those outlines… `stroke_cap()` can change these outlines to be sharper or to stick out, and `stroke_join()` changes how they connect at corners.

*Reference pages: <a href="../reference/sketch_stroke_cap.html" class="reference internal">stroke_cap()</a> and <a href="../reference/sketch_stroke_join.html" class="reference internal">stroke_join()</a>*

## background colors

As you’ve already seen, `size()` sets the size in pixels of your entire sketch window. There’s also a `background()` function to define the color of the background. Try adding this as the final line of your sketch:

    import py5
    
    def settings():
        py5.size(500,500)

    def draw():
        # setting our stroke color and width!
        py5.stroke('#FFFFFF')
        py5.stroke_weight(3)
    
        # red rectangles
        py5.fill('#FF0000')
        py5.rect(100,150, 200,300)
        rpy5.ect(10,15, 20,30)
    
        # orange square
        py5.fill('#FF9900')
        py5.rect(50,100, 150,150)
    
        # fill-less square
        py5.no_fill()
        py5.rect(250,100, 150,150)

        #dark blue background
        py5.background('#004477')

    py5.run_sketch()

![](https://py5coding.org/_images/ae8770875a7215c9ac6e92bca4f1e703256a5d50416bf7747cd8d99d184a2a4f.png)

If you run the sketch, you’ll notice everything has disappeared. This is because py5 draws from the top down, following the lines of your code, so the background is now hiding all the previous lines! Instead, we'll move that to the top of our draw function, so that it executes _before_ everything else, and the rectangles are drawn on top of the background.

    import py5
    
    def settings():
        py5.size(500,500)

    def draw():
        #dark blue background
        py5.background('#004477')
        
        # setting our stroke color and width!
        py5.stroke('#FFFFFF')
        py5.stroke_weight(3)
    
        # red rectangles
        py5.fill('#FF0000')
        py5.rect(100,150, 200,300)
        rpy5.ect(10,15, 20,30)
    
        # orange square
        py5.fill('#FF9900')
        py5.rect(50,100, 150,150)
    
        # fill-less square
        py5.no_fill()
        py5.rect(250,100, 150,150)

    py5.run_sketch()

![](https://py5coding.org/tutorials/images/drawing_2d_primitives/colour-blue-background.png)

Much better. When you’re working with still sketches like this, ordering your background, fills and shapes properly will be very important to get the correct visuals. On the other hand, in animated sketches, sometimes the `background()` function can be very useful to clear the entire screen before something else appears.

## changing color modes

Since a hexadecimal code is equivalent to using the RGB system, you can use straight RGB values for the same effect. By default, these values can go up to 255. For example, `fill('#FF0000')` (where FF represents the highest number possible) is equivalent to `fill(255, 0, 0)`. Why would you want to use one over the other? Well, if you had a program that had to change the color of a shape, and the color is stored as three numbers, it would be a lot easier to simply add to the red, green or blue color value than to try to calculate the differences between hex codes.

If you wanted to use HSB (hue, saturation, brightness) instead, you can use a function called `color_mode()` in your sketch, before you start coloring things in. If you use color selectors or color pickers in other programs, you will quickly discover that the *hue* is represented by a number from 0 to 360 (exactly like the degrees of a circle), and *saturation* and *brightness* can be anywhere from 0 to 100. Making this system work in your code is pretty straightforward. To use `color_mode()` you need the following arguments:

`color_mode(TYPE, maximum value, maximum value, maximum value)`

… which in this case means …

`color_mode(HSB, 360, 100, 100)`

In HSB mode, that bright red color we represented as `fill(255, 0, 0)` would instead be `fill(0, 100, 100)` or `fill(360, 100, 100)` - since the hue range is “circular” and loops back in on itself, either will work. That’s a color at the red point of the hue range, with maximum brightness and saturation. Why would you want to use HSB? Think again about a program that might have to change its colors while it runs. If you could simply add to the number representing hue and cycle through the rainbow that way, it would be a lot easier than manually working out how to do that with RGB values!

*Reference pages: <a href="../reference/sketch_color_mode.html" class="reference internal">color_mode()</a>*

# other primitives

You’ve seen `rect()` used a few different ways, to make rectangles (if the width and height are different) and squares (if those values are the same). Let’s take a look at some of the other functions py5 offers for drawing primitive shapes.

`point(x coordinate, y coordinate)` creates a point, or a single dot, at the position you specify with your arguments. The size of the point will be dependent on your `stroke_weight()`. Look in the top left corner of the image below:


import py5
    
    def settings():
        py5.size(500,500)

    def draw():
        #dark blue background
        py5.background('#004477')
    
        # setting our stroke color and width, and removing fill!
        py5.no_fill()
        py5.stroke('#FFFFFF')
        py5.stroke_weight(3)
    
        # three points/dots
        py5.point(100, 25)
        py5.point(200, 25)
        py5.point(150, 75)

    py5.run_sketch()

![](https://py5coding.org/_images/7ad0d6d0c354020e9f70fa312dd601256d771a7fc6ef8d0dae31abdfd6ceca9d.png)

`triangle(x, y, second x, second y, third x, third y)` is a bit of a mouthful while you’re explaining its arguments - but it will draw a triangle on the screen, with the three points of the triangle represented by these three pairs of x and y coordinates. To draw a triangle exactly where we’ve just drawn our three points, the function would look like this:

    py5.triangle(100,25, 200,25, 150,75)

It’s a good time to mention that in order to make your code easier to understand, there’s no reason you can’t use line breaks and indenting creatively. For example, to make those three pairs of x,y coordinates clearer, you could instead space it out like this, and it still runs:

    py5.triangle(100,25, # First corner
                 200,25, # Second corner
                 150,75) # Third corner

Here's what that sketch looks like now:

    import py5
    
    def settings():
        py5.size(500,500)

    def draw():
        #dark blue background
        py5.background('#004477')

        # setting our stroke color and width, and removing fill!
        py5.no_fill()
        py5.stroke('#FFFFFF')
        py5.stroke_weight(3)
    
        # three points/dots
        py5.point(100, 25)
        py5.point(200, 25)
        py5.point(150, 75)
    
        # triangle
        py5.triangle(100,25, # First corner
                     200,25, # Second corner
                     150,75) # Third corner
    
    py5.run_sketch()

![](https://py5coding.org/_images/0440d932aca4361ad77d3cf65f5b033afeed5b0d2c63581989f33fd647494759.png)

`ellipse(x, y, width, height)` creates an ellipse at the specified coordinates, with the width and height you choose. Giving the same width and height will create a perfect circle.

    import py5
    
    def settings():
        py5.size(500,500)

    def draw():
        #dark blue background
        py5.background('#004477')

        # setting our stroke color and width, and removing fill!
        py5.no_fill()
        py5.stroke('#FFFFFF')
        py5.stroke_weight(3)
    
        # three points/dots
        py5.point(100, 25)
        py5.point(200, 25)
        py5.point(150, 75)
    
        # triangle
        py5.triangle(100,25, # First corner
                     200,25, # Second corner
                     150,75) # Third corner

        # ellipse
        py5.ellipse(100,100, 100,50)
        
    py5.run_sketch()

![](https://py5coding.org/_images/a0f0549dbca8328e01a3892590e5c1937f321dacfcfec8c653068d2672fba521.png)

Note that the x, y position here is the center of the ellipse, not one of the edges. When we were drawing with the `rect()` function, earlier, that position was the top-left corner of the rectangle. You can change this behavior if you want - by default, py5 uses `ellipse_mode(CENTER)` and `rect_mode(CORNER)`.

*Reference pages: <a href="../reference/sketch_rect_mode.html" class="reference internal">rect_mode()</a> and <a href="../reference/sketch_ellipse_mode.html" class="reference internal">ellipse_mode()</a>*

`quad(x,y, x,y, x,y, x,y)` is a four-cornered or quadrilaterial shape, with each of those corners defined by a pair of x,y coordinates. It gives you more control over its shape than a `rect()` does.

    import py5
    
    def settings():
        py5.size(500,500)

    def draw():
        #dark blue background
        py5.background('#004477')

        # setting our stroke color and width, and removing fill!
        py5.no_fill()
        py5.stroke('#FFFFFF')
        py5.stroke_weight(3)
    
        # three points/dots
        py5.point(100, 25)
        py5.point(200, 25)
        py5.point(150, 75)
    
        # triangle
        py5.triangle(100,25, # First corner
                     200,25, # Second corner
                     150,75) # Third corner

        # ellipse
        py5.ellipse(100,100, 100,50)


        # a quad
        py5.quad(250,250, # Remember, you can
                  350,300, # break it up
                  380,400, # to understand
                  260,380) # what's happening!
                  
    py5.run_sketch()

![](https://py5coding.org/_images/cbeb8a557e1401caed785c20aa2791cf1039a94952029ba9ce18435663dc46db.png)

## rainbow task

Now that you've seen basic primitive shape functions, it’s time to complete a task. We’ll be recreating this rainbow image using what you’ve learned so far.

![](https://py5coding.org/tutorials/images/drawing_2d_primitives/drawing-rainbow.png)

If you want to match the colors perfectly, this code might help start you off…

import py5

def settings():
    py5.size(600,600)

def draw():
    py5.background('#004477') # dark blue background
    py5.no_stroke()

    py5.fill('#ff0000') # red 

    py5.fill('#ff9900') # orange 

    py5.fill('#ffff00') # yellow

    py5.fill('#00ff00') # green

    py5.fill('#0099ff') # blue

    py5.fill('#6633ff') # purple

> Here’s a hint: you don’t have to figure out how to make half-circles, or to make gaps in your shapes. Just cover shapes with other shapes, and it’ll look the same!

---

By the py5 community

© Copyright 2020-2025.

Content adapted from: [intro to py5 and python](https://py5coding.org/tutorials/intro_to_py5_and_python.html) and [drawing basic elements](https://py5coding.org/tutorials/intro_to_py5_and_python_02_drawing_2d_primitives.html)

Adjusted and augmented by the teacher and Gemini
