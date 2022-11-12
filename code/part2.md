---
layout: page
title: Writing Your Own Patterns&#x3A; Part 2
---

Let's pick up from where we left off in [Part 1](/code/part1)

---

### Table of contents

* [The `beforeRender` function](#the-beforerender-function)
* [Value, Brightness, and Gamma Correction](#value-brightness-and-gamma-correction)
* [Waves](#waves)
* [Time: A Sawtooth Wave](#time-a-sawtooth-wave)
* [Triangle](#triangle)
* [(Sine) Wave](#sine-wave)
* [Playing With Waves](#playing-with-waves)
* [Polar Waves](#polar-waves)
* [Noise](#noise)
* [Next Steps](#next-steps)

---

### The `beforeRender` Function

While the `render` and `render2D` functions are called once for each pixel, the `beforeRender` function is called once before each new frame of pixels is rendered to the strip. This is where we can prepare any data needed by all of the pixels once.

The delta argument is the number of elapsed milliseconds (with a resolution of 6.25ns!) since the last time beforeRender was called. You can use delta to create animations that run at the same speed regardless of the frame rate.

In the introduction, we used the `time` function to make patterns move. In [Part 1](/code/part1), we just did this in `render`, once for each pixel. Now we know that we should move that to `beforeRender`, since it only needs to be updated once per frame not once per pixel:

    export function beforeRender(delta) {
      t = time(.1)
    }
    
    export function render2D(index, x, y) {
      h = x + t
      hsv(h, 1, 1)
    }

So far all of the patterns we've created turn on all the pixels at full brightness. Let's add some variety.

---

### Value, Brightness, and Gamma Correction

Type (or copy and paste) the following code into the editor:

    export function beforeRender(delta) {
      t = time(.1)
    }

    export function render2D(index, x, y) {
      v = x + t // scroll value horizontally
      v = v % 1 // wrap value from 1.0 to 0.0 (value does not wrap automatically)
      hsv(1, 1, v)
    }

Note that we now have a slightly dark line scrolling horizontally.

Value (v) is the amount of light energy. You might think that a value of 0.5 would be half as bright as 1.0, but humans actually perceive brightness on a power-law scale (search for "gamma correction" for more information).
This means that our eyes perceive 0.25 as about half as bright as 1.0. 

To make the value change more noticeable, let's square it.

Change the line to the following:

    hsv(1, 1, v * v)

Notice the value change is more pronounced? We've squared the value. Value is between 0.0 and 1.0. So a value of 0.5, for example, when squared becomes 0.25. A value of 0.6 becomes 0.36, etc. Squaring the fractional values increases the contrast.

Try cubing the value:

    hsv(1, 1, v * v * v)

and the contrast increases even more. Notice that the brightest part stays just as bright, and the darkest part just as dark, but the values in between become more gradual. That's because 1.0 squared is still 1.0, and 0.0 squared equals 0.0.

The final code: 

    export function beforeRender(delta) {
      t = time(.1)
    }

    export function render2D(index, x, y) {
      v = x + t // scroll value horizontally
      v = v % 1 // wrap value from 1.0 to 0.0 (value does not wrap automatically)
      v = v * v * v // increase contrast
      hsv(1, 1, v)
    }

---

### Waves

We've only been using the `time` function to add motion so far. Let's try other ways.

Add the following line inside the `beforeRender` function:

    w = triangle(t)

And then change the first line in `render2D`:

    v = x + w

Notice now instead of constantly scrolling in one direction, it now moves back and forth!

Let's explore some different waveforms and how to generate them.

---

### Time: A Sawtooth Wave

The `time` function that we've been using creates a sawtooth wave between 0.0 and 1.0 that loops about every `65.536 * interval` seconds (use `0.15` for approximately 1 second).

      /|  /|  /|
     / | / | / |
    /  |/  |/  |

---

### Triangle

The `triangle` function converts a sawtooth wave between 0.0 and 1.0, like that returned by the `time` function, to a triangle wave between 0.0 and 1.0. The value passed to `triangle` is automatically wrapped between 0.0 and 1.0.

      /\    /\    /\  
     /  \  /  \  /  \ 
    /    \/    \/    \

---

### (Sine) Wave

The `wave` function converts a sawtooth wave between 0.0 and 1.0, like that returned by the `time` function, to a smooth sine wave between 0.0 and 1.0. The value passed to `wave` is automatically wrapped between 0.0 and 1.0.

<img src="/assets/img/code/sine-wave.png" class="img-thumbnail" style="width: 240px" />

---

### Playing with waves

Let's get back to playing.

Try changing line in `beforeRender` from `triangle` to `wave`:

    w = wave(t)

Notice the wave moves back and forth more smoothly, slowing as it reaches the sides before reversing direction.

Let's make it more interesting by changing the hue:

    h = y + w
    v = v * v * v
    hsv(h, 1, v)

The complete code so far:

    export function beforeRender(delta) {
      t = time(.1)
      w = wave(t)
    }

    export function render2D(index, x, y) {
      h = y + w // scroll hue vertically

      v = x + w // scroll value horizontally
      v = v % 1 // wrap value from 1.0 to 0.0 (value does not wrap automatically)
      v = v * v * v // increase contrast
      
      hsv(h, 1, v)
    }

---

### Polar Waves

Like before, we can switch from Cartesian XY coordinates to polar coordinates.

    export function beforeRender(delta) {
      t = time(.1)
      w = triangle(t)
    }

    export function render2D(index, x, y) {
      radius = hypot(x - .5, y - .5)
      
      h = radius * 2
      v = radius * 2 * w
      
      hsv(h, 1, v)
    }

Try changing it so the hue moves but the value doesn't:

    h = radius * 2 * w
    v = radius * 2

Flip the value so the center is bright and the outside is dark:

    v = 1 - (radius * 2)

The complete code:

    export function beforeRender(delta) {
      t = time(.1)
      w = triangle(t)
    }

    export function render2D(index, x, y) {
      radius = hypot(x - .5, y - .5)
      
      h = radius * 2 * w
      v = 1 - (radius * 2)
      v = v * v * v
      
      hsv(h, 1, v)
    }

---

### Noise

`setPerlinWrap(x, y, z)`

Causes Perlin functions to wrap at the given integer intervals between 2 and 256. Useful for creating textures that can repeat smoothly, while controlling density.

`perlin(x, y, z, seed)`

Generates 3D Perlin noise. Every integer value produces a different random result, with smooth transitions between them.

`perlinFbm(x, y, z, lacunarity, gain, octaves)`

Generates 3D fractal Brownian motion. The lacunarity controls the distance between octaves and should be set to 2 or another integer value if wrapping is desired. The gain controls the strength between each octave, try values around 0.5-0.8.

`perlinRidge(x, y, z, lacunarity, gain, offset, octaves)`

Generates 3D fractal ridged Perlin noise. The lacunarity controls the distance between octaves and should be set to 2 or another integer value if wrapping is desired. The gain controls the strength between each octave, try values around 0.5-0.8. The offset is used to invert the ridges, values around 1.0 work well.

`perlinTurbulence(x, y, z, lacunarity, gain, offset, octaves)`

Generates 3D fractal turbulent Perlin noise. The lacunarity controls the distance between octaves and should be set to 2 or another integer value if wrapping is desired. The gain controls the strength between each octave, try values around 0.5-0.8.

More noise details coming soon...

---

### Next Steps

Next steps: coming soon...
