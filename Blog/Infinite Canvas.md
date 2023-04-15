---
draft: true
---
# Making an infinite Canvas

There's loads of apps nowadays that use an Infinite Canvas for their main UI element. Apps like [Figma](https://www.figma.com/), [Excalidraw](https://excalidraw.com/) & [quadratichq](http://quadratichq.com/) but recently also [Obsidian](https://obsidian.md) via their canvas core plugin.

How do these apps make their infinite canvas? Well for Excalidraw and Quadratic, we can just look at the source code since they're Open-Source Software.

## Requirements

First, lets define what exactly we're trying to figure out.

To me, the main features of the infinite canvas are going to be:
- Drawing html/css to canvas
	- Handle Events
- Zooming in and out
- Moving stuff around

> At a later point I would also like to know how to:
> - Drawing bezier curves connecting divs that I can move around


> [!todo]
> Figma-like infinite canvas [blog post](https://betterprogramming.pub/how-to-create-a-figma-like-infinite-canvas-in-webgl-8be94f65674f).

## Lets dive into Excalidraw

At a high level, this video gives an amazing breakdown of how Excalidraw works:

[Excalidraw: Under the hood |embed](https://www.youtube.com/watch?v=gvEoTVjVjB8)

Unfortunately, it doesn't tell us how the details of the canvas, still very interesting.

### Into [the codebase](https://github.com/excalidraw/excalidraw)



## Quadratichq

The only [blog post](https://blog.quadratichq.com/) that quadratic has is about WASM and is more of a marketing piece rather than a technical blog post. 

### Into [the codebase](https://github.com/quadratichq/quadratic)

---
It seems like both Quadratichq and Figma are using webGL meanwhile excalidraw is using plain js.

I'll be prototyping mine in js for speed since I don't know webGL.

---

## Getting started with Canvas
https://codepen.io/metruzanca/pen/GRBeWMd

## To infinity and Beyond

Refactored to use a class: https://codepen.io/metruzanca/pen/BaPbWqM?editors=0011

Using a class to encapsulate the offset / scale abstraction needed for the coordinate system.

```
<iframe src="https://codesandbox.io/embed/github/metruzanca/infinite-canvas/master" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking" sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"></iframe>
```


references:
- https://github.com/TomHumphries/InfiniteCanvasWhiteboard/blob/master/index.html#L77
- https://betterprogramming.pub/how-to-create-a-figma-like-infinite-canvas-in-webgl-8be94f65674f