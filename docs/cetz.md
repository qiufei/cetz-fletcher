# https://cetz-package.github.io/docs/

## Advanced Typst Documentation
[Skip to main content](https://cetz-package.github.io/docs/advanced/#__docusaurus_skipToContent_fallback)

[int](https://typst.app/docs/reference/foundations/int)

## Advanced Context Features
[Skip to main content](https://cetz-package.github.io/docs/advanced/context/#__docusaurus_skipToContent_fallback)

## Custom Types Overview
[Skip to main content](https://cetz-package.github.io/docs/advanced/custom-types/#__docusaurus_skipToContent_fallback)

On this page

## [context](https://cetz-package.github.io/docs/advanced/custom-types\#context) 

A [dictionary](https://typst.app/docs/reference/foundations/dictionary) that holds the internal state of the canvas such as the element dictionary, the current transformation matrix, group and canvas unit length.
The following fields are considered stable:

- length (length): Length of one canvas unit as typst length
- transform (matrix): Current 4x4 transformation matrix
- background (none,color,gradient,tiling): The canvas' background
- debug (bool): True if the canvas' debug flag is set

## [element](https://cetz-package.github.io/docs/advanced/custom-types\#element) 

A function that, when called with a [context](https://cetz-package.github.io/docs/advanced/custom-types#context), returns some data that effects the canvas. Can also be an [array](https://typst.app/docs/reference/foundations/array) of this type.

- [context](https://cetz-package.github.io/docs/advanced/custom-types/#context)
- [element](https://cetz-package.github.io/docs/advanced/custom-types/#element)

## Advanced Drawing Functions
[Skip to main content](https://cetz-package.github.io/docs/advanced/draw-functions/#__docusaurus_skipToContent_fallback)

## Canvas Transformation Matrices
[Skip to main content](https://cetz-package.github.io/docs/advanced/transformations/#__docusaurus_skipToContent_fallback)

The default transformation matrix of the canvas is set to:
/// mat(1,0,−0.5,0;///0,−1,0.5,0;///0,0,0,0;///0,0,0,1)mat(1, 0,-0.5, 0;
/// 0,-1, 0.5, 0;
/// 0, 0, 0, 0;
/// 0, 0, 0, 1)mat(1,0,−0.5,0;///0,−1,0.5,0;///0,0,0,0;///0,0,0,1)

## Canvas Draw Functions
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/#__docusaurus_skipToContent_fallback)

Draw functions are the functions you import from the `draw` module and call within a `canvas` body. Depending on how and where you call them they can cause stuff to be drawn to the canvas or modify what is already on the canvas.

- [shapes](https://cetz-package.github.io/docs/api/draw-functions/shapes) For drawing shapes on the canvas.
- [grouping](https://cetz-package.github.io/docs/api/draw-functions/grouping) For grouping other draw functions together.
- [styling](https://cetz-package.github.io/docs/api/draw-functions/styling) For changing the styling of other draw functions.
- [transformations](https://cetz-package.github.io/docs/api/draw-functions/transformations) For transforming the points on the canvas.
- [projection](https://cetz-package.github.io/docs/api/draw-functions/projections)

## Drawing Functions Grouping
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/#__docusaurus_skipToContent_fallback)

Draw functions that allow collecting other draw functions together.

- [hide](https://cetz-package.github.io/docs/api/draw-functions/grouping/hide) Hides an element.
- [intersections](https://cetz-package.github.io/docs/api/draw-functions/grouping/intersections) Calculates the intersections between multiple elements.
- [group](https://cetz-package.github.io/docs/api/draw-functions/grouping/group) Groups one or more elements together.
- [anchor](https://cetz-package.github.io/docs/api/draw-functions/grouping/anchor) Creates a new anchor for the current group.
- [copy-anchors](https://cetz-package.github.io/docs/api/draw-functions/grouping/copy-anchors) Copies multiple anchors from one element into the current group.
- [set-ctx](https://cetz-package.github.io/docs/api/draw-functions/grouping/set-ctx) Allows modifying the current canvas context.
- [get-ctx](https://cetz-package.github.io/docs/api/draw-functions/grouping/get-ctx) Allows the reading of the current canvas context.
- [for-each-anchor](https://cetz-package.github.io/docs/api/draw-functions/grouping/for-each-anchor) Iterates throguh all named anchors of an element with a callback.
- [on-layer](https://cetz-package.github.io/docs/api/draw-functions/grouping/on-layer) Places elements on a specific layer.
- [floating](https://cetz-package.github.io/docs/api/draw-functions/grouping/floating) Places an element without affecting bounding boxes.

## Anchor Function Overview
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/anchor/#__docusaurus_skipToContent_fallback)

```
anchor(
name: str,position: coordinate,)
```

```codeBlockLines_e6Vv
// At the root scope
anchor("x", (1, 1))
// ...
circle("x", radius: .1)

```

![](<Base64-Image-Removed>)

#### name:

[str](https://typst.app/docs/reference/foundations/str)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/anchor/#name "Direct link to name")

The name of the anchor

#### position:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/anchor/#position "Direct link to position")

The position of the anchor

## Copy Anchors Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/copy-anchors/#__docusaurus_skipToContent_fallback)

```
copy-anchors(
element: str,filter: autoarray,)
```

Copies multiple anchors from one element into the current group. Panics when used outside of a group. Copied anchors will be accessible in the same way anchors created by the `anchor` element are.

#### element:

[str](https://typst.app/docs/reference/foundations/str)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/copy-anchors/#element )

The name of the element to copy anchors from.

#### filter:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/draw-functions/grouping/copy-anchors/#filter "Direct link to filter")

When set to `auto` all anchors will be copied to the group. An array of anchor names can instead be given so only the anchors that are in the element and the list will be copied over.

## Floating Elements Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/floating/#__docusaurus_skipToContent_fallback)

```
floating(
body: element,)
```

Places an element without affecting bounding boxes.

Floating elements are drawn to the canvas but are ignored when calculating bouding boxes. All other behaviours remain the same.

```codeBlockLines_e6Vv
group(name: "g", {
  content((1,0), [Normal])
  content((0,1), [Normal])
  floating(content((.5,1.5), [Floating]))
})
set-style(stroke: red)
rect("g.north-west", "g.south-east")

```

![](https://cetz-package.github.io/docs/assets/images/7fca9c-488ba9b725c27b9181e857a7fddf41b9.svg)

#### body:

[element](https://cetz-package.github.io/docs/advanced/custom-types#element)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/floating/#body "Direct link to body")

One or more elements to place

## For Each Anchor Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/for-each-anchor/#__docusaurus_skipToContent_fallback)

```
for-each-anchor(
name: str,callback: function,exclude: array,)
```

Iterates through all named anchors of an element and calls a callback for each one.

```codeBlockLines_e6Vv
// Label nodes anchors
rect((0, 0), (2,2), name: "my-rect")
for-each-anchor("my-rect", exclude: ("start", "mid", "end"), (name) => {
   content((), box(inset: 1pt, fill: white, text(8pt, [#name])), angle: -30deg)
})

```

![](https://cetz-package.github.io/docs/assets/images/d9c4e5-d025e1e2f3838b0e7b530ecbf1e2dccd.svg)

#### name:

[str](https://typst.app/docs/reference/foundations/str)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/for-each-anchor/#name "Direct link to name")

The name of the element with the anchors to loop through.

#### callback:

[function](https://typst.app/docs/reference/foundations/function)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/for-each-anchor/#callback "Direct link to callback")

A function that takes the anchor name and can return elements.

#### exclude:

[array](https://typst.app/docs/reference/foundations/array)

Default: `()` [​](https://cetz-package.github.io/docs/api/draw-functions/grouping/for-each-anchor/#exclude "Direct link to exclude")

An array of anchor names to not include in the loop.

## Get Context Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/get-ctx/#__docusaurus_skipToContent_fallback)

```
get-ctx(
callback: function,)
```

An advanced element that allows you to read the current [context](https://cetz-package.github.io/docs/advanced/custom-types#context) through a callback and return [element](https://cetz-package.github.io/docs/advanced/custom-types#element)s based on it.

```codeBlockLines_e6Vv
// Print the transformation matrix
get-ctx(ctx => {
  content((), [#repr(ctx.transform)])
})

```

![](https://cetz-package.github.io/docs/assets/images/a72054-5636910ee740fd2e3797f566af61e09d.svg)

#### callback:

[function](https://typst.app/docs/reference/foundations/function)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/get-ctx/#callback "Direct link to callback")

A function that accepts the [context](https://cetz-package.github.io/docs/advanced/custom-types#context) and can return elements.

## Element Grouping Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/#__docusaurus_skipToContent_fallback)

On this page

```
group(
body: elementsfunction,name: nonestr,anchor: nonestr,..style: style,)
```

Groups one or more elements together. This element acts as a scope, all state changes such as transformations and styling only affect the elements in the group. Elements after the group are not affected by the changes inside the group.

```codeBlockLines_e6Vv
// Create group
group({
  stroke(5pt)
  scale(.5); rotate(45deg)
  rect((-1,-1),(1,1))
})
rect((-1,-1),(1,1))

```

![](<Base64-Image-Removed>)

#### body:

elements or [function](https://typst.app/docs/reference/foundations/function)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/#body "Direct link to body")

Elements to group together. A least one is required. A function that accepts `ctx` and returns elements is also accepted.

#### anchor:

[none](https://typst.app/docs/reference/foundations/none/) or [str](https://typst.app/docs/reference/foundations/str)

Default: `none` [​](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/#anchor "Direct link to anchor")

Anchor to position the group and it's children relative to. For translation the difference between the groups `"default"` anchor and the passed anchor is used.

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/\#styling "Direct link to Styling")

_Root:_ `group`

#### padding:

[none](https://typst.app/docs/reference/foundations/none/) or [number](https://cetz-package.github.io/docs/basics/custom-types#number) or [array](https://typst.app/docs/reference/foundations/array) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

Default: `none` [​](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/#padding "Direct link to padding")

How much padding to add around the group's bounding box. `none` applies no padding. A number applies padding to all sides equally. A dictionary applies padding following Typst's `pad` function: [https://typst.app/docs/reference/layout/pad/](https://typst.app/docs/reference/layout/pad/). An array follows CSS like padding: `(y, x)`, `(top, x, bottom)` or `(top, right, bottom, left)`.

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/\#anchors "Direct link to Anchors")

Supports border and path anchors of the axis aligned bounding box of all the child elements of the group.

You can add custom named anchors to the group by using the [anchor](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/anchor) element while in the scope of said group, see [anchor](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/anchor) for more details.

The default anchor is `"center"` but this can be overridden by using [anchor](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/anchor) to place a new anchor called `"default"`.

When using named elements within a group, you can access the element's anchors outside of the group by using the implicit anchor coordinate. e.g. `"a.b.north"`

```codeBlockLines_e6Vv
group(name: "a", {
  circle((), name: "b")
})
circle("a.b.south", radius: 0.2)
circle((name: "a", anchor: "b.north"), radius: 0.2)

```

![](<Base64-Image-Removed>)

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/grouping/group/#anchors)

## Hide Elements Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/hide/#__docusaurus_skipToContent_fallback)

```
hide(
body: element,bounds: bool,)
```

Hides an element.

Hidden elements are not drawn to the canvas, are ignored when calculating bounding boxes and discarded by [merge-path](https://cetz-package.github.io/docs/api/draw-functions/grouping/shapes/merge-path). All other behaviours remain the same as a non-hidden element.

```codeBlockLines_e6Vv
set-style(radius: .5)
intersections("i", {
  circle((0,0), name: "a")
  circle((1,2), name: "b")
  // Use a hidden line to find the border intersections
  hide(line("a.center", "b.center"))
})
line("i.0", "i.1")

```

![](<Base64-Image-Removed>)

#### body:

[element](https://cetz-package.github.io/docs/advanced/custom-types#element)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/hide/#body "Direct link to body")

One or more elements to hide

#### bounds:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/draw-functions/grouping/hide/#bounds "Direct link to bounds")

If true, respect the bounding box of the hidden elements for resizing the canvas

## Path Intersections Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/intersections/#__docusaurus_skipToContent_fallback)

```
intersections(
name: str,..elements: elementsstr,samples: int,sort: nonefunction,)
```

Calculates the intersections between multiple paths and creates one anchor per intersection point.

All resulting anchors will be named numerically, starting at `0`. i.e., a call `intersections("a", ...)` will generate the anchors `"a.0"`, `"a.1"`, `"a.2"` to `"a.n"`, depending of the number of intersections.

```codeBlockLines_e6Vv
intersections("i", {
  circle((0, 0))
  bezier((0,0), (3,0), (1,-1), (2,1))
  line((0,-1), (0,1))
  rect((1.5,-1),(2.5,1))
})
for-each-anchor("i", (name) => {
  circle("i." + name, radius: .1, fill: blue)
})

```

![](<Base64-Image-Removed>)

You can also use named elements:

```codeBlockLines_e6Vv
circle((0,0), name: "a")
rect((0,0), (1,1), name: "b")
intersections("i", "a", "b")
for-each-anchor("i", (name) => {
  circle("i." + name, radius: .1, fill: blue)
})

```

![](<Base64-Image-Removed>)

You can calculate intersections with hidden elements by using [hide](https://cetz-package.github.io/docs/api/draw-functions/grouping/intersections/hide).

#### name:

[str](https://typst.app/docs/reference/foundations/str)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/intersections/#name "Direct link to name")

Name to prepend to the generated anchors. (Not to be confused with other `name` arguments that allow the use of anchor coordinates.)

#### ..elements:

elements or [str](https://typst.app/docs/reference/foundations/str)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/intersections/#elements "Direct link to ..elements")

Elements and/or element names to calculate intersections with. Elements referred to by name are (unlike elements passed) not drawn by the intersections function!

#### samples:

[int](https://typst.app/docs/reference/foundations/int)

Default: `10` [​](https://cetz-package.github.io/docs/api/draw-functions/grouping/intersections/#samples "Direct link to samples")

Number of samples to use for non-linear path segments. A higher sample count can give more precise results but worse performance.

#### sort:

[none](https://typst.app/docs/reference/foundations/none/) or [function](https://typst.app/docs/reference/foundations/function)

Default: `none` [​](https://cetz-package.github.io/docs/api/draw-functions/grouping/intersections/#sort "Direct link to sort")

A function of the form `(context, array<vector>) -> array<vector>`

that gets called with the list of intersection points.

CeTZ provides the following sorting functions:

- sorting.points-by-distace(points, reference: (0, 0, 0))
- sorting.points-by-angle(points, reference: (0, 0, 0))

## Layer Element Placement
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/on-layer/#__docusaurus_skipToContent_fallback)

```
on-layer(
layer: floatint,body: elementsfunction,)
```

Places elements on a specific layer.

A layer determines the position of an element in the draw queue. A lower layer is drawn before a higher layer.

Layers can be used to draw behind or in front of other elements, even if the other elements were created before or after. An example would be drawing a background behind a text, but using the text's calculated bounding box for positioning the background.

```codeBlockLines_e6Vv
// Draw something behind text
set-style(stroke: none)
content((0, 0), [This is an example.], name: "text")
on-layer(-1, {
  circle("text.north-east", radius: .3, fill: red)
  circle("text.south", radius: .4, fill: green)
  circle("text.north-west", radius: .2, fill: blue)
})

```

![](https://cetz-package.github.io/docs/assets/images/2948c3-972a11bb6f007ed38cf938326cabdcb4.svg)

#### layer:

[float](https://typst.app/docs/reference/foundations/float) or [int](https://typst.app/docs/reference/foundations/int)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/on-layer/#layer "Direct link to layer")

The layer to place the elements on. Elements placed without `on-layer` are always placed on layer 0.

#### body:

elements or [function](https://typst.app/docs/reference/foundations/function)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/on-layer/#body "Direct link to body")

Elements to draw on the layer specified. A function that accepts `ctx` and returns elements is also accepted.

## Element Scope Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/scope/#__docusaurus_skipToContent_fallback)

```
scope(
body: elementsfunction,)
```

This element acts as a scope, all state changes such as transformations and styling only affect the elements in the group. Elements after the scope are not affected by the changes inside the scope.
In contrast to `group`, the `scope` element does not create a named element itself and "leaks" body element to the outside.

#### body:

elements or [function](https://typst.app/docs/reference/foundations/function)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/scope/#body "Direct link to body")

Elements to group together. A least one is required. A function that accepts `ctx` and returns elements is also accepted.

## Canvas Context Modification
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/grouping/set-ctx/#__docusaurus_skipToContent_fallback)

```
set-ctx(
callback: function,)
```

An advanced element that allows you to modify the current canvas [context](https://cetz-package.github.io/docs/advanced/custom-types#context).
Note: The transformation matrix ( `transform`) is rounded after calling the `callback` function and therefore might be not exactly the matrix specified. This is due to rounding errors and should not cause any problems.

```codeBlockLines_e6Vv
// Setting a custom transformation matrix
set-ctx(ctx => {
  let mat = ((1, 0, .5, 0),
             (0, 1,  0, 0),
             (0, 0,  1, 0),
             (0, 0,  0, 1))
  ctx.transform = mat
  return ctx
})
circle((z: 0), fill: red)
circle((z: 1), fill: blue)
circle((z: 2), fill: green)

```

![](<Base64-Image-Removed>)

#### callback:

[function](https://typst.app/docs/reference/foundations/function)

[​](https://cetz-package.github.io/docs/api/draw-functions/grouping/set-ctx/#callback "Direct link to callback")

A function that accepts the context dictionary and only returns a new one.

## Projection Functions Guide
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/projections/#__docusaurus_skipToContent_fallback)

## Draw on XY Plane
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/projections/on-xy/#__docusaurus_skipToContent_fallback)

```
on-xy(
z: number,body: element,)
```

Draw elements on the xy-plane with optional z offset.

All vertices of all elements will be changed in the following way: (xyzargument)\\begin{pmatrix} x \\\ y \\\ z\_\\text{argument}\\end{pmatrix}​xyzargument​​​, where zargumentz\_\\text{argument}zargument​ is the z-value given as argument.

```codeBlockLines_e6Vv
on-xy({
  rect((-1, -1), (1, 1))
})

```

![](<Base64-Image-Removed>)

#### z:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0` [​](https://cetz-package.github.io/docs/api/draw-functions/projections/on-xy/#z "Direct link to z")

Z offset for all coordinates

#### body:

[element](https://cetz-package.github.io/docs/advanced/custom-types#element)

[​](https://cetz-package.github.io/docs/api/draw-functions/projections/on-xy/#body "Direct link to body")

Elements to draw

## Draw on XZ Plane
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/projections/on-xz/#__docusaurus_skipToContent_fallback)

```
on-xz(
y: number,body: element,)
```

Draw elements on the xz-plane with optional y offset.

All vertices of all elements will be changed in the following way: (xyargumenty)\\begin{pmatrix} x \\\ y\_\\text{argument} \\\ y \\end{pmatrix}​xyargument​y​​, where yargumenty\_\\text{argument}yargument​ is the y-value given as argument.

```codeBlockLines_e6Vv
on-xz({
  rect((-1, -1), (1, 1))
})

```

![](<Base64-Image-Removed>)

#### y:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0` [​](https://cetz-package.github.io/docs/api/draw-functions/projections/on-xz/#y "Direct link to y")

Y offset for all coordinates

#### body:

[element](https://cetz-package.github.io/docs/advanced/custom-types#element)

[​](https://cetz-package.github.io/docs/api/draw-functions/projections/on-xz/#body "Direct link to body")

Elements to draw

## Draw on YZ Plane
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/projections/on-yz/#__docusaurus_skipToContent_fallback)

```
on-yz(
x: number,body: element,)
```

Draw elements on the yz-plane with optional x offset.

All vertices of all elements will be changed in the following way: (xargumentxy)\\begin{pmatrix} x\_\\text{argument} \\\ x \\\ y \\end{pmatrix}​xargument​xy​​, where xargumentx\_\\text{argument}xargument​ is the x-value given as argument.

```codeBlockLines_e6Vv
on-yz({
  rect((-1, -1), (1, 1))
})

```

![](<Base64-Image-Removed>)

#### x:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0` [​](https://cetz-package.github.io/docs/api/draw-functions/projections/on-yz/#x "Direct link to x")

X offset for all coordinates

#### body:

[element](https://cetz-package.github.io/docs/advanced/custom-types#element)

[​](https://cetz-package.github.io/docs/api/draw-functions/projections/on-yz/#body "Direct link to body")

Elements to draw

## Orthographic Projection Setup
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/projections/ortho/#__docusaurus_skipToContent_fallback)

```
ortho(
x: angle,y: angle,z: angle,sorted: bool,cull-face: nonestr,reset-transform: bool,body: element,name: ,)
```

Set-up an orthographic projection environment.

This is a transformation matrix that rotates elements around the x, the y and the z axis by the parameters given.

By default an isometric projection (x ≈ 35.264°, y = 45°) is set.

```codeBlockLines_e6Vv
ortho({
  on-xz({
    rect((-1,-1), (1,1))
  })
})

```

![](<Base64-Image-Removed>)

#### x:

[angle](https://typst.app/docs/reference/layout/angle)

Default: `35.264deg` [​](https://cetz-package.github.io/docs/api/draw-functions/projections/ortho/#x "Direct link to x")

X-axis rotation angle

#### y:

[angle](https://typst.app/docs/reference/layout/angle)

Default: `45deg` [​](https://cetz-package.github.io/docs/api/draw-functions/projections/ortho/#y "Direct link to y")

Y-axis rotation angle

#### z:

[angle](https://typst.app/docs/reference/layout/angle)

Default: `0deg` [​](https://cetz-package.github.io/docs/api/draw-functions/projections/ortho/#z "Direct link to z")

Z-axis rotation angle

#### sorted:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `true` [​](https://cetz-package.github.io/docs/api/draw-functions/projections/ortho/#sorted "Direct link to sorted")

Sort drawables by maximum distance (front to back)

#### cull-face:

[none](https://typst.app/docs/reference/foundations/none/) or [str](https://typst.app/docs/reference/foundations/str)

Default: `none` [​](https://cetz-package.github.io/docs/api/draw-functions/projections/ortho/#cullface "Direct link to cull-face")

Enable back-face culling if set to `"cw"` for clockwise

or `"ccw"` for counter-clockwise. Polygons of the specified order will not get drawn.

#### reset-transform:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/draw-functions/projections/ortho/#resettransform "Direct link to reset-transform")

Ignore the current transformation matrix

#### body:

[element](https://cetz-package.github.io/docs/advanced/custom-types#element)

[​](https://cetz-package.github.io/docs/api/draw-functions/projections/ortho/#body "Direct link to body")

Elements to draw

## Canvas Shape Drawing
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/#__docusaurus_skipToContent_fallback)

Draw functions that draw shapes onto the canvas, be that lines, circles or curves.

- [circle](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle) Draws a circle at a point.
- [arc](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc) Draws an arc between two points.
- [mark](https://cetz-package.github.io/docs/api/draw-functions/shapes/mark) Draws a mark at a point in a direction.
- [line](https://cetz-package.github.io/docs/api/draw-functions/shapes/line) Draws a line between two points, or a line strip between 3 or more points.
- [polygon](https://cetz-package.github.io/docs/api/draw-functions/shapes/polygon) Draws a regular polygon.
- [grid](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid) Draws a grid.
- [content](https://cetz-package.github.io/docs/api/draw-functions/shapes/content) Places some content on the canvas.
- [rect](https://cetz-package.github.io/docs/api/draw-functions/shapes/rect) Draws a rectangle between two points.
- [bezier](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier) Draws a bezier with control points.
- [hobby](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby) Draws a hobby curve.
- [catmull](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull) Draws a Catmull-Rom curve.
- [merge-path](https://cetz-package.github.io/docs/api/draw-functions/shapes/merge-path) Merges the paths of other draw functions into one continuous path.

## Drawing Arcs and Segments
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#__docusaurus_skipToContent_fallback)

On this page

```
arc(
position: coordinate,start: autoangle,stop: autoangle,delta: autoangle,name: nonestr,anchor: nonestr,..style: style,)
```

Draws a circular segment.

```codeBlockLines_e6Vv
arc((0,0), start: 45deg, stop: 135deg)
arc((0,-0.5), start: 45deg, delta: 90deg, mode: "CLOSE")
arc((0,-1), stop: 135deg, delta: 90deg, mode: "PIE")

```

![](<Base64-Image-Removed>)

Note that two of the three angle arguments ( `start`, `stop` and `delta`) must be set.
The current position `()` gets updated to the arc's end coordinate (anchor `arc-end`).

#### position:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#position "Direct link to position")

Position to place the arc at.

#### start:

[auto](https://typst.app/docs/reference/foundations/auto/) or [angle](https://typst.app/docs/reference/layout/angle)

Default: `auto` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#start "Direct link to start")

The angle at which the arc should start. Remember that `0deg` points directly towards the right and `90deg` points up.

#### stop:

[auto](https://typst.app/docs/reference/foundations/auto/) or [angle](https://typst.app/docs/reference/layout/angle)

Default: `auto` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#stop "Direct link to stop")

The angle at which the arc should stop.

#### delta:

[auto](https://typst.app/docs/reference/foundations/auto/) or [angle](https://typst.app/docs/reference/layout/angle)

Default: `auto` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#delta "Direct link to delta")

The change in angle away start or stop.

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/\#styling "Direct link to Styling")

_Root_: `arc`

#### radius:

[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [array](https://typst.app/docs/reference/foundations/array)

Default: `1` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#radius "Direct link to radius")

The radius of the arc. An elliptical arc can be created by passing a tuple of numbers where the first element is the x radius and the second element is the y radius.

#### mode:

[str](https://typst.app/docs/reference/foundations/str)

Default: `"OPEN"` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#mode "Direct link to mode")

The options are: `"OPEN"` no additional lines are drawn so just the arc is shown; `"CLOSE"` a line is drawn from the start to the end of the arc creating a circular segment; `"PIE"` lines are drawn from the start and end of the arc to the origin creating a circular sector.

#### update-position:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `true` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#updateposition "Direct link to update-position")

Update the current canvas position to the arc's end point (anchor `"arc-end"`). This overrides the default of `true`, that allows chaining of (arc) elements.

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/\#anchors "Direct link to Anchors")

Supports border and path anchors.

- **arc-start**: The position at which the arc's curve starts, this is the default.
- **arc-end**: The position of the arc's curve end.
- **arc-center**: The midpoint of the arc's curve.
- **center**: The center of the arc, this position changes depending on if the arc is closed or not.
- **chord-center**: Center of chord of the arc drawn between the start and end point.
- **origin**: The origin of the arc's circle.

## arc-through [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/\#arc-through "Direct link to arc-through")

```
arc-through(
a: coordinate,b: coordinate,c: coordinate,name: nonestr,..style: style,)
```

Draws an arc that passes through three points a, b and c.

Note that all three points must not lie on a straight line, otherwise
the function fails.

```codeBlockLines_e6Vv
arc-through((0,1), (1,1), (1,0))

```

![](<Base64-Image-Removed>)

#### a:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#a "Direct link to a")

Start position of the arc

#### b:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#b "Direct link to b")

Position the arc passes through

#### c:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#c "Direct link to c")

End position of the arc

### Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/\#styling "Direct link to Styling")

_Root_: `arc`

Uses the same styling as [arc](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/arc#styling)

### Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/\#anchors "Direct link to Anchors")

For anchors see [arc](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/arc#anchors).

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#anchors)
- [arc-through](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#arc-through)
  - [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#styling)
  - [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/arc/#anchors)

## Bezier Curve Functions
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#__docusaurus_skipToContent_fallback)

On this page

```
bezier(
start: coordinate,end: coordinate,..ctrl-style: coordinatestyle,name: nonestr,)
```

Draws a quadratic or cubic bezier curve

```codeBlockLines_e6Vv
let (a, b, c) = ((0, 0), (2, 0), (1, 1))
line(a, c,  b, stroke: gray)
bezier(a, b, c)

let (a, b, c, d) = ((0, -1), (2, -1), (.5, -2), (1.5, 0))
line(a, c, d, b, stroke: gray)
bezier(a, b, c, d)

```

![](<Base64-Image-Removed>)

#### start:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#start "Direct link to start")

Start position

#### end:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#end "Direct link to end")

End position (last coordinate)

#### ..ctrl-style:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate) or [style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#ctrlstyle "Direct link to ..ctrl-style")

The first two positional arguments are taken as cubic bezier control points, where the first is the start control point and the second is the end control point. One control point can be given for a quadratic bezier curve instead. Named arguments are for styling.

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/\#styling "Direct link to Styling")

_Root_ `bezier`

Supports marks.

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/\#anchors "Direct link to Anchors")

Supports path anchors.

- **ctrl-n**: nth control point where n is an integer starting at 0

## bezier-through [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/\#bezier-through "Direct link to bezier-through")

```
bezier-through(
start: coordinate,pass-through: coordinate,end: coordinate,name: nonestr,..style: style,)
```

Draws a cubic bezier curve through a set of three points. See [bezier](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/bezier) for style and anchor details.

```codeBlockLines_e6Vv
let (a, b, c) = ((0, 0), (1, 1), (2, -1))
line(a, b, c, stroke: gray)
bezier-through(a, b, c, name: "b")

// Show calculated control points
line(a, "b.ctrl-0", "b.ctrl-1", c, stroke: gray)

```

![](<Base64-Image-Removed>)

#### start:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#start "Direct link to start")

The position to start the curve.

#### pass-through:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#passthrough "Direct link to pass-through")

The position to pass the curve through.

#### end:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#end "Direct link to end")

The position to end the curve.

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#anchors)
- [bezier-through](https://cetz-package.github.io/docs/api/draw-functions/shapes/bezier/#bezier-through)

## Catmull-Rom Curve
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull/#__docusaurus_skipToContent_fallback)

On this page

```
catmull(
..pts-style: coordinatestyle,close: bool,name: nonestr,)
```

Draws a Catmull-Rom curve through a set of points.

```codeBlockLines_e6Vv
catmull((0,0), (1,1), (2,-1), (3,0), tension: .4, stroke: blue)
catmull((0,0), (1,1), (2,-1), (3,0), tension: .5, stroke: red)

```

![](<Base64-Image-Removed>)

#### ..pts-style:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate) or [style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull/#ptsstyle "Direct link to ..pts-style")

Positional arguments should be coordinates that the curve should pass through. Named arguments are for styling.

#### close:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull/#close "Direct link to close")

Closes the curve with a straight line between the start and end of the curve.

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull/\#styling "Direct link to Styling")

_Root_: `catmull`

Supports marks.

#### tension:

[float](https://typst.app/docs/reference/foundations/float)

Default: `0.5` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull/#tension "Direct link to tension")

How tight the curve should fit to the points. The higher the tension the less curvy the curve.

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull/\#anchors "Direct link to Anchors")

Supports path anchors.

- **pt-n**: The nth given position (0 indexed so "pt-0" is equal to "start")

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull/#anchors)

## Circle Drawing Functions
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#__docusaurus_skipToContent_fallback)

On this page

```
circle(
..points-style: coordinatestyle,name: nonestr,anchor: nonestr,)
```

Draws a circle or ellipse.

```codeBlockLines_e6Vv
circle((0,0))
// Draws an ellipse
circle((0,-2), radius: (0.75, 0.5))
// Draws a circle at (0, 2) through point (1, 3)
circle((0,2), (rel: (1,1)))

```

![](<Base64-Image-Removed>)

#### ..points-style:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate) or [style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#pointsstyle "Direct link to ..points-style")

The position to place the circle on.

If given two coordinates, the distance between them is used as radius.
If given a single coordinate, the radius can be set via the `radius` (style)
argument.

### Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/\#styling "Direct link to Styling")

_Root_: `circle`

#### radius:

[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [array](https://typst.app/docs/reference/foundations/array)

Default: `1` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#radius "Direct link to radius")

A number that defines the size of the circle's radius. Can also be set to a tuple of two numbers to define the radii of an ellipse, the first number is the `x` radius and the second is the `y` radius.

### Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/\#anchors "Direct link to Anchors")

Supports border and path anchors. The `"center"` anchor is the default.

## circle-through [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/\#circle-through "Direct link to circle-through")

```
circle-through(
a: coordinate,b: coordinate,c: coordinate,name: nonestr,anchor: nonestr,..style: style,)
```

Draws a circle through three coordinates.

```codeBlockLines_e6Vv
let (a, b, c) = ((0,0), (2,-.5), (1,1))
line(a, b, c, close: true, stroke: gray)
circle-through(a, b, c, name: "c")
circle("c.center", radius: .05, fill: red)

```

![](<Base64-Image-Removed>)

#### a:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#a "Direct link to a")

Coordinate a.

#### b:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#b "Direct link to b")

Coordinate b.

#### c:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#c "Direct link to c")

Coordinate c.

### Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/\#styling "Direct link to Styling")

_Root_: `circle`

`circle-through` has the same styling as [circle](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/circle#styling) except for `radius` as the circle's radius is calculated by the given coordinates.

### Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/\#anchors "Direct link to Anchors")

Supports the same anchors as [circle](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/circle#anchors) as well as:

- **a**: Coordinate a
- **b**: Coordinate b
- **c**: Coordinate c

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#anchors)
- [circle-through](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#circle-through)
  - [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#styling)
  - [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/circle/#anchors)

## Typst Content Positioning
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/#__docusaurus_skipToContent_fallback)

On this page

```
content(
..args-style: coordinatecontentstyle,angle: anglecoordinate,anchor: nonestr,name: nonestr,)
```

Positions Typst content in the canvas. Note that the content itself is not transformed only its position is.

```codeBlockLines_e6Vv
content((0,0), [Hello World!])

```

![](https://cetz-package.github.io/docs/assets/images/8ea959-3c5971843181495e7c2806abc6cd76c1.svg)

To put text on a line you can let the function calculate the angle between its position and a second coordinate by passing it to `angle`:

```codeBlockLines_e6Vv
line((0, 0), (3, 1), name: "line")
content(
  ("line.start", 50%, "line.end"),
  angle: "line.end",
  padding: .1,
  anchor: "south",
  [Text on a line]
)

```

![](https://cetz-package.github.io/docs/assets/images/e4e44b-9596f6fa920fdce5946676a2a8a995fb.svg)

```codeBlockLines_e6Vv
// Place content in a rect between two coordinates
content(
  (0, 0),
  (2, 2),
  box(
    par(justify: false)[This is a long text.],
    stroke: 1pt,
    width: 100%,
    height: 100%,
    inset: 1em
  )
)

```

![](https://cetz-package.github.io/docs/assets/images/c5ca70-e03719c9ff175c2a3f553182e8f055ca.svg)

#### ..args-style:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate) or [content](https://typst.app/docs/reference/foundations/content) or [style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/#argsstyle "Direct link to ..args-style")

When one coordinate is given as a positional argument, the content will be placed at that position. When two coordinates are given as positional arguments, the content will be placed inside a rectangle between the two positions. All named arguments are styling and any additional positional arguments will panic.

#### angle:

[angle](https://typst.app/docs/reference/layout/angle) or [coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

Default: `0deg` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/#angle "Direct link to angle")

Rotates the content by the given angle. A coordinate can be given to rotate the content by the angle between it and the first coordinate given in `args`. This effectively points the right hand side of the content towards the coordinate. This currently exists because Typst's rotate function does not change the width and height of content.

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/\#styling "Direct link to Styling")

_Root_: `content`

#### padding:

[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

Default: `0` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/#padding "Direct link to padding")

Sets the spacing around content. Can be a single number to set padding on all sides or a dictionary to specify each side specifically. The dictionary follows Typst's `pad` function: [https://typst.app/docs/reference/layout/pad/](https://typst.app/docs/reference/layout/pad/)

#### frame:

[str](https://typst.app/docs/reference/foundations/str) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/#frame "Direct link to frame")

Sets the frame style. Can be [none](https://typst.app/docs/reference/foundations/none/), `"rect"` or `"circle"` and inherits the `stroke` and `fill` style.

#### auto-scale:

[bool](https://typst.app/docs/reference/foundations/bool)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/#autoscale "Direct link to auto-scale")

If `true`, apply current canvas scaling to the content. Defaults to `false`.

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/\#anchors "Direct link to Anchors")

Supports border anchors, the default anchor is set to **center**.

- **mid**: Content center, from baseline to top bounds
- **mid-east**: Content center extended to the east
- **mid-west**: Content center extended to the west
- **base**: Horizontally centered baseline of the content
- **base-east**: Baseline height extended to the east
- **base-west**: Baseline height extended to the west
- **text**: Position at the content start on the baseline of the content

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/content/#anchors)

## Grid Drawing Functions
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid/#__docusaurus_skipToContent_fallback)

On this page

```
grid(
from: coordinate,to: coordinate,name: nonestr,..style: style,)
```

Draws a grid between two coordinates

```codeBlockLines_e6Vv
// Draw a grid
grid((0,0), (2,2))

// Draw a smaller blue grid
grid((1,1), (2,2), stroke: blue, step: .25)

```

![](<Base64-Image-Removed>)

#### from:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid/#from "Direct link to from")

The top left of the grid

#### to:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid/#to "Direct link to to")

The bottom right of the grid

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid/\#styling "Direct link to Styling")

_Root_: `grid`

#### step:

[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [array](https://typst.app/docs/reference/foundations/array) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

Default: `1` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid/#step "Direct link to step")

Distance between grid lines. A distance of 111 means to draw a grid line every 111 length units in x- and y-direction. If given a dictionary with `x` and `y` keys or a tuple, the step is set per axis.

#### help-lines:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid/#helplines "Direct link to help-lines")

If true, force the stroke style to `gray + 0.2pt`

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid/\#anchors "Direct link to Anchors")

Supports border anchors.

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/grid/#anchors)

## Hobby Curve Drawing
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/#__docusaurus_skipToContent_fallback)

On this page

```
hobby(
..pts-style: coordinatestyle,ta: autoarray,tb: autoarray,close: bool,name: nonestr,)
```

Draws a Hobby curve through a set of points.

```codeBlockLines_e6Vv
hobby((0, 0), (1, 1), (2, -1), (3, 0), omega: 0, stroke: blue)
hobby((0, 0), (1, 1), (2, -1), (3, 0), omega: 1, stroke: red)

```

![](<Base64-Image-Removed>)

#### ..pts-style:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate) or [style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/#ptsstyle "Direct link to ..pts-style")

Positional arguments are the coordinates to use to draw the curve with, a minimum of two is required. Named arguments are for styling.

#### tb:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/#tb "Direct link to tb")

Incoming tension at `pts.at(n+1)` from `pts.at(n)` to `pts.at(n+1)`. The number given must be one less than the number of points.

#### ta:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/#ta "Direct link to ta")

Outgoing tension at `pts.at(n)` from `pts.at(n)` to `pts.at(n+1)`. The number given must be one less than the number of points.

#### close:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/#close "Direct link to close")

Closes the curve with a proper smooth curve between the start and end of the curve.

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/\#styling "Direct link to Styling")

_Root_ `hobby`

Supports marks.

#### omega:

[array](https://typst.app/docs/reference/foundations/array)

Default: `(1, 1)` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/#omega "Direct link to omega")

A tuple of floats that describe how curly the curve should be at each endpoint. When the curl is close to zero, the spline approaches a straight line near the endpoints. When the curl is close to one, it approaches a circular arc.

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/\#anchors "Direct link to Anchors")

Supports path anchors.

- **pt-n**: The nth given position (0 indexed, so "pt-0" is equal to "start")

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/hobby/#anchors)

## Line Drawing Functions
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/line/#__docusaurus_skipToContent_fallback)

On this page

```
line(
..pts-style: coordinatestyle,close: bool,name: nonestr,)
```

Draws a line, more than two points can be given to create a line-strip.

```codeBlockLines_e6Vv
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))
line((-1, -1), (-0.5, 0.5), (0.5, 0.5), (1, -1), close: true)

```

![](<Base64-Image-Removed>)

If the first or last coordinates are given as the name of an element,
that has a `"default"` anchor, the intersection of that element's border
and a line from the first or last two coordinates given is used as coordinate.
This is useful to span a line between the borders of two elements.

```codeBlockLines_e6Vv
circle((1,2), radius: .5, name: "a")
rect((2,1), (rel: (1,1)), name: "b")
line("a", "b")

```

![](<Base64-Image-Removed>)

#### ..pts-style:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate) or [style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/line/#ptsstyle "Direct link to ..pts-style")

Positional two or more coordinates to draw lines between. Accepts style key-value pairs.

#### close:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/line/#close "Direct link to close")

If true, the line-strip gets closed to form a polygon

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/line/\#styling "Direct link to Styling")

_Root:_ `line`

Supports mark styling.

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/line/\#anchors "Direct link to Anchors")

Supports path anchors.

- **centroid**: The centroid anchor is calculated for _closed non self-intersecting_ polygons if all vertices share the same z value.

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/line/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/line/#anchors)

## Mark Drawing Functions
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/mark/#__docusaurus_skipToContent_fallback)

On this page

```
mark(
from: coordinate,to: coordinateangle,..style: style,)
```

Draws a single mark pointing towards a target coordinate.

```codeBlockLines_e6Vv
mark((0,0), (1,0), symbol: ">", fill: black)
mark((0,0), (1,1), symbol: "stealth", scale: 3, fill: black)

```

![](<Base64-Image-Removed>)

Note: To place a mark centered at the first coodinate ( `from`) use
the marks `anchor: "center"` style.

#### from:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/mark/#from "Direct link to from")

The position to place the mark.

#### to:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate) or [angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/mark/#to "Direct link to to")

The position or angle the mark should point towards.

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/mark/\#styling "Direct link to Styling")

_Root_: `mark`

You can directly use the styling from [Mark Styling](https://cetz-package.github.io/docs/basics/marks).

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/mark/#styling)

## Merge Paths Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/merge-path/#__docusaurus_skipToContent_fallback)

On this page

```
merge-path(
body: elements,close: bool,name: nonestr,..style: style,)
```

Merges two or more paths by concattenating their elements. Anchors and visual styling, such as `stroke` and `fill`, are not preserved. When an element's path does not start at the same position the previous element's path ended, a straight line is drawn between them so that the final path is continuous. You must then pay attention to the direction in which element paths are drawn.

```codeBlockLines_e6Vv
merge-path(fill: white, {
  line((0, 0), (1, 0))
  bezier((), (0, 0), (1,1), (0,1))
})

```

![](<Base64-Image-Removed>)

Elements hidden via @@hide() are ignored.

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/merge-path/\#anchors "Direct link to Anchors")

**centroid**: Centroid of the _closed and non self-intersecting_ shape. Only exists if `close` is true.
Supports path anchors and shapes where all vertices share the same z-value.

#### body:

elements

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/merge-path/#body "Direct link to body")

Elements with paths to be merged together.

#### close:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/merge-path/#close "Direct link to close")

Close the path with a straight line from the start of the path to its end.

- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/merge-path/#anchors)

## Polygon Drawing Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/polygon/#__docusaurus_skipToContent_fallback)

On this page

```
polygon(
origin: coordinate,sides: int,angle: angle,name: nonestr,anchor: ,..style: ,)
```

Draws a regular polygon.

```codeBlockLines_e6Vv
polygon((0,0), 3, angle: 90deg)
polygon((2,0), 5)
polygon((4,0), 7)

```

![](<Base64-Image-Removed>)

#### origin:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/polygon/#origin "Direct link to origin")

Coordinate to draw the polygon at

#### sides:

[int](https://typst.app/docs/reference/foundations/int)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/polygon/#sides "Direct link to sides")

Number of sides of the polygon (>= 3)

#### angle:

[angle](https://typst.app/docs/reference/layout/angle)

Default: `0deg` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/polygon/#angle "Direct link to angle")

Angle angle to rotate the polygon arround its origin

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/polygon/\#styling "Direct link to Styling")

_Root_: `polygon`

#### radius:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `1` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/polygon/#radius "Direct link to radius")

Radius of the polygon

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/polygon/#styling)

## Rectangle Drawing Functions
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/shapes/rect/#__docusaurus_skipToContent_fallback)

On this page

```
rect(
a: coordinate,b: coordinate,name: nonestr,anchor: nonestr,..style: style,)
```

Draws a rectangle between two coordinates.

```codeBlockLines_e6Vv
rect((0,0), (1,1))
rect(
  (-.5, -.5),
  (rel: (2, 2)),
  radius: (
    north-east: (100%, .5),
    south-west: (100%, .5),
    rest: .2
  ),
  stroke: red
)
rect((-1, -1), (rel: (3, 3)), radius: .5, stroke: blue)

```

![](<Base64-Image-Removed>)

#### a:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/rect/#a "Direct link to a")

Coordinate of the bottom left corner of the rectangle.

#### b:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/shapes/rect/#b "Direct link to b")

Coordinate of the top right corner of the rectangle. You can draw a rectangle with a specified width and height by using relative coordinates for this parameter `(rel: (width, height))`.

## Styling [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/rect/\#styling "Direct link to Styling")

_Root_: `rect`

#### radius:

[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [ratio](https://typst.app/docs/reference/layout/ratio) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

Default: `0` [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/rect/#radius "Direct link to radius")

The rectangle's corner radius. If set to a single number, that radius is applied to all four corners of the rectangle. If passed a dictionary you can set the radii per corner. The following keys support either a [number](https://cetz-package.github.io/docs/basics/custom-types#number), [ratio](https://typst.app/docs/reference/layout/ratio) or an array of [number](https://cetz-package.github.io/docs/basics/custom-types#number) or [ratio](https://typst.app/docs/reference/layout/ratio) for specifying a different x- and y-radius: `north`, `east`, `south`, `west`, `north-west`, `north-east`, `south-west` and `south-east`. To set a default value for remaining corners, the `rest` key can be used.

Ratio values are relative to the rectangle's width and height.

```codeBlockLines_e6Vv
rect((0,0), (rel: (1,1)), radius: 0)
rect((2,0), (rel: (1,1)), radius: 25%)
rect((4,0), (rel: (1,1)), radius: (north: 50%))
rect((6,0), (rel: (1,1)), radius: (north-east: 50%))
rect((8,0), (rel: (1,1)), radius: (south-west: 0, rest: 50%))
rect((10,0), (rel: (1,1)), radius: (rest: (20%, 50%)))

```

![](<Base64-Image-Removed>)

## Anchors [​](https://cetz-package.github.io/docs/api/draw-functions/shapes/rect/\#anchors "Direct link to Anchors")

Supports border and path anchors. It's default is the `"center"` anchor.

- [Styling](https://cetz-package.github.io/docs/api/draw-functions/shapes/rect/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/draw-functions/shapes/rect/#anchors)

## Element Styling Functions
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/styling/#__docusaurus_skipToContent_fallback)

Draw functions that change how other elements are drawn.

- [set-style](https://cetz-package.github.io/docs/api/draw-functions/styling/set-style) Sets the styling for elements.
- [fill](https://cetz-package.github.io/docs/api/draw-functions/styling/fill) Shorthand to set the fill of elements.
- [stroke](https://cetz-package.github.io/docs/api/draw-functions/styling/stroke) Shorthand to set the stroke of elements.

## Current Fill Style
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/styling/fill/#__docusaurus_skipToContent_fallback)

```
fill(
fill: paint,)
```

Set current fill style

Shorthand for `set-style(fill: <fill>)`

#### fill:

paint

[​](https://cetz-package.github.io/docs/api/draw-functions/styling/fill/#fill "Direct link to fill")

Fill style

## Set Current Style
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/styling/set-style/#__docusaurus_skipToContent_fallback)

```
set-style(
..style: style,)
```

Set current style

#### ..style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/draw-functions/styling/set-style/#style "Direct link to ..style")

Style key-value pairs

## Stroke Style Settings
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/styling/stroke/#__docusaurus_skipToContent_fallback)

```
stroke(
stroke: stroke,)
```

Set current stroke style

Shorthand for `set-style(stroke: <fill>)`

#### stroke:

[stroke](https://typst.app/docs/reference/visualize/stroke)

[​](https://cetz-package.github.io/docs/api/draw-functions/styling/stroke/#stroke "Direct link to stroke")

Stroke style

## Transformation Functions Overview
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/transformations/#__docusaurus_skipToContent_fallback)

All transformation functions push a transformation matrix onto the current transform stack. To apply transformations scoped use the [`group`](https://cetz-package.github.io/docs/api/draw-functions/grouping/group) draw function.

Transformation matrices get multiplied in the following order:

Mworld=Mworld⋅MlocalM\_{\\text{world}} = M\_\\text{world} \\cdot M\_\\text{local}Mworld​=Mworld​⋅Mlocal​

## Move To Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/transformations/move-to/#__docusaurus_skipToContent_fallback)

```
move-to(
pt: coordinate,)
```

Sets the previous coordinate.

The previous coordinate can be used via `()` (empty coordinate).
It is also used as base for relative coordinates if not specified
otherwise.

```codeBlockLines_e6Vv
circle((), radius: .25)
move-to((1,0))
circle((), radius: .15)

```

![](<Base64-Image-Removed>)

#### pt:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/transformations/move-to/#pt "Direct link to pt")

The coordinate to move to.

## Transformation Rotation
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/transformations/rotate/#__docusaurus_skipToContent_fallback)

```
rotate(
..angles: angle,origin: nonecoordinate,)
```

Rotates the transformation matrix on the z-axis by a given angle or other axes when specified.

```codeBlockLines_e6Vv
// Rotate on z-axis
rotate(z: 45deg)
rect((-1,-1), (1,1))
// Rotate on y-axis
rotate(y: 80deg)
circle((0,0))

```

![](<Base64-Image-Removed>)

#### ..angles:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/draw-functions/transformations/rotate/#angles "Direct link to ..angles")

A single angle as a positional argument to rotate on the z-axis by.

Named arguments of `x`, `y` or `z` can be given to rotate on their respective axis.
You can give named arguments of `yaw`, `pitch` or `roll`, too.

#### origin:

[none](https://typst.app/docs/reference/foundations/none/) or [coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

Default: `none` [​](https://cetz-package.github.io/docs/api/draw-functions/transformations/rotate/#origin "Direct link to origin")

Origin to rotate around, or (0, 0, 0) if set to `none`.

## Scale Transformation Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/transformations/scale/#__docusaurus_skipToContent_fallback)

```
scale(
..args: floatratio,origin: nonecoordinate,)
```

Scales the transformation matrix by the given factor(s).

```codeBlockLines_e6Vv
// Scale the y-axis
scale(y: 50%)
circle((0,0))

```

![](<Base64-Image-Removed>)

Note that content like text does not scale automatically. See `auto-scale` styling of content for that.

#### ..args:

[float](https://typst.app/docs/reference/foundations/float) or [ratio](https://typst.app/docs/reference/layout/ratio)

[​](https://cetz-package.github.io/docs/api/draw-functions/transformations/scale/#args "Direct link to ..args")

A single value to scale the transformation matrix by or per axis

scaling factors. Accepts a single float or ratio value or any combination of the named arguments
`x`, `y` and `z` to set per axis scaling factors. A ratio of 100% is the same as the value 111.

#### origin:

[none](https://typst.app/docs/reference/foundations/none/) or [coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

Default: `none` [​](https://cetz-package.github.io/docs/api/draw-functions/transformations/scale/#origin "Direct link to origin")

Origin to rotate around, or (0, 0, 0) if set to `none`.

## Set Origin Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/transformations/set-origin/#__docusaurus_skipToContent_fallback)

```
set-origin(
origin: coordinate,)
```

Sets the given position as the new origin `(0, 0, 0)`

```codeBlockLines_e6Vv
// Outer rect
rect((0,0), (2,2), name: "r")
// Move origin to top edge
set-origin("r.north")
circle((0, 0), radius: .1)

```

![](<Base64-Image-Removed>)

#### origin:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/transformations/set-origin/#origin "Direct link to origin")

Coordinate to set as new origin `(0,0,0)`

## Set Transformation Matrix
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/transformations/set-transform/#__docusaurus_skipToContent_fallback)

```
set-transform(
mat: nonematrix,)
```

Sets the transformation matrix.

#### mat:

[none](https://typst.app/docs/reference/foundations/none/) or [matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/draw-functions/transformations/set-transform/#mat "Direct link to mat")

The 4x4 transformation matrix to set. If `none` is passed, the transformation matrix is set to the identity matrix ( `matrix.ident()`).

## Viewport Transformation Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/transformations/set-viewport/#__docusaurus_skipToContent_fallback)

```
set-viewport(
1: ,from: coordinate,to: coordinate,bounds: vector,)
```

Span viewport between two coordinates and set-up scaling and translation

```codeBlockLines_e6Vv
rect((0,0), (2,2))
set-viewport((0,0), (2,2), bounds: (10, 10))
circle((5,5))

```

![](<Base64-Image-Removed>)

#### from:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/transformations/set-viewport/#from "Direct link to from")

Bottom left corner coordinate

#### to:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/draw-functions/transformations/set-viewport/#to "Direct link to to")

Top right corner coordinate

#### bounds:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

Default: `(1` [​](https://cetz-package.github.io/docs/api/draw-functions/transformations/set-viewport/#bounds "Direct link to bounds")

Viewport bounds vector that describes the inner width,

height and depth of the viewport

## Matrix Translation Function
[Skip to main content](https://cetz-package.github.io/docs/api/draw-functions/transformations/translate/#__docusaurus_skipToContent_fallback)

```
translate(
..args: vectorfloatlength,pre: bool,)
```

Translates the transformation matrix by the given vector or dictionary.

```codeBlockLines_e6Vv
// Outer rect
rect((0, 0), (2, 2))
// Inner rect
translate(x: .5, y: .5)
rect((0, 0), (1, 1))

```

![](<Base64-Image-Removed>)

#### ..args:

[vector](https://cetz-package.github.io/docs/api/internal/vector) or [float](https://typst.app/docs/reference/foundations/float) or [length](https://typst.app/docs/reference/layout/length)

[​](https://cetz-package.github.io/docs/api/draw-functions/transformations/translate/#args "Direct link to ..args")

A single vector or any combination of the named arguments `x`, `y` and `z` to translate by.

A translation matrix with the given offsets gets multiplied with the current transformation depending on the value of `pre`.

#### pre:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/draw-functions/transformations/translate/#pre "Direct link to pre")

Specify matrix multiplication order

- false: `World = World * Translate`
- true: `World = Translate * World`

## Cetz API Documentation
[Skip to main content](https://cetz-package.github.io/docs/api/internal/#__docusaurus_skipToContent_fallback)

## Axis Aligned Bounding Box
[Skip to main content](https://cetz-package.github.io/docs/api/internal/aabb/#__docusaurus_skipToContent_fallback)

On this page

An Axis Aligned Bounding Box, or AABB for short.

They take the form of a [dictionary](https://typst.app/docs/reference/foundations/dictionary) with the following keys:

- low [vector](https://cetz-package.github.io/docs/api/internal/vector): Min. bounds vector
- high [vector](https://cetz-package.github.io/docs/api/internal/vector): Max. bounds vector

The following functions are in the `aabb` module.

## aabb [​](https://cetz-package.github.io/docs/api/internal/aabb/\#aabb "Direct link to aabb")

```
aabb(
pts: array,init: aabb,) -> aabb
```

Compute an axis aligned bounding box (aabb) for a list of vectors.

#### pts:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/aabb/#pts "Direct link to pts")

List of [vector](https://cetz-package.github.io/docs/api/internal/vector)s.

#### init:

aabb

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/aabb/#init "Direct link to init")

Initial aabb

## mid [​](https://cetz-package.github.io/docs/api/internal/aabb/\#mid "Direct link to mid")

```
mid(
bounds: aabb,) -> vector
```

Get the mid-point of an AABB as vector.

#### bounds:

aabb

[​](https://cetz-package.github.io/docs/api/internal/aabb/#bounds "Direct link to bounds")

The AABB to get the mid-point of.

## size [​](https://cetz-package.github.io/docs/api/internal/aabb/\#size "Direct link to size")

```
size(
bounds: aabb,) -> vector
```

Get the size of an aabb as vector. This is a vector from the aabb's low to high.

#### bounds:

aabb

[​](https://cetz-package.github.io/docs/api/internal/aabb/#bounds "Direct link to bounds")

The aabb to get the size of.

## padded [​](https://cetz-package.github.io/docs/api/internal/aabb/\#padded "Direct link to padded")

```
padded(
bounds: aabb,padding: nonedictionary,) -> aabb
```

Pad AABB with padding from dictionary with keys top, left, right and bottom.

#### bounds:

aabb

[​](https://cetz-package.github.io/docs/api/internal/aabb/#bounds "Direct link to bounds")

The AABB to pad.

#### padding:

[none](https://typst.app/docs/reference/foundations/none/) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

[​](https://cetz-package.github.io/docs/api/internal/aabb/#padding "Direct link to padding")

Padding values

- [aabb](https://cetz-package.github.io/docs/api/internal/aabb/#aabb)
- [mid](https://cetz-package.github.io/docs/api/internal/aabb/#mid)
- [size](https://cetz-package.github.io/docs/api/internal/aabb/#size)
- [padded](https://cetz-package.github.io/docs/api/internal/aabb/#padded)

## Anchor Creation Functions
[Skip to main content](https://cetz-package.github.io/docs/api/internal/anchor/#__docusaurus_skipToContent_fallback)

On this page

Functions to aid in anchor creation when defining custom elements.

## border [​](https://cetz-package.github.io/docs/api/internal/anchor/\#border "Direct link to border")

```
border(
center: vector,x-dist: number,y-dist: number,drawables: drawables,angle: angle,) -> vector or none
```

Calculates a border anchor at the given angle by testing for an intersection between a line and the given drawables. Returns `none` if no intersection is found for better error reporting.

#### center:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/anchor/#center "Direct link to center")

The position from which to start the test line.

#### x-dist:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

[​](https://cetz-package.github.io/docs/api/internal/anchor/#xdist "Direct link to x-dist")

The furthest distance the test line should go in the x direction.

#### y-dist:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

[​](https://cetz-package.github.io/docs/api/internal/anchor/#ydist "Direct link to y-dist")

The furthest distance the test line should go in the y direction.

#### drawables:

drawables

[​](https://cetz-package.github.io/docs/api/internal/anchor/#drawables "Direct link to drawables")

Drawables to test for an intersection against. Ideally should be of type path but all others are ignored.

#### angle:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/anchor/#angle "Direct link to angle")

The angle to check for a border anchor at.

## setup [​](https://cetz-package.github.io/docs/api/internal/anchor/\#setup "Direct link to setup")

```
setup(
callback: functionauto,anchor-names: array,default: strnone,transform: matrixnone,name: strnone,offset-anchor: strnone,border-anchors: bool,path-anchors: bool,radii: nonearray,path: nonedrawable,nested-anchors: ,) -> array
```

Setup an anchor calculation and handling function for an element. Unifies anchor error checking and calculation of the offset transform.

A tuple of a transformation matrix and function will be returned.
The transform is calculated by translating the given transform by the distance between the position of `offset-anchor` and `default`. It can then be used to correctly transform an element's drawables. If either are none the calculation won't happen but the transform will still be returned.
The function can be used to get the transformed anchors of an element by passing it a string. An empty array can be passed to get the list of valid anchors.

#### callback:

[function](https://typst.app/docs/reference/foundations/function) or [auto](https://typst.app/docs/reference/foundations/auto/)

[​](https://cetz-package.github.io/docs/api/internal/anchor/#callback "Direct link to callback")

The function to call to get a named anchor's position. The anchor's name will be passed and it should return a [vector](https://cetz-package.github.io/docs/api/internal/vector) ( `str => vector`). If no named anchors exist on the element `auto` can be given instead of a function.

#### anchor-names:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/anchor/#anchornames "Direct link to anchor-names")

A list of valid anchor names. This list will be used to validate an anchor exists before `callback` is used.

#### default:

[str](https://typst.app/docs/reference/foundations/str) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/anchor/#default "Direct link to default")

The name of the default anchor, if one exists.

#### transform:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/anchor/#transform "Direct link to transform")

The current transformation matrix to apply to an anchor's position before returning it. If `offset-anchor` and `default` is set, it will be first translated by the distance between them.

#### name:

[str](https://typst.app/docs/reference/foundations/str) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/anchor/#name "Direct link to name")

The name of the element, this is only used in the error message in the event an anchor is invalid.

#### offset-anchor:

[str](https://typst.app/docs/reference/foundations/str) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/anchor/#offsetanchor "Direct link to offset-anchor")

The name of an anchor to offset the transform by.

#### border-anchors:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/anchor/#borderanchors "Direct link to border-anchors")

If true, add border anchors.

#### path-anchors:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/anchor/#pathanchors "Direct link to path-anchors")

If true, add path anchors.

#### radii:

[none](https://typst.app/docs/reference/foundations/none/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/anchor/#radii "Direct link to radii")

Radius tuple used for border anchor calculation.

#### path:

[none](https://typst.app/docs/reference/foundations/none/) or drawable

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/anchor/#path "Direct link to path")

Path used for path and border anchor calculation.

- [border](https://cetz-package.github.io/docs/api/internal/anchor/#border)
- [setup](https://cetz-package.github.io/docs/api/internal/anchor/#setup)

## Bezier Curve Functions
[Skip to main content](https://cetz-package.github.io/docs/api/internal/bezier/#__docusaurus_skipToContent_fallback)

On this page

An [array](https://typst.app/docs/reference/foundations/array) of three or four [vector](https://cetz-package.github.io/docs/api/internal/vector)s, the start point, the endpoint, the first control point and optionally a second control point if the bezier is cubic.

The following functions are in the `bezier` module.

## quadratic-point [​](https://cetz-package.github.io/docs/api/internal/bezier/\#quadratic-point "Direct link to quadratic-point")

```
quadratic-point(
a: vector,b: vector,c: vector,t: float,) -> vector
```

Get the point on quadratic bezier at position `t`.

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#a "Direct link to a")

Start point

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#b "Direct link to b")

End point

#### c:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c "Direct link to c")

Control point

#### t:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#t "Direct link to t")

Position on curve \[0,1\]\[0, 1\]\[0,1\]

## quadratic-derivative [​](https://cetz-package.github.io/docs/api/internal/bezier/\#quadratic-derivative "Direct link to quadratic-derivative")

```
quadratic-derivative(
a: vector,b: vector,c: vector,t: float,) -> vector
```

Get the derivative (dx/dt) of a quadratic bezier at position `t`.

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#a "Direct link to a")

Start point

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#b "Direct link to b")

End point

#### c:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c "Direct link to c")

Control point

#### t:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#t "Direct link to t")

Position on curve \[0, 1\]

## cubic-point [​](https://cetz-package.github.io/docs/api/internal/bezier/\#cubic-point "Direct link to cubic-point")

```
cubic-point(
a: vector,b: vector,c1: vector,c2: vector,t: float,) -> vector
```

Get the point on a cubic bezier curve at position `t`.

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#a "Direct link to a")

Start point

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#b "Direct link to b")

End point

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Control point 2

#### t:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#t "Direct link to t")

Position on curve \[0, 1\]

## cubic-derivative [​](https://cetz-package.github.io/docs/api/internal/bezier/\#cubic-derivative "Direct link to cubic-derivative")

```
cubic-derivative(
a: vector,b: vector,c1: vector,c2: vector,t: float,) -> vector
```

Get the derivative (dx/dt) of a cubic bezier at position `t`.

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#a "Direct link to a")

Start point

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#b "Direct link to b")

End point

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Control point 2

#### t:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#t "Direct link to t")

Position on curve \[0, 1\]

## to-abc [​](https://cetz-package.github.io/docs/api/internal/bezier/\#to-abc "Direct link to to-abc")

```
to-abc(
s: vector,e: vector,B: vector,t: float,deg: int,) -> array
```

Get a bezier curve's ABC coordinates. Returns them as a respective [array](https://typst.app/docs/reference/foundations/array) of [vector](https://cetz-package.github.io/docs/api/internal/vector)s.

```codeBlockLines_e6Vv
       /A\  <-- Control point of quadratic bezier
      / | \
     /  |  \
    /_.-B-._\  <-- Point on curve
   ,'   |   ',
  /     |     \
 s------C------e  <-- Point on line between s and e

```

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### B:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#b "Direct link to B")

Point on curve

#### t:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#t "Direct link to t")

Position on curve \[0,1\]\[0, 1\]\[0,1\]

#### deg:

[int](https://typst.app/docs/reference/foundations/int)

Default: `2` [​](https://cetz-package.github.io/docs/api/internal/bezier/#deg "Direct link to deg")

Bezier degree (2 or 3)

## quadratic-through-3points [​](https://cetz-package.github.io/docs/api/internal/bezier/\#quadratic-through-3points "Direct link to quadratic-through-3points")

```
quadratic-through-3points(
s: vector,B: vector,e: vector,) -> bezier
```

Compute the control points for a quadratic bezier through 3 points.

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### B:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#b "Direct link to B")

A point which the curve passes through

## quadratic-to-cubic [​](https://cetz-package.github.io/docs/api/internal/bezier/\#quadratic-to-cubic "Direct link to quadratic-to-cubic")

```
quadratic-to-cubic(
s: vector,e: vector,c: vector,) -> bezier
```

Convert a quadratic bezier to a cubic bezier.

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### c:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c "Direct link to c")

Control point

## cubic-through-3points [​](https://cetz-package.github.io/docs/api/internal/bezier/\#cubic-through-3points "Direct link to cubic-through-3points")

```
cubic-through-3points(
s: vector,B: vector,e: vector,) -> bezier
```

Compute the control points for a cubic bezier through 3 points.

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### B:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#b "Direct link to B")

A point which the curve passes through

## split [​](https://cetz-package.github.io/docs/api/internal/bezier/\#split "Direct link to split")

```
split(
s: vector,e: vector,c1: vector,c2: vector,t: float,) -> array
```

Split a cubic bezier into two cubic beziers at the point `t`. Returns an [array](https://typst.app/docs/reference/foundations/array) of two bezier. The first holds the original curve start `s`, and the second holds the original curve end `e`.

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Control point 2

#### t:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#t "Direct link to t")

The point on the bezier to split, \[0,1\]\[0, 1\]\[0,1\]

## cubic-arclen [​](https://cetz-package.github.io/docs/api/internal/bezier/\#cubic-arclen "Direct link to cubic-arclen")

```
cubic-arclen(
s: vector,e: vector,c1: vector,c2: vector,samples: ,) -> float
```

Get the approximate cubic curve length

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Control point 2

## cubic-shorten-linear [​](https://cetz-package.github.io/docs/api/internal/bezier/\#cubic-shorten-linear "Direct link to cubic-shorten-linear")

```
cubic-shorten-linear(
s: vector,e: vector,c1: vector,c2: vector,d: float,) -> bezier
```

Shorten the curve by offsetting s and c1 or e and c2 by distance d. If d is positive the curve gets shortened by moving s and c1 closer to e, if d is negative, e and c2 get moved closer to s.

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Control point 2

#### d:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#d "Direct link to d")

Distance to shorten by

## cubic-t-for-distance [​](https://cetz-package.github.io/docs/api/internal/bezier/\#cubic-t-for-distance "Direct link to cubic-t-for-distance")

```
cubic-t-for-distance(
s: vector,e: vector,c1: vector,c2: vector,d: float,samples: ,) -> float
```

Approximate bezier interval `t` for a given distance `d`. If `d` is positive, the functions starts from the curve's start `s`, if `d` is negative, it starts form the curve's end `e`.

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Control point 2

#### d:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#d "Direct link to d")

The distance along the bezier to find `t`.

## cubic-shorten [​](https://cetz-package.github.io/docs/api/internal/bezier/\#cubic-shorten "Direct link to cubic-shorten")

```
cubic-shorten(
s: vector,e: vector,c1: vector,c2: vector,d: float,samples: int,) -> bezier
```

Shorten curve by distance `d`. This keeps the curvature of the curve by finding new values along the original curve. If `d` is positive the curve gets shortened by moving `s` closer to `e`, if `d` is negative, `e` is moved closer to `s`. The points `s` and `e` are moved along the curve, keeping the curve's curvature the same (the control points get recalculated).

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Control point 2

#### d:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#d "Direct link to d")

Distance to shorten by

#### samples:

[int](https://typst.app/docs/reference/foundations/int)

Default: `15` [​](https://cetz-package.github.io/docs/api/internal/bezier/#samples "Direct link to samples")

Maximum of samples/steps to use

## cubic-extrema [​](https://cetz-package.github.io/docs/api/internal/bezier/\#cubic-extrema "Direct link to cubic-extrema")

```
cubic-extrema(
s: vector,e: vector,c1: vector,c2: vector,) -> array
```

Find cubic curve extrema by calculating the roots of the curve's first derivative. Returns an [array](https://typst.app/docs/reference/foundations/array) of [vector](https://cetz-package.github.io/docs/api/internal/vector) ordered by distance along the curve from the start to its end.

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Control point 2

## cubic-aabb [​](https://cetz-package.github.io/docs/api/internal/bezier/\#cubic-aabb "Direct link to cubic-aabb")

```
cubic-aabb(
s: vector,e: vector,c1: vector,c2: vector,) -> array
```

Returns axis aligned bounding box coordinates `(bottom-left, top-right)` for a cubic bezier curve.

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Curve start

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Curve end

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Control point 2

## catmull-to-cubic [​](https://cetz-package.github.io/docs/api/internal/bezier/\#catmull-to-cubic "Direct link to catmull-to-cubic")

```
catmull-to-cubic(
points: array,k: float,close: bool,) -> array
```

Returns an array of cubic bezier for a catmull curve through an array of points.

#### points:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#points "Direct link to points")

Array of 2d points

#### k:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#k "Direct link to k")

Strength between 0 and 1

## line-cubic-intersections [​](https://cetz-package.github.io/docs/api/internal/bezier/\#line-cubic-intersections "Direct link to line-cubic-intersections")

```
line-cubic-intersections(
la: vector,lb: vector,s: vector,e: vector,c1: vector,c2: vector,ray: bool,) -> array
```

Calculate the intersection points between a 2D cubic-bezier and a straight line. Returns an array of [vector](https://cetz-package.github.io/docs/api/internal/vector)

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#s "Direct link to s")

Bezier start point

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#e "Direct link to e")

Bezier end point

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c1 "Direct link to c1")

Bezier control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#c2 "Direct link to c2")

Bezier control point 2

#### la:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#la "Direct link to la")

Line start point

#### lb:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/bezier/#lb "Direct link to lb")

Line end point

#### ray:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/bezier/#ray "Direct link to ray")

If set to true, ignore line length

- [quadratic-point](https://cetz-package.github.io/docs/api/internal/bezier/#quadratic-point)
- [quadratic-derivative](https://cetz-package.github.io/docs/api/internal/bezier/#quadratic-derivative)
- [cubic-point](https://cetz-package.github.io/docs/api/internal/bezier/#cubic-point)
- [cubic-derivative](https://cetz-package.github.io/docs/api/internal/bezier/#cubic-derivative)
- [to-abc](https://cetz-package.github.io/docs/api/internal/bezier/#to-abc)
- [quadratic-through-3points](https://cetz-package.github.io/docs/api/internal/bezier/#quadratic-through-3points)
- [quadratic-to-cubic](https://cetz-package.github.io/docs/api/internal/bezier/#quadratic-to-cubic)
- [cubic-through-3points](https://cetz-package.github.io/docs/api/internal/bezier/#cubic-through-3points)
- [split](https://cetz-package.github.io/docs/api/internal/bezier/#split)
- [cubic-arclen](https://cetz-package.github.io/docs/api/internal/bezier/#cubic-arclen)
- [cubic-shorten-linear](https://cetz-package.github.io/docs/api/internal/bezier/#cubic-shorten-linear)
- [cubic-t-for-distance](https://cetz-package.github.io/docs/api/internal/bezier/#cubic-t-for-distance)
- [cubic-shorten](https://cetz-package.github.io/docs/api/internal/bezier/#cubic-shorten)
- [cubic-extrema](https://cetz-package.github.io/docs/api/internal/bezier/#cubic-extrema)
- [cubic-aabb](https://cetz-package.github.io/docs/api/internal/bezier/#cubic-aabb)
- [catmull-to-cubic](https://cetz-package.github.io/docs/api/internal/bezier/#catmull-to-cubic)
- [line-cubic-intersections](https://cetz-package.github.io/docs/api/internal/bezier/#line-cubic-intersections)

## Canvas Drawing Setup
[Skip to main content](https://cetz-package.github.io/docs/api/internal/canvas/#__docusaurus_skipToContent_fallback)

```
canvas(
length: lengthratio,debug: bool,background: nonecolor,padding: nonenumberarraydictionary,body: nonearrayelement,) -> content
```

Sets up a canvas for drawing on.

#### length:

[length](https://typst.app/docs/reference/layout/length) or [ratio](https://typst.app/docs/reference/layout/ratio)

Default: `1cm` [​](https://cetz-package.github.io/docs/api/internal/canvas/#length "Direct link to length")

Used to specify what 1 coordinate unit is. If given a ratio, that ratio is relative to the containing elements width!

#### body:

[none](https://typst.app/docs/reference/foundations/none/) or [array](https://typst.app/docs/reference/foundations/array) or [element](https://cetz-package.github.io/docs/advanced/custom-types#element)

[​](https://cetz-package.github.io/docs/api/internal/canvas/#body "Direct link to body")

A code block in which functions from the `draw` module have been called.

#### background:

[none](https://typst.app/docs/reference/foundations/none/) or [color](https://typst.app/docs/reference/visualize/color/)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/canvas/#background "Direct link to background")

A color to be used for the background of the canvas.

#### padding:

[none](https://typst.app/docs/reference/foundations/none/) or [number](https://cetz-package.github.io/docs/basics/custom-types#number) or [array](https://typst.app/docs/reference/foundations/array) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/canvas/#padding "Direct link to padding")

How much padding to add to the canvas. `none` applies no padding. A number applies padding to all sides equally. A dictionary applies padding following Typst's `pad` function: [https://typst.app/docs/reference/layout/pad/](https://typst.app/docs/reference/layout/pad/). An array follows CSS like padding: `(y, x)`, `(top, x, bottom)` or `(top, right, bottom, left)`.

#### debug:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/canvas/#debug "Direct link to debug")

Shows the bounding boxes of each element when `true`.

## Complex Number Operations
[Skip to main content](https://cetz-package.github.io/docs/api/internal/complex/#__docusaurus_skipToContent_fallback)

On this page

A complex number that takes the form of an [array](https://typst.app/docs/reference/foundations/array) of two [float](https://typst.app/docs/reference/foundations/float)s. The first element is the real number and the second represents the imaginary.

## re [​](https://cetz-package.github.io/docs/api/internal/complex/\#re "Direct link to re")

```
re(
V: complex,) -> float
```

Returns the real part of a complex number.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

A complex number.

## im [​](https://cetz-package.github.io/docs/api/internal/complex/\#im "Direct link to im")

```
im(
V: complex,) -> float
```

Returns the imaginary part of a complex number.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

A complex number.

## mul [​](https://cetz-package.github.io/docs/api/internal/complex/\#mul "Direct link to mul")

```
mul(
V: complex,W: complex,)
```

Multiplies two complex numbers together and returns the result VWV WVW.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number on the left hand side.

#### W:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#w "Direct link to W")

The complex number on the right hand side.

## conj [​](https://cetz-package.github.io/docs/api/internal/complex/\#conj "Direct link to conj")

```
conj(
V: complex,) -> complex
```

Calculates the conjugate of a complex number.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

A complex number.

## dot [​](https://cetz-package.github.io/docs/api/internal/complex/\#dot "Direct link to dot")

```
dot(
V: complex,W: complex,) -> float
```

Calculates the dot product of two complex numbers in R^2 V⋅WV \\cdot WV⋅W.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number on the left hand side.

#### W:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#w "Direct link to W")

The complex number on the right hand side.

## normsq [​](https://cetz-package.github.io/docs/api/internal/complex/\#normsq "Direct link to normsq")

```
normsq(
V: complex,) -> float
```

Calculates the squared normal of a complex number.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number.

## norm [​](https://cetz-package.github.io/docs/api/internal/complex/\#norm "Direct link to norm")

```
norm(
V: complex,) -> float
```

Calculates the normal of a complex number

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number.

## scale [​](https://cetz-package.github.io/docs/api/internal/complex/\#scale "Direct link to scale")

```
scale(
V: complex,t: float,) -> complex
```

Multiplies a complex number by a scale factor.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number to scale.

#### t:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/complex/#t "Direct link to t")

The scale factor.

## unit [​](https://cetz-package.github.io/docs/api/internal/complex/\#unit "Direct link to unit")

```
unit(
V: complex,) -> vector
```

Returns a unit vector in the direction of a complex number.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number.

## inv [​](https://cetz-package.github.io/docs/api/internal/complex/\#inv "Direct link to inv")

```
inv(
V: complex,) -> complex
```

Inverts a complex number.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number

## div [​](https://cetz-package.github.io/docs/api/internal/complex/\#div "Direct link to div")

```
div(
V: complex,W: complex,) -> complex
```

Divides two complex numbers.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number of the numerator.

#### W:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#w "Direct link to W")

The complex number of the denominator.

## add [​](https://cetz-package.github.io/docs/api/internal/complex/\#add "Direct link to add")

```
add(
V: complex,W: complex,) -> complex
```

Adds two complex numbers together.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number on the left hand side.

#### W:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#w "Direct link to W")

The complex number on the right hand side.

## sub [​](https://cetz-package.github.io/docs/api/internal/complex/\#sub "Direct link to sub")

```
sub(
V: complex,W: complex,) -> complex
```

Subtracts two complex numbers together.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number on the left hand side.

#### W:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#w "Direct link to W")

The complex number on the right hand side.

## arg [​](https://cetz-package.github.io/docs/api/internal/complex/\#arg "Direct link to arg")

```
arg(
V: complex,)
```

Calculates the argument of a complex number.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

The complex number.

## ang [​](https://cetz-package.github.io/docs/api/internal/complex/\#ang "Direct link to ang")

```
ang(
V: complex,W: complex,)
```

Get the signed angle of two complex numbers from V to W.

#### V:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#v "Direct link to V")

A complex number.

#### W:

complex

[​](https://cetz-package.github.io/docs/api/internal/complex/#w "Direct link to W")

A complex number.

- [re](https://cetz-package.github.io/docs/api/internal/complex/#re)
- [im](https://cetz-package.github.io/docs/api/internal/complex/#im)
- [mul](https://cetz-package.github.io/docs/api/internal/complex/#mul)
- [conj](https://cetz-package.github.io/docs/api/internal/complex/#conj)
- [dot](https://cetz-package.github.io/docs/api/internal/complex/#dot)
- [normsq](https://cetz-package.github.io/docs/api/internal/complex/#normsq)
- [norm](https://cetz-package.github.io/docs/api/internal/complex/#norm)
- [scale](https://cetz-package.github.io/docs/api/internal/complex/#scale)
- [unit](https://cetz-package.github.io/docs/api/internal/complex/#unit)
- [inv](https://cetz-package.github.io/docs/api/internal/complex/#inv)
- [div](https://cetz-package.github.io/docs/api/internal/complex/#div)
- [add](https://cetz-package.github.io/docs/api/internal/complex/#add)
- [sub](https://cetz-package.github.io/docs/api/internal/complex/#sub)
- [arg](https://cetz-package.github.io/docs/api/internal/complex/#arg)
- [ang](https://cetz-package.github.io/docs/api/internal/complex/#ang)

## Coordinate Resolution Functions
[Skip to main content](https://cetz-package.github.io/docs/api/internal/coordinate/#__docusaurus_skipToContent_fallback)

On this page

Functions to aid in resolving coordinates.

## resolve-system [​](https://cetz-package.github.io/docs/api/internal/coordinate/\#resolve-system "Direct link to resolve-system")

```
resolve-system(
c: coordinate,) -> str
```

Figures out what system a coordinate belongs to and returns the corresponding string.

#### c:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/internal/coordinate/#c "Direct link to c")

The coordinate to find the system of.

## resolve [​](https://cetz-package.github.io/docs/api/internal/coordinate/\#resolve "Direct link to resolve")

```
resolve(
ctx: context,..coordinates: coordinate,update: bool,) -> array
```

Resolve a list of coordinates to absolute vectors. Returns an array of the new [context](https://cetz-package.github.io/docs/advanced/custom-types#context) then the resolved coordinate vectors.

```codeBlockLines_e6Vv
line((0,0), (1,1), name: "l")
get-ctx(ctx => {
  // Get the vector of coordinate "l.start" and "l.end"
  let (ctx, a, b) = cetz.coordinate.resolve(ctx, "l.start", "l.end")
  content("l.start", [#a], frame: "rect", stroke: none, fill: white)
  content("l.end",   [#b], frame: "rect", stroke: none, fill: white)
})

```

![](https://cetz-package.github.io/docs/assets/images/4564e4-30aedc30ea09b66ee86cbbdd03950ff0.svg)

#### ctx:

[context](https://cetz-package.github.io/docs/advanced/custom-types#context)

[​](https://cetz-package.github.io/docs/api/internal/coordinate/#ctx "Direct link to ctx")

Canvas context object

#### ..coordinates:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/internal/coordinate/#coordinates "Direct link to ..coordinates")

List of coordinates

#### update:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `true` [​](https://cetz-package.github.io/docs/api/internal/coordinate/#update "Direct link to update")

Update the context's last position

- [resolve-system](https://cetz-package.github.io/docs/api/internal/coordinate/#resolve-system)
- [resolve](https://cetz-package.github.io/docs/api/internal/coordinate/#resolve)

## Drawable API Overview
[Skip to main content](https://cetz-package.github.io/docs/api/internal/drawable/#__docusaurus_skipToContent_fallback)

On this page

A [dictionary](https://typst.app/docs/reference/foundations/dictionary) that contains path or content data that will actually get drawn by the canvas. Can also be an [array](https://typst.app/docs/reference/foundations/array) of this type.

## apply-transform [​](https://cetz-package.github.io/docs/api/internal/drawable/\#apply-transform "Direct link to apply-transform")

```
apply-transform(
transform: matrix,drawables: drawable,) -> drawable
```

Applies a transform to drawables. If a single drawable is given it will be returned in a single element [array](https://typst.app/docs/reference/foundations/array).

#### transform:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#transform "Direct link to transform")

The transformation matrix.

#### drawables:

drawable

[​](https://cetz-package.github.io/docs/api/internal/drawable/#drawables "Direct link to drawables")

The drawables to transform.

## path [​](https://cetz-package.github.io/docs/api/internal/drawable/\#path "Direct link to path")

```
path(
close: bool,fill: colornone,stroke: stroke,fill-rule: string,segments: array,) -> drawable
```

Creates a path drawable from path segements.

#### segments:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#segments "Direct link to segments")

The segments to create the path from.

#### close:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/drawable/#close "Direct link to close")

If `true` the path will be closed.

#### fill:

[color](https://typst.app/docs/reference/visualize/color/) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/drawable/#fill "Direct link to fill")

The color to fill the path with.

#### fill-rule:

string

Default: `"non-zero"` [​](https://cetz-package.github.io/docs/api/internal/drawable/#fillrule "Direct link to fill-rule")

One of "even-odd" or "non-zero".

#### stroke:

[stroke](https://typst.app/docs/reference/visualize/stroke)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/drawable/#stroke "Direct link to stroke")

The stroke of the path.

## content [​](https://cetz-package.github.io/docs/api/internal/drawable/\#content "Direct link to content")

```
content(
pos: vector,width: float,height: float,border: segment,body: content,) -> drawable
```

Creates a content drawable.

#### pos:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#pos "Direct link to pos")

The position of the drawable.

#### width:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#width "Direct link to width")

The width of the drawable.

#### height:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#height "Direct link to height")

The height of the drawable.

#### border:

segment

[​](https://cetz-package.github.io/docs/api/internal/drawable/#border "Direct link to border")

A segment to define the border of the drawable with.

#### body:

[content](https://typst.app/docs/reference/foundations/content)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#body "Direct link to body")

The content of the drawable.

## ellipse [​](https://cetz-package.github.io/docs/api/internal/drawable/\#ellipse "Direct link to ellipse")

```
ellipse(
x: float,y: float,z: float,rx: float,ry: float,fill: colornone,stroke: stroke,) -> drawable
```

Creates a path drawable in the shape of an ellipse.

#### x:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#x "Direct link to x")

The xxx position of the ellipse.

#### y:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#y "Direct link to y")

The yyy position of the ellipse.

#### z:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#z "Direct link to z")

The zzz position of the ellipse.

#### rx:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#rx "Direct link to rx")

The radius of the ellipse in the xxx axis.

#### ry:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#ry "Direct link to ry")

The radius of the ellipse in the yyy axis.

#### fill:

[color](https://typst.app/docs/reference/visualize/color/) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/drawable/#fill "Direct link to fill")

The color to fill the ellipse with.

#### stroke:

[stroke](https://typst.app/docs/reference/visualize/stroke)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/drawable/#stroke "Direct link to stroke")

The stroke of the ellipse's path.

## arc [​](https://cetz-package.github.io/docs/api/internal/drawable/\#arc "Direct link to arc")

```
arc(
x: float,y: float,z: float,start: angle,stop: angle,rx: float,ry: float,mode: str,fill: colornone,stroke: stroke,) -> drawable
```

Creates a path drawable in the shape of an arc.

#### x:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#x "Direct link to x")

The xxx position of the start of the arc.

#### y:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#y "Direct link to y")

The yyy position of the start of the arc.

#### z:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#z "Direct link to z")

The zzz position of the start of the arc.

#### start:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#start "Direct link to start")

The angle along an ellipse to start drawing the arc from.

#### stop:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#stop "Direct link to stop")

The angle along an ellipse to stop drawing the arc at.

#### rx:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#rx "Direct link to rx")

The radius of the arc in the xxx axis.

#### ry:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/drawable/#ry "Direct link to ry")

The radius of the arc in the yyy axis.

#### mode:

[str](https://typst.app/docs/reference/foundations/str)

Default: `"OPEN"` [​](https://cetz-package.github.io/docs/api/internal/drawable/#mode "Direct link to mode")

How to draw the arc: `"OPEN"` leaves the path open, `"CLOSED"` closes the arc by drawing a straight line between the end of the arc and its start, `"PIE"` also closes the arc by drawing a line from its end to its origin then to its start.

#### fill:

[color](https://typst.app/docs/reference/visualize/color/) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/drawable/#fill "Direct link to fill")

The color to fill the arc with.

#### stroke:

[stroke](https://typst.app/docs/reference/visualize/stroke)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/drawable/#stroke "Direct link to stroke")

The stroke of the arc's path.

- [apply-transform](https://cetz-package.github.io/docs/api/internal/drawable/#apply-transform)
- [path](https://cetz-package.github.io/docs/api/internal/drawable/#path)
- [content](https://cetz-package.github.io/docs/api/internal/drawable/#content)
- [ellipse](https://cetz-package.github.io/docs/api/internal/drawable/#ellipse)
- [arc](https://cetz-package.github.io/docs/api/internal/drawable/#arc)

## Hobby Curve Calculations
[Skip to main content](https://cetz-package.github.io/docs/api/internal/hobby/#__docusaurus_skipToContent_fallback)

On this page

## hobby-to-cubic-open [​](https://cetz-package.github.io/docs/api/internal/hobby/\#hobby-to-cubic-open "Direct link to hobby-to-cubic-open")

```
hobby-to-cubic-open(
points: array,ta: autoarray,tb: autoarray,rho: autofunction,omega: autoarray,) -> array
```

Calculates a bezier spline for an open Hobby curve through a list of points. Returns an [array](https://typst.app/docs/reference/foundations/array) of beziers

#### points:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/hobby/#points "Direct link to points")

List of points

#### ta:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#ta "Direct link to ta")

Outgoing tension per point

#### tb:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#tb "Direct link to tb")

Incoming tension per point

#### rho:

[auto](https://typst.app/docs/reference/foundations/auto/) or [function](https://typst.app/docs/reference/foundations/function)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#rho "Direct link to rho")

The rho function of the form `(float, float) => float`

#### omega:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#omega "Direct link to omega")

Tuple of the curl at the start end end of the curve `(start, end)` as floats

## hobby-to-cubic-closed [​](https://cetz-package.github.io/docs/api/internal/hobby/\#hobby-to-cubic-closed "Direct link to hobby-to-cubic-closed")

```
hobby-to-cubic-closed(
points: array,ta: autoarray,tb: autoarray,rho: autoarray,) -> array
```

Calculates a bezier spline for a closed Hobby curve through a list of points. Returns an [array](https://typst.app/docs/reference/foundations/array) of beziers.

#### points:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/hobby/#points "Direct link to points")

List of points

#### ta:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#ta "Direct link to ta")

Outgoing tension per point

#### tb:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#tb "Direct link to tb")

Incoming tension per point

#### rho:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#rho "Direct link to rho")

The rho function of the form `(float, b) => float`

## hobby-to-cubic [​](https://cetz-package.github.io/docs/api/internal/hobby/\#hobby-to-cubic "Direct link to hobby-to-cubic")

```
hobby-to-cubic(
points: array,ta: autoarray,tb: autoarray,rho: autoarray,omega: autoarray,close: bool,) -> array
```

Calculates a bezier spline for a Hobby curve through a list of points. Returns an [array](https://typst.app/docs/reference/foundations/array) of beziers.

#### points:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/hobby/#points "Direct link to points")

List of points

#### ta:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#ta "Direct link to ta")

Outgoing tension per point

#### tb:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#tb "Direct link to tb")

Incoming tension per point

#### rho:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#rho "Direct link to rho")

The rho function of the form `(float, float) => float`

#### omega:

[auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `auto` [​](https://cetz-package.github.io/docs/api/internal/hobby/#omega "Direct link to omega")

Tuple of the curl at the start end end of the curve `(start, end)` as floats

#### close:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/hobby/#close "Direct link to close")

Close the curve

- [hobby-to-cubic-open](https://cetz-package.github.io/docs/api/internal/hobby/#hobby-to-cubic-open)
- [hobby-to-cubic-closed](https://cetz-package.github.io/docs/api/internal/hobby/#hobby-to-cubic-closed)
- [hobby-to-cubic](https://cetz-package.github.io/docs/api/internal/hobby/#hobby-to-cubic)

## Intersection Functions Overview
[Skip to main content](https://cetz-package.github.io/docs/api/internal/intersection/#__docusaurus_skipToContent_fallback)

On this page

## line-line [​](https://cetz-package.github.io/docs/api/internal/intersection/\#line-line "Direct link to line-line")

```
line-line(
a: vector,b: vector,c: vector,d: vector,ray: bool,) -> vector or none
```

Checks for a line-line intersection between the given points and returns its position, otherwise [none](https://typst.app/docs/reference/foundations/none/).

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#a "Direct link to a")

Line 1 point 1

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#b "Direct link to b")

Line 1 point 2

#### c:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#c "Direct link to c")

Line 2 point 1

#### d:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#d "Direct link to d")

Line 2 point 2

#### ray:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/intersection/#ray "Direct link to ray")

When `true`, intersections will be found for the whole line instead of inbetween the given points.

## line-cubic [​](https://cetz-package.github.io/docs/api/internal/intersection/\#line-cubic "Direct link to line-cubic")

```
line-cubic(
la: vector,lb: vector,s: vector,e: vector,c1: vector,c2: vector,) -> array
```

Finds the intersections of a line and cubic bezier.

#### s:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#s "Direct link to s")

Bezier start point

#### e:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#e "Direct link to e")

Bezier end point

#### c1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#c1 "Direct link to c1")

Bezier control point 1

#### c2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#c2 "Direct link to c2")

Bezier control point 2

#### la:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#la "Direct link to la")

Line start point

#### lb:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#lb "Direct link to lb")

Line end point

#### ray:

[bool](https://typst.app/docs/reference/foundations/bool)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#ray "Direct link to ray")

When `true`, intersections will be found for the whole line instead of inbetween the given points.

## line-linestrip [​](https://cetz-package.github.io/docs/api/internal/intersection/\#line-linestrip "Direct link to line-linestrip")

```
line-linestrip(
la: vector,lb: vector,v: array,) -> array
```

Finds the intersections of a line and linestrip.

#### la:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#la "Direct link to la")

Line start point.

#### lb:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#lb "Direct link to lb")

Line end point.

#### v:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#v "Direct link to v")

An [array](https://typst.app/docs/reference/foundations/array) of [vector](https://cetz-package.github.io/docs/api/internal/vector)s that define each point on the linestrip.

## line-path [​](https://cetz-package.github.io/docs/api/internal/intersection/\#line-path "Direct link to line-path")

```
line-path(
la: vector,lb: vector,path: drawable,) -> array
```

Finds the intersections of a line and path in 2D. The path should be given as a drawable of type `path`.

#### la:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#la "Direct link to la")

Line start

#### lb:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/intersection/#lb "Direct link to lb")

Line end

#### path:

drawable

[​](https://cetz-package.github.io/docs/api/internal/intersection/#path "Direct link to path")

The path.

## path-path [​](https://cetz-package.github.io/docs/api/internal/intersection/\#path-path "Direct link to path-path")

```
path-path(
a: path,b: path,samples: int,) -> array
```

Finds the intersections between two path drawables in 2D.

#### a:

path

[​](https://cetz-package.github.io/docs/api/internal/intersection/#a "Direct link to a")

Path a

#### b:

path

[​](https://cetz-package.github.io/docs/api/internal/intersection/#b "Direct link to b")

Path b

#### samples:

[int](https://typst.app/docs/reference/foundations/int)

Default: `8` [​](https://cetz-package.github.io/docs/api/internal/intersection/#samples "Direct link to samples")

Number of samples to use for bezier curves

- [line-line](https://cetz-package.github.io/docs/api/internal/intersection/#line-line)
- [line-cubic](https://cetz-package.github.io/docs/api/internal/intersection/#line-cubic)
- [line-linestrip](https://cetz-package.github.io/docs/api/internal/intersection/#line-linestrip)
- [line-path](https://cetz-package.github.io/docs/api/internal/intersection/#line-path)
- [path-path](https://cetz-package.github.io/docs/api/internal/intersection/#path-path)

## Mark Management API
[Skip to main content](https://cetz-package.github.io/docs/api/internal/mark/#__docusaurus_skipToContent_fallback)

On this page

## check-mark [​](https://cetz-package.github.io/docs/api/internal/mark/\#check-mark "Direct link to check-mark")

```
check-mark(
style: style,) -> bool
```

Checks if a mark should be drawn according to the current style.

#### style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/internal/mark/#style "Direct link to style")

The current style.

## process-style [​](https://cetz-package.github.io/docs/api/internal/mark/\#process-style "Direct link to process-style")

```
process-style(
ctx: context,style: style,root: str,path-length: float,)
```

Processes the mark styling.
TODO: remember what is actually going on here.

#### ctx:

[context](https://cetz-package.github.io/docs/advanced/custom-types#context)

[​](https://cetz-package.github.io/docs/api/internal/mark/#ctx "Direct link to ctx")

The context object.

#### style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/internal/mark/#style "Direct link to style")

The current style.

#### root:

[str](https://typst.app/docs/reference/foundations/str)

[​](https://cetz-package.github.io/docs/api/internal/mark/#root "Direct link to root")

Where the mark is being placed, normally either `"start"` or `"end"`. Allows different styling for marks in different directions.

#### path-length:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/mark/#pathlength "Direct link to path-length")

The length of the path. This is used for relative offsets.

## place-mark-on-path [​](https://cetz-package.github.io/docs/api/internal/mark/\#place-mark-on-path "Direct link to place-mark-on-path")

```
place-mark-on-path(
ctx: context,styles: style,segments: drawable,is-end: bool,) -> dictionary
```

Places a mark on the given path. Returns a [dictionary](https://typst.app/docs/reference/foundations/dictionary) with the following keys:

#### drawables:

drawable

[​](https://cetz-package.github.io/docs/api/internal/mark/#drawables "Direct link to drawables")

The mark drawables.

#### distance:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/mark/#distance "Direct link to distance")

The length to shorten the path by.

#### pos:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/mark/#pos "Direct link to pos")

The position of the mark, can be used to snap the end of the path to after shortening.

* * *

#### ctx:

[context](https://cetz-package.github.io/docs/advanced/custom-types#context)

[​](https://cetz-package.github.io/docs/api/internal/mark/#ctx "Direct link to ctx")

The canvas context object.

#### styles:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/internal/mark/#styles "Direct link to styles")

A processed mark styling.

#### segments:

drawable

[​](https://cetz-package.github.io/docs/api/internal/mark/#segments "Direct link to segments")

The path to place the mark on.

#### is-end:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/mark/#isend "Direct link to is-end")

TODO

## place-marks-along-path [​](https://cetz-package.github.io/docs/api/internal/mark/\#place-marks-along-path "Direct link to place-marks-along-path")

```
place-marks-along-path(
ctx: context,style: style,transform: matrix,path: drawable,add-path: bool,) -> array
```

Places marks along a path. Returns them as an [array](https://typst.app/docs/reference/foundations/array) of drawable.

#### ctx:

[context](https://cetz-package.github.io/docs/advanced/custom-types#context)

[​](https://cetz-package.github.io/docs/api/internal/mark/#ctx "Direct link to ctx")

The context object.

#### style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/internal/mark/#style "Direct link to style")

The current mark styling.

#### transform:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/mark/#transform "Direct link to transform")

The current transformation matrix.

#### path:

drawable

[​](https://cetz-package.github.io/docs/api/internal/mark/#path "Direct link to path")

The path to place the marks on.

#### add-path:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `true` [​](https://cetz-package.github.io/docs/api/internal/mark/#addpath "Direct link to add-path")

When `true` the shortened path will returned as the first drawable in the [array](https://typst.app/docs/reference/foundations/array)

- [check-mark](https://cetz-package.github.io/docs/api/internal/mark/#check-mark)
- [process-style](https://cetz-package.github.io/docs/api/internal/mark/#process-style)
- [place-mark-on-path](https://cetz-package.github.io/docs/api/internal/mark/#place-mark-on-path)
- [place-marks-along-path](https://cetz-package.github.io/docs/api/internal/mark/#place-marks-along-path)

## Matrix Operations Guide
[Skip to main content](https://cetz-package.github.io/docs/api/internal/matrix/#__docusaurus_skipToContent_fallback)

On this page

An [array](https://typst.app/docs/reference/foundations/array) of [array](https://typst.app/docs/reference/foundations/array)s of [float](https://typst.app/docs/reference/foundations/float)s that represent a matrix. Can be any size but transformation matrices are 4x4.

## ident [​](https://cetz-package.github.io/docs/api/internal/matrix/\#ident "Direct link to ident")

```
ident(
size: int,) -> matrix
```

Create a (square) identity matrix with dimensions size×sizesize \\times sizesize×size

#### size:

[int](https://typst.app/docs/reference/foundations/int)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#size "Direct link to size")

Size of the matrix

## diag [​](https://cetz-package.github.io/docs/api/internal/matrix/\#diag "Direct link to diag")

```
diag(
..diag: float,) -> matrix
```

Create a square matrix with the diagonal set to the
given values

#### ..diag:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#diag "Direct link to ..diag")

Diagonal values

## dim [​](https://cetz-package.github.io/docs/api/internal/matrix/\#dim "Direct link to dim")

```
dim(
m: matrix,) -> array
```

Returns the dimension of the given matrix as `(m, n)`

#### m:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#m "Direct link to m")

The matrix

## column [​](https://cetz-package.github.io/docs/api/internal/matrix/\#column "Direct link to column")

```
column(
mat: matrix,n: int,) -> vector
```

Returns the nth column of a matrix as a [vector](https://cetz-package.github.io/docs/api/internal/vector)

#### mat:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#mat "Direct link to mat")

Input matrix

#### n:

[int](https://typst.app/docs/reference/foundations/int)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#n "Direct link to n")

The column's index

## set-column [​](https://cetz-package.github.io/docs/api/internal/matrix/\#set-column "Direct link to set-column")

```
set-column(
mat: matrix,n: int,vec: vector,) -> matrix
```

Replaces the nth column of a matrix with the given vector.

#### mat:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#mat "Direct link to mat")

Input matrix.

#### n:

[int](https://typst.app/docs/reference/foundations/int)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#n "Direct link to n")

The index of the column to replace

#### vec:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#vec "Direct link to vec")

The column data to insert.

## round [​](https://cetz-package.github.io/docs/api/internal/matrix/\#round "Direct link to round")

```
round(
mat: matrix,precision: int,) -> matrix
```

Rounds each value in the matrix to a precision.

#### mat:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#mat "Direct link to mat")

Input matrix

#### precision:

[int](https://typst.app/docs/reference/foundations/int)

Default: `8` [​](https://cetz-package.github.io/docs/api/internal/matrix/#precision "Direct link to precision")

Rounding precision (digits)

## transform-translate [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-translate "Direct link to transform-translate")

```
transform-translate(
x: float,y: float,z: float,) -> matrix
```

Returns a 4×44 \\times 44×4 translation matrix

#### x:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#x "Direct link to x")

The translation in the xxx direction.

#### y:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#y "Direct link to y")

The translation in the yyy direction.

#### z:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#z "Direct link to z")

The translation in the xxx direction.

## transform-shear-x [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-shear-x "Direct link to transform-shear-x")

```
transform-shear-x(
factor: float,) -> matrix
```

Returns a 4×44 \\times 44×4 x-shear matrix

#### factor:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#factor "Direct link to factor")

The shear in the xxx direction.

## transform-shear-z [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-shear-z "Direct link to transform-shear-z")

```
transform-shear-z(
factor: float,) -> matrix
```

Returns a 4×44 \\times 44×4 z-shear matrix

#### factor:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#factor "Direct link to factor")

The shear in the zzz direction.

## transform-scale [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-scale "Direct link to transform-scale")

```
transform-scale(
f: floatarraydictionary,) -> matrix
```

Returns a 4×44 \\times 44×4 scale matrix

#### f:

[float](https://typst.app/docs/reference/foundations/float) or [array](https://typst.app/docs/reference/foundations/array) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#f "Direct link to f")

The scale factor(s) of the matrix. An [array](https://typst.app/docs/reference/foundations/array) of at least 3 [float](https://typst.app/docs/reference/foundations/float)s sets the x, y and z scale factors. A [dictionary](https://typst.app/docs/reference/foundations/dictionary) sets the scale in the direction of the corresponding x, y and z keys. A single [float](https://typst.app/docs/reference/foundations/float) sets the scale for all directions.

## transform-rotate-dir [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-rotate-dir "Direct link to transform-rotate-dir")

```
transform-rotate-dir(
dir: vector,up: vector,) -> matrix
```

Returns a 4×44 \\times 44×4 rotation xyz matrix for a direction and up vector

#### dir:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#dir "Direct link to dir")

idk

#### up:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#up "Direct link to up")

idk

## transform-rotate-x [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-rotate-x "Direct link to transform-rotate-x")

```
transform-rotate-x(
angle: angle,) -> matrix
```

Returns a 4×44 \\times 44×4xxx rotation matrix

#### angle:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#angle "Direct link to angle")

The angle to rotate around the xxx axis

## transform-rotate-y [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-rotate-y "Direct link to transform-rotate-y")

```
transform-rotate-y(
angle: angle,) -> matrix
```

Returns a 4×44 \\times 44×4yyy rotation matrix

#### angle:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#angle "Direct link to angle")

The angle to rotate around the yyy axis

## transform-rotate-z [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-rotate-z "Direct link to transform-rotate-z")

```
transform-rotate-z(
angle: angle,) -> matrix
```

Returns a 4×44 \\times 44×4zzz rotation matrix

#### angle:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#angle "Direct link to angle")

The angle to rotate around the zzz axis

## transform-rotate-xz [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-rotate-xz "Direct link to transform-rotate-xz")

```
transform-rotate-xz(
x: angle,z: angle,) -> matrix
```

Returns a 4×44 \\times 44×4xzx zxz rotation matrix

#### x:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#x "Direct link to x")

The angle to rotate around the xxx axis

#### z:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#z "Direct link to z")

The angle to rotate around the zzz axis

## transform-rotate-ypr [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-rotate-ypr "Direct link to transform-rotate-ypr")

```
transform-rotate-ypr(
a: angle,b: angle,c: angle,) -> matrix
```

Returns a 4×44 \\times 44×4 rotation matrix - yaw-pitch-roll

Calculates the product of the three rotation matrices
R=Rz(a)Ry(b)Rx(c)R = Rz(a) Ry(b) Rx(c)R=Rz(a)Ry(b)Rx(c)

#### a:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#a "Direct link to a")

Yaw

#### b:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#b "Direct link to b")

Pitch

#### c:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#c "Direct link to c")

Roll

## transform-rotate-xyz [​](https://cetz-package.github.io/docs/api/internal/matrix/\#transform-rotate-xyz "Direct link to transform-rotate-xyz")

```
transform-rotate-xyz(
x: angle,y: angle,z: angle,) -> matrix
```

Returns a 4×44 \\times 44×4 rotation matrix - euler angles

Calculates the product of the three rotation matrices
R=Rz(z)Ry(y)Rx(x)R = Rz(z) Ry(y) Rx(x)R=Rz(z)Ry(y)Rx(x)

#### x:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#x "Direct link to x")

Rotation about x

#### y:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#y "Direct link to y")

Rotation about y

#### z:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#z "Direct link to z")

Rotation about z

## mul-mat [​](https://cetz-package.github.io/docs/api/internal/matrix/\#mul-mat "Direct link to mul-mat")

```
mul-mat(
..matrices: matrix,) -> matrix
```

Multiplies matrices on top of each other.

#### ..matrices:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#matrices "Direct link to ..matrices")

The matrices to multiply from left to right.

## mul4x4-vec3 [​](https://cetz-package.github.io/docs/api/internal/matrix/\#mul4x4-vec3 "Direct link to mul4x4-vec3")

```
mul4x4-vec3(
mat: matrix,vec: vector,w: float,) -> vector
```

Multiplies a 4×44 \\times 44×4 matrix with a vector of size 3 or 4. The resulting is three dimensional

#### mat:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#mat "Direct link to mat")

The matrix to multiply

#### vec:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#vec "Direct link to vec")

The vector to multiply

#### w:

[float](https://typst.app/docs/reference/foundations/float)

Default: `1` [​](https://cetz-package.github.io/docs/api/internal/matrix/#w "Direct link to w")

The default value for the fourth element of the vector if it is three dimensional.

## mul-vec [​](https://cetz-package.github.io/docs/api/internal/matrix/\#mul-vec "Direct link to mul-vec")

```
mul-vec(
mat: matrix,vec: vector,) -> vector
```

Multiplies an m×nm \\times nm×n matrix with an mmmth dimensional vector where m\\lte4m \\lte 4m\\lte4. Prefer the use of `mul4x4-vec3` when possible as it does not use loops.

#### mat:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#mat "Direct link to mat")

The matrix to multiply

#### vec:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#vec "Direct link to vec")

The vector to multiply

## inverse [​](https://cetz-package.github.io/docs/api/internal/matrix/\#inverse "Direct link to inverse")

```
inverse(
matrix: matrix,) -> matrix
```

Calculates the inverse matrix of any size.

#### matrix:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#matrix "Direct link to matrix")

The matrix to inverse.

## swap-cols [​](https://cetz-package.github.io/docs/api/internal/matrix/\#swap-cols "Direct link to swap-cols")

```
swap-cols(
mat: matrix,a: int,b: int,) -> matrix
```

Swaps the a-th column with the b-th column.

#### mat:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#mat "Direct link to mat")

Matrix

#### a:

[int](https://typst.app/docs/reference/foundations/int)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#a "Direct link to a")

The index of column a.

#### b:

[int](https://typst.app/docs/reference/foundations/int)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#b "Direct link to b")

The index of column b.

## translate [​](https://cetz-package.github.io/docs/api/internal/matrix/\#translate "Direct link to translate")

```
translate(
mat: matrix,vec: vector,)
```

Translates a matrix by a vector.

#### mat:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#mat "Direct link to mat")

The matrix to translate

#### vec:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/matrix/#vec "Direct link to vec")

The vector to translate by.

- [ident](https://cetz-package.github.io/docs/api/internal/matrix/#ident)
- [diag](https://cetz-package.github.io/docs/api/internal/matrix/#diag)
- [dim](https://cetz-package.github.io/docs/api/internal/matrix/#dim)
- [column](https://cetz-package.github.io/docs/api/internal/matrix/#column)
- [set-column](https://cetz-package.github.io/docs/api/internal/matrix/#set-column)
- [round](https://cetz-package.github.io/docs/api/internal/matrix/#round)
- [transform-translate](https://cetz-package.github.io/docs/api/internal/matrix/#transform-translate)
- [transform-shear-x](https://cetz-package.github.io/docs/api/internal/matrix/#transform-shear-x)
- [transform-shear-z](https://cetz-package.github.io/docs/api/internal/matrix/#transform-shear-z)
- [transform-scale](https://cetz-package.github.io/docs/api/internal/matrix/#transform-scale)
- [transform-rotate-dir](https://cetz-package.github.io/docs/api/internal/matrix/#transform-rotate-dir)
- [transform-rotate-x](https://cetz-package.github.io/docs/api/internal/matrix/#transform-rotate-x)
- [transform-rotate-y](https://cetz-package.github.io/docs/api/internal/matrix/#transform-rotate-y)
- [transform-rotate-z](https://cetz-package.github.io/docs/api/internal/matrix/#transform-rotate-z)
- [transform-rotate-xz](https://cetz-package.github.io/docs/api/internal/matrix/#transform-rotate-xz)
- [transform-rotate-ypr](https://cetz-package.github.io/docs/api/internal/matrix/#transform-rotate-ypr)
- [transform-rotate-xyz](https://cetz-package.github.io/docs/api/internal/matrix/#transform-rotate-xyz)
- [mul-mat](https://cetz-package.github.io/docs/api/internal/matrix/#mul-mat)
- [mul4x4-vec3](https://cetz-package.github.io/docs/api/internal/matrix/#mul4x4-vec3)
- [mul-vec](https://cetz-package.github.io/docs/api/internal/matrix/#mul-vec)
- [inverse](https://cetz-package.github.io/docs/api/internal/matrix/#inverse)
- [swap-cols](https://cetz-package.github.io/docs/api/internal/matrix/#swap-cols)
- [translate](https://cetz-package.github.io/docs/api/internal/matrix/#translate)

## Path Segment Utilities
[Skip to main content](https://cetz-package.github.io/docs/api/internal/path-util/#__docusaurus_skipToContent_fallback)

On this page

## segment-start [​](https://cetz-package.github.io/docs/api/internal/path-util/\#segment-start "Direct link to segment-start")

```
segment-start(
s: segment,) -> vector
```

Returns the first position vector of a path segment.

#### s:

segment

[​](https://cetz-package.github.io/docs/api/internal/path-util/#s "Direct link to s")

Path segment

## segment-end [​](https://cetz-package.github.io/docs/api/internal/path-util/\#segment-end "Direct link to segment-end")

```
segment-end(
s: segment,) -> vector
```

Returns the last position vector of a path segment

#### s:

segment

[​](https://cetz-package.github.io/docs/api/internal/path-util/#s "Direct link to s")

Path segment

## bounds [​](https://cetz-package.github.io/docs/api/internal/path-util/\#bounds "Direct link to bounds")

```
bounds(
segments: array,) -> array
```

Calculates the bounding points for a list of path segments

#### segments:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#segments "Direct link to segments")

List of path segments

## length [​](https://cetz-package.github.io/docs/api/internal/path-util/\#length "Direct link to length")

```
length(
segments: array,) -> float
```

Calculates the length of a path

#### segments:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#segments "Direct link to segments")

List of path segments

## segment-at-t [​](https://cetz-package.github.io/docs/api/internal/path-util/\#segment-at-t "Direct link to segment-at-t")

```
segment-at-t(
segments: array,t: floatratio,rev: bool,samples: int,clamp: bool,) -> dictionary
```

Finds the segment that contains a point that is distance `t` from the start of a path.

#### segments:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#segments "Direct link to segments")

The array of segments that make up the path.

#### t:

[float](https://typst.app/docs/reference/foundations/float) or [ratio](https://typst.app/docs/reference/layout/ratio)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#t "Direct link to t")

The distance to find the segment with. A [float](https://typst.app/docs/reference/foundations/float) will be in absolute distance along the path. A [ratio](https://typst.app/docs/reference/layout/ratio) will be relative to the length of the path. Will panic if the distance is greater than the length of the path.

#### rev:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/path-util/#rev "Direct link to rev")

When true the path will be reversed, effectively looking for the segment from the end of the path.

#### samples:

[int](https://typst.app/docs/reference/foundations/int)

Default: `default-samples` [​](https://cetz-package.github.io/docs/api/internal/path-util/#samples "Direct link to samples")

The number of samples to use when calculating the length of a cubic segment.

#### clamp:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/path-util/#clamp "Direct link to clamp")

Clamps the distance to the length of the path, so the function won't panic.

* * *

Returns a [dictionary](https://typst.app/docs/reference/foundations/dictionary) with the folloing key-value pairs:

#### index:

[int](https://typst.app/docs/reference/foundations/int)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#index "Direct link to index")

The index of the segment in the given array of segments.

#### segment:

segment

[​](https://cetz-package.github.io/docs/api/internal/path-util/#segment "Direct link to segment")

The found segment.

#### travelled:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#travelled "Direct link to travelled")

The absolute distance travelled along the path to find the segment.

#### distance:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#distance "Direct link to distance")

The distance left to travel along the path.

#### length:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#length "Direct link to length")

The length of the returned segment.

## point-on-path [​](https://cetz-package.github.io/docs/api/internal/path-util/\#point-on-path "Direct link to point-on-path")

```
point-on-path(
segments: array,t: intfloatratio,samples: ,extrapolate: bool,) -> none or vector
```

Finds the position of a point a distance from the start of a path. If the path is empty [none](https://typst.app/docs/reference/foundations/none/) will be returned.

#### segments:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#segments "Direct link to segments")

List of path segments

#### t:

[int](https://typst.app/docs/reference/foundations/int) or [float](https://typst.app/docs/reference/foundations/float) or [ratio](https://typst.app/docs/reference/layout/ratio)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#t "Direct link to t")

Absolute position on the path if given an float or integer, or relative position if given a ratio from 0% to 100%. When this value is negative, the point will be found from the end of the path instaed of the start.

#### extrapolate:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/path-util/#extrapolate "Direct link to extrapolate")

If true, use linear extrapolation if distance is outsides the path's range

## direction [​](https://cetz-package.github.io/docs/api/internal/path-util/\#direction "Direct link to direction")

```
direction(
segments: array,t: intfloatratio,samples: ,clamp: bool,) -> array
```

Finds the position and direction of a point a distance along from the start of a path. Returns an [array](https://typst.app/docs/reference/foundations/array) of two vectors where the first is the position, and the second is the direction.

#### segments:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#segments "Direct link to segments")

List of path segments

#### t:

[int](https://typst.app/docs/reference/foundations/int) or [float](https://typst.app/docs/reference/foundations/float) or [ratio](https://typst.app/docs/reference/layout/ratio)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#t "Direct link to t")

Absolute position on the path if given an float or integer, or relative position if given a ratio from 0% to 100%. When this value is negative, the point will be found from the end of the path instaed of the start.

#### extrapolate:

[bool](https://typst.app/docs/reference/foundations/bool)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#extrapolate "Direct link to extrapolate")

If true, use linear extrapolation if distance is outsides the path's range

#### clamp:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/internal/path-util/#clamp "Direct link to clamp")

Clamps the distance between the start and end of a path.

## line-segment [​](https://cetz-package.github.io/docs/api/internal/path-util/\#line-segment "Direct link to line-segment")

```
line-segment(
points: array,) -> segment
```

Creates a line segment with points

#### points:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#points "Direct link to points")

List of points

## cubic-segment [​](https://cetz-package.github.io/docs/api/internal/path-util/\#cubic-segment "Direct link to cubic-segment")

```
cubic-segment(
a: vector,b: vector,ctrl-a: vector,ctrl-b: vector,) -> segment
```

Creates a cubic bezier segment

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#a "Direct link to a")

Start

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#b "Direct link to b")

End

#### ctrl-a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#ctrla "Direct link to ctrl-a")

Control point a

#### ctrl-b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#ctrlb "Direct link to ctrl-b")

Control point b

## normalize [​](https://cetz-package.github.io/docs/api/internal/path-util/\#normalize "Direct link to normalize")

```
normalize(
segments: array,) -> array
```

Normalize segments by connecting gaps via straight line segments and merging multiple line segments into a single one.

#### segments:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#segments "Direct link to segments")

The path segments to normalize.

## shorten-segment [​](https://cetz-package.github.io/docs/api/internal/path-util/\#shorten-segment "Direct link to shorten-segment")

```
shorten-segment(
segment: segment,distance: float,snap-to: nonevector,mode: str,samples: int,) -> segment
```

Shortens a segment by a given distance.

#### segment:

segment

[​](https://cetz-package.github.io/docs/api/internal/path-util/#segment "Direct link to segment")

The segment to shorten.

#### distance:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#distance "Direct link to distance")

The distance to move the start of the segment towards the end of the segment. If this value is negative, the end of the segment will be moved towards the start.

#### snap-to:

[none](https://typst.app/docs/reference/foundations/none/) or [vector](https://cetz-package.github.io/docs/api/internal/vector)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/path-util/#snapto "Direct link to snap-to")

Shortening bezier curves suffers from rounding and precision errors so a position can be given to "snap" a curve's start/end point to.

#### mode:

[str](https://typst.app/docs/reference/foundations/str)

Default: `"CURVED"` [​](https://cetz-package.github.io/docs/api/internal/path-util/#mode "Direct link to mode")

How cubic segments should be shortned. Can be `"LINEAR"` to use `bezier.cubic-shorten-linear` or `"CURVED"` to use `bezier.cubic-shorten`.

#### samples:

[int](https://typst.app/docs/reference/foundations/int)

Default: `default-samples` [​](https://cetz-package.github.io/docs/api/internal/path-util/#samples "Direct link to samples")

The number of samples to use when shortening a cubic segment.

## shorten-path [​](https://cetz-package.github.io/docs/api/internal/path-util/\#shorten-path "Direct link to shorten-path")

```
shorten-path(
segments: segments,start-distance: intfloat,end-distance: intfloat,snap-to: ,mode: ,samples: ,) -> segments Segments of the path that have been shortened
```

Shortens a path's segments by the given distances. The start of the path is shortened first by moving the point along the path towards the end. The end of the path is then shortened in the same way. When a distance is 0 no other calculations are made.

#### segments:

segments

[​](https://cetz-package.github.io/docs/api/internal/path-util/#segments "Direct link to segments")

The segments of the path to shorten.

#### start-distance:

[int](https://typst.app/docs/reference/foundations/int) or [float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#startdistance "Direct link to start-distance")

The distance to shorten from the start of the path.

#### end-distance:

[int](https://typst.app/docs/reference/foundations/int) or [float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/path-util/#enddistance "Direct link to end-distance")

The distance to shorten from the end of the path

#### pos:

[none](https://typst.app/docs/reference/foundations/none/) or tuple

[​](https://cetz-package.github.io/docs/api/internal/path-util/#pos "Direct link to pos")

Tuple of points to "snap" the path ends to

- [segment-start](https://cetz-package.github.io/docs/api/internal/path-util/#segment-start)
- [segment-end](https://cetz-package.github.io/docs/api/internal/path-util/#segment-end)
- [bounds](https://cetz-package.github.io/docs/api/internal/path-util/#bounds)
- [length](https://cetz-package.github.io/docs/api/internal/path-util/#length)
- [segment-at-t](https://cetz-package.github.io/docs/api/internal/path-util/#segment-at-t)
- [point-on-path](https://cetz-package.github.io/docs/api/internal/path-util/#point-on-path)
- [direction](https://cetz-package.github.io/docs/api/internal/path-util/#direction)
- [line-segment](https://cetz-package.github.io/docs/api/internal/path-util/#line-segment)
- [cubic-segment](https://cetz-package.github.io/docs/api/internal/path-util/#cubic-segment)
- [normalize](https://cetz-package.github.io/docs/api/internal/path-util/#normalize)
- [shorten-segment](https://cetz-package.github.io/docs/api/internal/path-util/#shorten-segment)
- [shorten-path](https://cetz-package.github.io/docs/api/internal/path-util/#shorten-path)

## Element Processing API
[Skip to main content](https://cetz-package.github.io/docs/api/internal/process/#__docusaurus_skipToContent_fallback)

On this page

## element [​](https://cetz-package.github.io/docs/api/internal/process/\#element )

```
element(
ctx: ctx,element-func: function,)
```

Processes an element's function to get its drawables and bounds. Returns a [dictionary](https://typst.app/docs/reference/foundations/dictionary) with the key-values: `ctx` The modified context object, `bounds` The aabb of the element's drawables, `drawables` An [array](https://typst.app/docs/reference/foundations/array) of the element's drawables.

#### ctx:

ctx

[​](https://cetz-package.github.io/docs/api/internal/process/#ctx "Direct link to ctx")

The current context object.

#### element-func:

[function](https://typst.app/docs/reference/foundations/function)

[​](https://cetz-package.github.io/docs/api/internal/process/#elementfunc "Direct link to element-func")

A function that when passed ctx, it should return an element dictionary.

## many [​](https://cetz-package.github.io/docs/api/internal/process/\#many "Direct link to many")

```
many(
ctx: ctx,body: array,) -> dictionary
```

Runs the `element` function for a list of element functions and aggregates the results.

#### ctx:

ctx

[​](https://cetz-package.github.io/docs/api/internal/process/#ctx "Direct link to ctx")

The current context object.

#### body:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/process/#body "Direct link to body")

The array of element functions to process.

- [element](https://cetz-package.github.io/docs/api/internal/process/#element)
- [many](https://cetz-package.github.io/docs/api/internal/process/#many)

## Style Resolution
[Skip to main content](https://cetz-package.github.io/docs/api/internal/styles/#__docusaurus_skipToContent_fallback)

On this page

## resolve [​](https://cetz-package.github.io/docs/api/internal/styles/\#resolve "Direct link to resolve")

```
resolve(
dict: style,root: nonestr,merge: style,base: nonestyle,) -> style
```

You can use this to combine the style in `ctx`, the style given by a user for a single element and an element's default style.

`base` is first merged onto `dict` without overwriting existing values, and if `root` is given it is merged onto that key of `dict`. `merge` is then merged onto `dict` but does overwrite existing entries, if `root` is given it is merged onto that key of `dict`. Then entries in `dict` that are [auto](https://typst.app/docs/reference/foundations/auto/) inherit values from their nearest ancestor and entries of type [dictionary](https://typst.app/docs/reference/foundations/dictionary) are merged with their closest ancestor.

```codeBlockLines_e6Vv
#let dict = (
  stroke: "black",
  fill: none,
  mark: (stroke: auto, fill: "blue"),
  line: (stroke: auto, mark: auto, fill: "red")
)
#cetz.styles.resolve(dict, merge: (mark: (stroke: "yellow")), root: "line")

```

![](https://cetz-package.github.io/docs/assets/images/f9964c-69a9f54ec58236d940b642ffdd001c16.svg)

The following is a more detailed explanation of how the algorithm works to use as a reference if needed. It should be updated whenever changes are made.
Remember that dictionaries are recursively merged, if an entry is any other type it is simply updated. (dict + dict = merged dict, value + dict = dict, dict + value = value)
First if `base` is given, it will be merged without overwriting values onto `dict`. If `root` is given it will be merged onto that key of `dict`.
Each level of `dict` is then processed with these steps. If `root` is given the level with that key will be the first, otherwise the whole of `dict` is processed.

- Values on the corresponding level of `merge` are inserted into the level if the key does not exist on the level or if they are not both dictionaries. If they are both dictionaries their values will be inserted in the same stage at a lower level.
- If an entry is `auto` or a dictionary, the tree is travelled back up until an entry with the same key is found. If the current entry is `auto` the value of the ancestor's entry is copied. Or if the current entry and ancestor entry is a dictionary, they are merged with the current entry overwriting any values in it's ancestors.
- Each entry that is a dictionary is then resolved from step 1.

```codeBlockLines_e6Vv
get-ctx(ctx => {
  // Get the current "mark" style
  content((0,0), [#cetz.styles.resolve(ctx.style, root: "mark")])
})

```

![](https://cetz-package.github.io/docs/assets/images/e53d6b-79f1b44b056ea8064a5fb1a6fde0846c.svg)

#### dict:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/internal/styles/#dict "Direct link to dict")

Current context style from `ctx.style`.

#### merge:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

Default: `(:)` [​](https://cetz-package.github.io/docs/api/internal/styles/#merge "Direct link to merge")

Style values overwriting the current style. I.e. inline styles passed with an element: `line(.., stroke: red)`.

#### root:

[none](https://typst.app/docs/reference/foundations/none/) or [str](https://typst.app/docs/reference/foundations/str)

Default: `none` [​](https://cetz-package.github.io/docs/api/internal/styles/#root "Direct link to root")

Style root element name.

#### base:

[none](https://typst.app/docs/reference/foundations/none/) or [style](https://cetz-package.github.io/docs/basics/custom-types#style)

Default: `(:)` [​](https://cetz-package.github.io/docs/api/internal/styles/#base "Direct link to base")

Style values to merge into `dict` without overwriting it.

- [resolve](https://cetz-package.github.io/docs/api/internal/styles/#resolve)

## Vector Transformation Utilities
[Skip to main content](https://cetz-package.github.io/docs/api/internal/util/#__docusaurus_skipToContent_fallback)

On this page

## apply-transform [​](https://cetz-package.github.io/docs/api/internal/util/\#apply-transform "Direct link to apply-transform")

```
apply-transform(
transform: matrixfunction,..vecs: vector,) -> vector or array or dictionary
```

Multiplies vectors by a transformation matrix. If multiple vectors are given they are returned as an array, if only one vector is given only one will be returned, if a dictionary is given they will be returned in the dictionary with the same keys.

#### transform:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix) or [function](https://typst.app/docs/reference/foundations/function)

[​](https://cetz-package.github.io/docs/api/internal/util/#transform "Direct link to transform")

The 4×44 \\times 44×4 transformation matrix or a function that accepts and returns a vector.

#### ..vecs:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#vecs "Direct link to ..vecs")

Vectors to get transformed. Only the positional part of the sink is used. A dictionary of vectors can also be passed and all will be transformed.

## revert-transform [​](https://cetz-package.github.io/docs/api/internal/util/\#revert-transform "Direct link to revert-transform")

```
revert-transform(
transform: matrix,..vecs: ,) -> vector
```

Reverts the transform of the given vector

#### transform:

[matrix](https://cetz-package.github.io/docs/api/internal/matrix)

[​](https://cetz-package.github.io/docs/api/internal/util/#transform "Direct link to transform")

Transformation matrix

#### vec:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#vec "Direct link to vec")

Vector to be transformed

## line-pt [​](https://cetz-package.github.io/docs/api/internal/util/\#line-pt "Direct link to line-pt")

```
line-pt(
a: vector,b: vector,t: float,) -> vector
```

Linearly interpolates between two points and returns its position

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#a "Direct link to a")

Start point

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#b "Direct link to b")

End point

#### t:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/util/#t "Direct link to t")

Position on the line \[0,1\]\[0, 1\]\[0,1\]

## line-normal [​](https://cetz-package.github.io/docs/api/internal/util/\#line-normal "Direct link to line-normal")

```
line-normal(
a: vector,b: vector,) -> vector
```

Get orthogonal vector to line

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#a "Direct link to a")

Start point

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#b "Direct link to b")

End point

## circle-arclen [​](https://cetz-package.github.io/docs/api/internal/util/\#circle-arclen "Direct link to circle-arclen")

```
circle-arclen(
radius: float,angle: angle,) -> float
```

Calculates the arc-length of a circle or arc

#### radius:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/util/#radius "Direct link to radius")

Circle or arc radius

#### angle:

[angle](https://typst.app/docs/reference/layout/angle)

Default: `360deg` [​](https://cetz-package.github.io/docs/api/internal/util/#angle "Direct link to angle")

The angle of the arc.

## ellipse-point [​](https://cetz-package.github.io/docs/api/internal/util/\#ellipse-point "Direct link to ellipse-point")

```
ellipse-point(
center: vector,radius: floatarray,angle: ,) -> vector
```

Get point on an ellipse for an angle

#### center:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#center "Direct link to center")

Center

#### radius:

[float](https://typst.app/docs/reference/foundations/float) or [array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/util/#radius "Direct link to radius")

Radius or tuple of x/y radii

#### angled:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/util/#angled "Direct link to angled")

Angle to get the point at

## calculate-circle-center-3pt [​](https://cetz-package.github.io/docs/api/internal/util/\#calculate-circle-center-3pt "Direct link to calculate-circle-center-3pt")

```
calculate-circle-center-3pt(
a: vector,b: vector,c: vector,) -> vector
```

Calculates the center of a circle from 3 points. The z coordinate is taken from point a.

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#a "Direct link to a")

Point 1

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#b "Direct link to b")

Point 2

#### c:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#c "Direct link to c")

Point 3

## resolve-number [​](https://cetz-package.github.io/docs/api/internal/util/\#resolve-number "Direct link to resolve-number")

```
resolve-number(
ctx: context,num: number,) -> float
```

Converts a [number](https://cetz-package.github.io/docs/basics/custom-types#number) to "canvas units"

#### ctx:

[context](https://cetz-package.github.io/docs/advanced/custom-types#context)

[​](https://cetz-package.github.io/docs/api/internal/util/#ctx "Direct link to ctx")

The current context object.

#### num:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

[​](https://cetz-package.github.io/docs/api/internal/util/#num "Direct link to num")

The number to resolve.

## resolve-radius [​](https://cetz-package.github.io/docs/api/internal/util/\#resolve-radius "Direct link to resolve-radius")

```
resolve-radius(
radius: numberarray,) -> array
```

Ensures that a radius has an `x` and `y` component.

## min [​](https://cetz-package.github.io/docs/api/internal/util/\#min "Direct link to min")

```
min(
..a: ,) -> float
```

Finds the minimum of a set of values while ignoring [none](https://typst.app/docs/reference/foundations/none/) values.

## max [​](https://cetz-package.github.io/docs/api/internal/util/\#max "Direct link to max")

```
max(
..a: floatnone,) -> float
```

Finds the maximum of a set of values while ignoring [none](https://typst.app/docs/reference/foundations/none/) values.

## merge-dictionary [​](https://cetz-package.github.io/docs/api/internal/util/\#merge-dictionary "Direct link to merge-dictionary")

```
merge-dictionary(
a: dictionary,b: dictionary,overwrite: bool,) -> dictionary
```

Merges dictionary `b` onto dictionary `a`. If a key does not exist in `a` but does in `b`, it is inserted into `a` with `b`'s value. If a key does exist in `a` and `b`, the value in `b` is only inserted into `a` if the `overwrite` argument is `true`. If a key does exist both in `a` and `b` and both values are of type [dictionary](https://typst.app/docs/reference/foundations/dictionary) they will be recursively merged with this same function.

#### a:

[dictionary](https://typst.app/docs/reference/foundations/dictionary)

[​](https://cetz-package.github.io/docs/api/internal/util/#a "Direct link to a")

Dictionary a

#### b:

[dictionary](https://typst.app/docs/reference/foundations/dictionary)

[​](https://cetz-package.github.io/docs/api/internal/util/#b "Direct link to b")

Dictionary b

#### overwrite:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `true` [​](https://cetz-package.github.io/docs/api/internal/util/#overwrite "Direct link to overwrite")

Whether to override an entry in `a` that also exists in `b` with the value in `b`.

## measure [​](https://cetz-package.github.io/docs/api/internal/util/\#measure "Direct link to measure")

```
measure(
ctx: context,cnt: content,) -> vector
```

Measures the size of some [content](https://typst.app/docs/reference/foundations/content) in canvas coordinates.

#### ctx:

[context](https://cetz-package.github.io/docs/advanced/custom-types#context)

[​](https://cetz-package.github.io/docs/api/internal/util/#ctx "Direct link to ctx")

The current context object.

#### cnt:

[content](https://typst.app/docs/reference/foundations/content)

[​](https://cetz-package.github.io/docs/api/internal/util/#cnt "Direct link to cnt")

The content to measure.

## as-padding-dict [​](https://cetz-package.github.io/docs/api/internal/util/\#as-padding-dict "Direct link to as-padding-dict")

```
as-padding-dict(
padding: nonenumberarraydictionary,) -> dictionary
```

Get a padding/margin dictionary with keys `(top, left, bottom, right)` from a padding value.

Type of `padding`:

- [none](https://typst.app/docs/reference/foundations/none/): All sides padded by 0
- [number](https://cetz-package.github.io/docs/basics/custom-types#number): All sides are padded by the same value
- [array](https://typst.app/docs/reference/foundations/array): CSS like padding: `(y, x)`, `(top, x, bottom)` or `(top, right, bottom, left)`
- [dictionary](https://typst.app/docs/reference/foundations/dictionary): Converts a Typst padding dictionary (top, left, bottom, right, x, y, rest) to a dictionary containing top, left, bottom and right.

#### padding:

[none](https://typst.app/docs/reference/foundations/none/) or [number](https://cetz-package.github.io/docs/basics/custom-types#number) or [array](https://typst.app/docs/reference/foundations/array) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

[​](https://cetz-package.github.io/docs/api/internal/util/#padding "Direct link to padding")

Padding specification

## as-corner-radius-dict [​](https://cetz-package.github.io/docs/api/internal/util/\#as-corner-radius-dict "Direct link to as-corner-radius-dict")

```
as-corner-radius-dict(
ctx: context,radii: nonenumberdictionary,size: ???,) -> dictionary
```

Creates a corner-radius dictionary with keys `north-east`, `north-west`, `south-east` and `south-west` with values of a two element [array](https://typst.app/docs/reference/foundations/array) of the radius in the `x` and `y` direction. Returns none if all radii are zero or none.

#### ctx:

[context](https://cetz-package.github.io/docs/advanced/custom-types#context)

[​](https://cetz-package.github.io/docs/api/internal/util/#ctx "Direct link to ctx")

The current canvas context object

#### radii:

[none](https://typst.app/docs/reference/foundations/none/) or [number](https://cetz-package.github.io/docs/basics/custom-types#number) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

[​](https://cetz-package.github.io/docs/api/internal/util/#radii "Direct link to radii")

The radius specification. A [number](https://cetz-package.github.io/docs/basics/custom-types#number) will cause all corners to have the same radius. An [array](https://typst.app/docs/reference/foundations/array) with two items will cause all corners to have the same rx and ry radius. A [dictionary](https://typst.app/docs/reference/foundations/dictionary) can be given where the key specifies the corner and the value specifies the radius. The value can be either [number](https://cetz-package.github.io/docs/basics/custom-types#number) for a circle radius or [array](https://typst.app/docs/reference/foundations/array) for an x and y radius. The keys `north`, `south`, `east` and `west` targets both corners in that cardinal direction e.g. `south` sets the south west and south east corners. The keys `north-east`, `north-west`, `south-east` and `south-west` targets the corresponding corner. The key `rest` targets all other corners that have not been target by other keys.

#### size:

???

[​](https://cetz-package.github.io/docs/api/internal/util/#size "Direct link to size")

I'm not sure what this does.

## sort-points-by-distance [​](https://cetz-package.github.io/docs/api/internal/util/\#sort-points-by-distance "Direct link to sort-points-by-distance")

```
sort-points-by-distance(
base: vector,pts: array,) -> array
```

Sorts an array of vectors by distance to a common position.

#### base:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/util/#base "Direct link to base")

The position to measure the distance of the other vectors from.

#### pts:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/internal/util/#pts "Direct link to pts")

The array of vectors to sort.

## resolve-stroke [​](https://cetz-package.github.io/docs/api/internal/util/\#resolve-stroke "Direct link to resolve-stroke")

```
resolve-stroke(
stroke: nonestroke,) -> dictionary
```

Resolves a stroke into a usable dictionary with all fields that are missing or auto set to their Typst defaults.

#### stroke:

[none](https://typst.app/docs/reference/foundations/none/) or [stroke](https://typst.app/docs/reference/visualize/stroke)

[​](https://cetz-package.github.io/docs/api/internal/util/#stroke "Direct link to stroke")

The stroke to resolve.

## assert-body [​](https://cetz-package.github.io/docs/api/internal/util/\#assert-body "Direct link to assert-body")

```
assert-body(
body: ,)
```

Asserts whether a "body" has the correct type.

- [apply-transform](https://cetz-package.github.io/docs/api/internal/util/#apply-transform)
- [revert-transform](https://cetz-package.github.io/docs/api/internal/util/#revert-transform)
- [line-pt](https://cetz-package.github.io/docs/api/internal/util/#line-pt)
- [line-normal](https://cetz-package.github.io/docs/api/internal/util/#line-normal)
- [circle-arclen](https://cetz-package.github.io/docs/api/internal/util/#circle-arclen)
- [ellipse-point](https://cetz-package.github.io/docs/api/internal/util/#ellipse-point)
- [calculate-circle-center-3pt](https://cetz-package.github.io/docs/api/internal/util/#calculate-circle-center-3pt)
- [resolve-number](https://cetz-package.github.io/docs/api/internal/util/#resolve-number)
- [resolve-radius](https://cetz-package.github.io/docs/api/internal/util/#resolve-radius)
- [min](https://cetz-package.github.io/docs/api/internal/util/#min)
- [max](https://cetz-package.github.io/docs/api/internal/util/#max)
- [merge-dictionary](https://cetz-package.github.io/docs/api/internal/util/#merge-dictionary)
- [measure](https://cetz-package.github.io/docs/api/internal/util/#measure)
- [as-padding-dict](https://cetz-package.github.io/docs/api/internal/util/#as-padding-dict)
- [as-corner-radius-dict](https://cetz-package.github.io/docs/api/internal/util/#as-corner-radius-dict)
- [sort-points-by-distance](https://cetz-package.github.io/docs/api/internal/util/#sort-points-by-distance)
- [resolve-stroke](https://cetz-package.github.io/docs/api/internal/util/#resolve-stroke)
- [assert-body](https://cetz-package.github.io/docs/api/internal/util/#assert-body)

## Vector Operations API
[Skip to main content](https://cetz-package.github.io/docs/api/internal/vector/#__docusaurus_skipToContent_fallback)

On this page

An [array](https://typst.app/docs/reference/foundations/array) of any number of [float](https://typst.app/docs/reference/foundations/float)s.

## as-mat [​](https://cetz-package.github.io/docs/api/internal/vector/\#as-mat "Direct link to as-mat")

```
as-mat(
v: vector,mode: str,) -> matrix
```

Converts a vector to a row or column matrix.

#### v:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v "Direct link to v")

The vector to convert.

#### mode:

[str](https://typst.app/docs/reference/foundations/str)

Default: `"row"` [​](https://cetz-package.github.io/docs/api/internal/vector/#mode "Direct link to mode")

The type of matrix to convert into. Must be one of `"row"` or `"column"`.

## as-vec [​](https://cetz-package.github.io/docs/api/internal/vector/\#as-vec "Direct link to as-vec")

```
as-vec(
0: ,v: vector,init: vector,) -> vector
```

Ensures a vector has an exact number of components. This is done by passing another vector `init` that has the required dimension. If the original vector does not have enough dimensions, the values from `init` will be inserted. It is recommended to use a zero vector for `init`.

#### v:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v "Direct link to v")

The vector to ensure.

#### init:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

Default: `(0` [​](https://cetz-package.github.io/docs/api/internal/vector/#init "Direct link to init")

The vector to check the dimension against.

## len [​](https://cetz-package.github.io/docs/api/internal/vector/\#len "Direct link to len")

```
len(
v: vector,) -> float
```

Return length/magnitude of a vector.

#### v:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v "Direct link to v")

The vector to find the magnitude of.

## add [​](https://cetz-package.github.io/docs/api/internal/vector/\#add "Direct link to add")

```
add(
v1: vector,v2: vector,) -> vector
```

Adds two vectors of the same dimension

#### v1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v1 "Direct link to v1")

The vector on the left hand side.

#### v2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v2 "Direct link to v2")

The vector on the right hand side.

## sub [​](https://cetz-package.github.io/docs/api/internal/vector/\#sub "Direct link to sub")

```
sub(
v1: vector,v2: vector,) -> vector
```

Subtracts two vectors of the same dimension

#### v1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v1 "Direct link to v1")

The vector on the left hand side.

#### v2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v2 "Direct link to v2")

The vector on the right hand side.

## dist [​](https://cetz-package.github.io/docs/api/internal/vector/\#dist "Direct link to dist")

```
dist(
a: vector,b: vector,) -> float
```

Calculates the distance between two vectors by subtracting the length of vector `a` from vector `b`.

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#a "Direct link to a")

Vector a

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#b "Direct link to b")

Vector b

## scale [​](https://cetz-package.github.io/docs/api/internal/vector/\#scale "Direct link to scale")

```
scale(
v: vector,x: float,) -> vector
```

Multiplys a vector with scalar `x`

#### v:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v "Direct link to v")

The vector to scale.

#### x:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/vector/#x "Direct link to x")

The scale factor.

## div [​](https://cetz-package.github.io/docs/api/internal/vector/\#div "Direct link to div")

```
div(
v: vector,x: float,)
```

Divides a vector by scalar `x`

#### v:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v "Direct link to v")

The vector to be divded.

#### x:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/vector/#x "Direct link to x")

The inverse scale factor.

## neg [​](https://cetz-package.github.io/docs/api/internal/vector/\#neg "Direct link to neg")

```
neg(
v: vector,) -> vector
```

Negates each value in a vector

#### v:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v "Direct link to v")

The vector to negate.

## norm [​](https://cetz-package.github.io/docs/api/internal/vector/\#norm "Direct link to norm")

```
norm(
v: vector,) -> vector
```

Normalizes a vector (divide by its length)

#### v:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v "Direct link to v")

The vector to normalize.

## element-product [​](https://cetz-package.github.io/docs/api/internal/vector/\#element-product "Direct link to element-product")

```
element-product(
a: vector,b: vector,)
```

Multiply two vectors component-wise

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#a "Direct link to a")

First vector.

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#b "Direct link to b")

Second vector.

## dot [​](https://cetz-package.github.io/docs/api/internal/vector/\#dot "Direct link to dot")

```
dot(
v1: vector,v2: vector,) -> float
```

Calculates the dot product between two vectors.

#### v1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v1 "Direct link to v1")

The vector on the left hand side.

#### v2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v2 "Direct link to v2")

The vector on the right hand side.

## cross [​](https://cetz-package.github.io/docs/api/internal/vector/\#cross "Direct link to cross")

```
cross(
v1: vector,v2: vector,) -> vector
```

Calculates the cross product of two vectors with a dimension of three.

#### v1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v1 "Direct link to v1")

The vector on the left hand side.

#### v2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v2 "Direct link to v2")

The vector on the right hand side.

## angle2 [​](https://cetz-package.github.io/docs/api/internal/vector/\#angle2 "Direct link to angle2")

```
angle2(
a: vector,b: vector,) -> angle
```

Calculates the angle between two vectors and the x-axis in 2d space

#### a:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#a "Direct link to a")

The vector to measure the angle from.

#### b:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#b "Direct link to b")

The vector to measure the angle to.

## angle [​](https://cetz-package.github.io/docs/api/internal/vector/\#angle "Direct link to angle")

```
angle(
v1: vector,c: vector,v2: vector,)
```

Calculates the angle between three vectors

#### v1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v1 "Direct link to v1")

The vector to measure the angle from.

#### c:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#c "Direct link to c")

The vector to measure the angle at.

#### v2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v2 "Direct link to v2")

The vector to measure the angle to.

## lerp [​](https://cetz-package.github.io/docs/api/internal/vector/\#lerp "Direct link to lerp")

```
lerp(
v1: vector,v2: vector,t: float,)
```

Linear interpolation between two vectors.

#### v1:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v1 "Direct link to v1")

The vector to interpolate from.

#### v2:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v2 "Direct link to v2")

The vector to interpolate to.

#### t:

[float](https://typst.app/docs/reference/foundations/float)

[​](https://cetz-package.github.io/docs/api/internal/vector/#t "Direct link to t")

The factor to interpolate by. A value of `0` is `v1` and a value of `1` is `v2`.

## rotate-z [​](https://cetz-package.github.io/docs/api/internal/vector/\#rotate-z "Direct link to rotate-z")

```
rotate-z(
v: vector,angle: angle,) -> vector
```

Rotates a vector of dimension 2 or 3 around the z-axis by an angle.

#### v:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

[​](https://cetz-package.github.io/docs/api/internal/vector/#v "Direct link to v")

The vector to rotate.

#### angle:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/api/internal/vector/#angle "Direct link to angle")

The angle to rotate by.

- [as-mat](https://cetz-package.github.io/docs/api/internal/vector/#as-mat)
- [as-vec](https://cetz-package.github.io/docs/api/internal/vector/#as-vec)
- [len](https://cetz-package.github.io/docs/api/internal/vector/#len)
- [add](https://cetz-package.github.io/docs/api/internal/vector/#add)
- [sub](https://cetz-package.github.io/docs/api/internal/vector/#sub)
- [dist](https://cetz-package.github.io/docs/api/internal/vector/#dist)
- [scale](https://cetz-package.github.io/docs/api/internal/vector/#scale)
- [div](https://cetz-package.github.io/docs/api/internal/vector/#div)
- [neg](https://cetz-package.github.io/docs/api/internal/vector/#neg)
- [norm](https://cetz-package.github.io/docs/api/internal/vector/#norm)
- [element-product](https://cetz-package.github.io/docs/api/internal/vector/#element-product)
- [dot](https://cetz-package.github.io/docs/api/internal/vector/#dot)
- [cross](https://cetz-package.github.io/docs/api/internal/vector/#cross)
- [angle2](https://cetz-package.github.io/docs/api/internal/vector/#angle2)
- [angle](https://cetz-package.github.io/docs/api/internal/vector/#angle)
- [lerp](https://cetz-package.github.io/docs/api/internal/vector/#lerp)
- [rotate-z](https://cetz-package.github.io/docs/api/internal/vector/#rotate-z)

## CeTZ Libraries Functions
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/#__docusaurus_skipToContent_fallback)

Functions of CeTZ's libraries.

## Angle Drawing Functions
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/angle/#__docusaurus_skipToContent_fallback)

Provides helper functions to draw angles and right angles.

## Angle Drawing API
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/angle/angle/#__docusaurus_skipToContent_fallback)

On this page

```
angle(
origin: coordinate,a: coordinate,b: coordinate,direction: string,label: nonecontentfunction,name: nonestr,..style: style,)
```

Draw an angle counter-clock-wise between `a` and `b` through origin `origin`

```codeBlockLines_e6Vv
line((0,0), (1,1.5), name: "a")
line((0,0), (2,-1), name: "b")

// Draw an angle between the two lines
cetz.angle.angle("a.start", "a.end", "b.end", label: $ alpha $,
  mark: (end: ">"), radius: 1.5)
cetz.angle.angle("a.start", "b.end", "a.end", label: $ alpha' $,
  radius: 50%, direction: "cw")

```

![](<Base64-Image-Removed>)

#### origin:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/angle/angle/#origin "Direct link to origin")

Angle origin

#### a:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/angle/angle/#a "Direct link to a")

Coordinate of side `a`, containing an angle between `origin` and `b`.

#### b:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/angle/angle/#b "Direct link to b")

Coordinate of side `b`, containing an angle between `origin` and `a`.

#### direction:

string

Default: `"ccw"` [​](https://cetz-package.github.io/docs/api/libraries/angle/angle/#direction "Direct link to direction")

Direction of the angle. Accepts "cw" (clockwise) and "ccw" (counter-clockwise), the latter being the default.

#### label:

[none](https://typst.app/docs/reference/foundations/none/) or [content](https://typst.app/docs/reference/foundations/content) or [function](https://typst.app/docs/reference/foundations/function)

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/angle/angle/#label "Direct link to label")

Draw a label at the angles "label" anchor. If label is a function, it gets the angle value passed as argument. The function must be of the format `angle => content`.

#### name:

[none](https://typst.app/docs/reference/foundations/none/) or [str](https://typst.app/docs/reference/foundations/str)

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/angle/angle/#name "Direct link to name")

Element name, used for querying anchors.

#### ..style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/libraries/angle/angle/#style "Direct link to ..style")

Style key-value pairs.

## Styling [​](https://cetz-package.github.io/docs/api/libraries/angle/angle/\#styling "Direct link to Styling")

_Root:_ `angle` \

#### radius:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0.5` [​](https://cetz-package.github.io/docs/api/libraries/angle/angle/#radius "Direct link to radius")

The radius of the angles arc. If of type `ratio`, it is relative to the smaller distance of either origin to a or origin to b.

#### label-radius:

[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [ratio](https://typst.app/docs/reference/layout/ratio)

Default: `50%` [​](https://cetz-package.github.io/docs/api/libraries/angle/angle/#labelradius "Direct link to label-radius")

The radius of the angles label origin. If of type `ratio`, it is relative to `radius`.

## Anchors [​](https://cetz-package.github.io/docs/api/libraries/angle/angle/\#anchors "Direct link to Anchors")

- **a** Point a
- **b** Point b
- **origin** Origin
- **label** Label center
- **start** Arc start
- **end** Arc end

- [Styling](https://cetz-package.github.io/docs/api/libraries/angle/angle/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/libraries/angle/angle/#anchors)

## Right Angle Drawing
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/#__docusaurus_skipToContent_fallback)

On this page

```
right-angle(
origin: coordinate,a: coordinate,b: coordinate,label: nonecontent,name: nonestr,..style: style,)
```

Draw a right angle between `a` and `b` through origin `origin`

```codeBlockLines_e6Vv
line((0,0), (1,2), name: "a")
line((0,0), (2,-1), name: "b")

// Draw an angle between the two lines
cetz.angle.right-angle(
  "a.start",
  "a.end",
  "b.end",
  radius: 1.5
)

```

![](<Base64-Image-Removed>)

#### origin:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/#origin "Direct link to origin")

Angle origin

#### a:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/#a "Direct link to a")

Coordinate of side `a`, containing an angle between `origin` and `b`.

#### b:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/#b "Direct link to b")

Coordinate of side `b`, containing an angle between `origin` and `a`.

#### label:

[none](https://typst.app/docs/reference/foundations/none/) or [content](https://typst.app/docs/reference/foundations/content)

Default: `"•"` [​](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/#label "Direct link to label")

Draw a label at the angles "label" anchor.

#### name:

[none](https://typst.app/docs/reference/foundations/none/) or [str](https://typst.app/docs/reference/foundations/str)

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/#name "Direct link to name")

Element name, used for querying anchors.

#### ..style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/#style "Direct link to ..style")

Style key-value pairs.

## Styling [​](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/\#styling "Direct link to Styling")

Styling is the same as the `angle` function.

## Anchors [​](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/\#anchors "Direct link to Anchors")

Anchors are the same as the `angle` function

- [Styling](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/libraries/angle/right-angle/#anchors)

## Shapes and Modifications
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/decorations/#__docusaurus_skipToContent_fallback)

Various pre-made shapes and path modifications.

## Cetz Braces Documentation
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/decorations/braces/#__docusaurus_skipToContent_fallback)

## Curly Brace Decoration
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#__docusaurus_skipToContent_fallback)

On this page

```
brace(
start: coordinate,end: coordinate,..style: style,name: stringnone,)
```

Draw a curly brace between two points.

```codeBlockLines_e6Vv
cetz.decorations.brace((0,1),(2,1))

cetz.decorations.brace((0,0),(2,0),
  pointiness: 45deg, outer-pointiness: 45deg)
cetz.decorations.brace((0,-1),(2,-1),
  pointiness: 90deg, outer-pointiness: 90deg)

```

![](<Base64-Image-Removed>)

#### start:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#start "Direct link to start")

Start point

#### end:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#end "Direct link to end")

End point

#### name:

string or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#name "Direct link to name")

Element name used for querying anchors

#### ..style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#style "Direct link to ..style")

Style key-value pairs

## Styling [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/\#styling "Direct link to Styling")

_Root:_ `brace`

#### amplitude:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0.5` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#amplitude "Direct link to amplitude")

Sets the height of the brace, from its baseline to its middle tip.

#### pointiness:

[ratio](https://typst.app/docs/reference/layout/ratio) or [angle](https://typst.app/docs/reference/layout/angle)

Default: `15deg` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#pointiness "Direct link to pointiness")

How pointy the spike should be. `0deg` or `100%` for maximum pointiness, `90deg` or `0%` for minimum.

#### outer-pointiness:

[ratio](https://typst.app/docs/reference/layout/ratio) or [angle](https://typst.app/docs/reference/layout/angle)

Default: `15deg` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#outerpointiness "Direct link to outer-pointiness")

How pointy the outer edges should be. `0deg` or `100%` for maximum pointiness (allowing for a smooth transition to a straight line), `90deg` or `0%` for minimum. Setting this to [auto](https://typst.app/docs/reference/foundations/auto/) will use the value set for `pointiness`.

#### content-offset:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0.3` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#contentoffset "Direct link to content-offset")

Offset of the `"content"` anchor from the spike of the brace.

#### flip:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#flip "Direct link to flip")

Mirror the brace along the line between start and end.

## Anchors [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/\#anchors "Direct link to Anchors")

- **start** Where the brace starts, same as the `start` parameter.
- **end** Where the brace end, same as the `end` parameter.
- **spike** Point of the spike, halfway between `start` and `end` and shifted by `amplitude` towards the pointing direction.
- **content** Point to place content/text at, in front of the spike.
- **center** Center of the enclosing rectangle.

- [Styling](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/libraries/decorations/braces/brace/#anchors)

## Flat Brace Decoration
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#__docusaurus_skipToContent_fallback)

On this page

```
flat-brace(
start: coordinate,end: coordinate,flip: bool,debug: bool,name: strnone,..style: style,)
```

Draw a flat curly brace between two points.

```codeBlockLines_e6Vv
cetz.decorations.flat-brace((0,1),(2,1))

cetz.decorations.flat-brace((0,0),(2,0),
  curves: .2,
  aspect: 25%)
cetz.decorations.flat-brace((0,-1),(2,-1),
  outer-curves: 0,
  aspect: 75%)

```

![](<Base64-Image-Removed>)

This mimics the braces from TikZ's [`decorations.pathreplacing` library](https://github.com/pgf-tikz/pgf/blob/6e5fd71581ab04351a89553a259b57988bc28140/tex/generic/pgf/libraries/decorations/pgflibrarydecorations.pathreplacing.code.tex#L136-L185).
In contrast to the `brace` function, these braces use straight line segments, resulting in better looks for long braces with a small amplitude.

#### start:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#start "Direct link to start")

Start point

#### end:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#end "Direct link to end")

End point

#### flip:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#flip "Direct link to flip")

Flip the brace around

#### name:

[str](https://typst.app/docs/reference/foundations/str) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#name "Direct link to name")

Element name for querying anchors

#### ..style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#style "Direct link to ..style")

Style key-value pairs

## Styling [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/\#styling "Direct link to Styling")

_Root:_ `flat-brace`

#### amplitude:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0.3` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#amplitude "Direct link to amplitude")

Determines how much the brace rises above the base line.

- aspect (ratio) = 50% Determines the fraction of the total length where the spike will be placed.







#### curves:



[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)



Default: `auto` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#curves "Direct link to curves")



Curviness factor of the brace, a factor of 0 means no curves.









#### outer-curves:



[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [auto](https://typst.app/docs/reference/foundations/auto/) or [array](https://typst.app/docs/reference/foundations/array)



Default: `auto` [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#outercurves "Direct link to outer-curves")



Curviness factor of the outer curves of the brace. A factor of 0 means no curves.


## Anchors [​](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/\#anchors "Direct link to Anchors")

- **start** Where the brace starts, same as the `start` parameter.
- **end** Where the brace end, same as the `end` parameter.
- **spike** Point of the spike's top.
- **content** Point to place content/text at, in front of the spike.
- **center** Center of the enclosing rectangle.

- [Styling](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#styling)
- [Anchors](https://cetz-package.github.io/docs/api/libraries/decorations/braces/flat-brace/#anchors)

## Path Decorations Overview
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/decorations/path/#__docusaurus_skipToContent_fallback)

Path decorations are elements that accept a path as input and generate one or more shapes that follow that path.

All path decoration functions support the following style keys:

#### start:

[ratio](https://typst.app/docs/reference/layout/ratio) or [length](https://typst.app/docs/reference/layout/length)

Default: `0%` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/#start "Direct link to start")

Absolute or relative start of the decoration on the path.

#### end:

[ratio](https://typst.app/docs/reference/layout/ratio) or [length](https://typst.app/docs/reference/layout/length)

Default: `100%` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/#end "Direct link to end")

Absolute or relative end of the decoration on the path.

#### rest:

[str](https://typst.app/docs/reference/foundations/str)

Default: `LINE` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/#rest "Direct link to rest")

If set to `"LINE"`, generate lines between the path's start/end and the
decoration's start/end if the path is _not closed_.

#### width:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `1` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/#width "Direct link to width")

Width or thickness of the decoration.

#### segments:

[int](https://typst.app/docs/reference/foundations/int)

Default: `10` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/#segments "Direct link to segments")

The number of repetitions/phases to generate. This key is ignored if
`segment-length` is not [none](https://typst.app/docs/reference/foundations/none/)

#### segment-length:

[none](https://typst.app/docs/reference/foundations/none/) or [number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/#segmentlength "Direct link to segment-length")

Length of one repetion/phase of the decoration.

#### align:

[str](https://typst.app/docs/reference/foundations/str)

Default: `'START'` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/#align "Direct link to align")

Alignment of the decoration on the path _if `segment-length` is set_ and the
decoration does not fill up the full range between start and stop. Can be one
of `"START"`, `"MID"`, `"END`.

## Coil Decoration API
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/decorations/path/coil/#__docusaurus_skipToContent_fallback)

On this page

```
coil(
target: drawable,close: autobool,name: nonestring,..style: style,)
```

Draw a stretched coil/loop spring along a path

The number of windings can be controlled via the `segments` or `segment-length` style key, and the width via `amplitude`.

```codeBlockLines_e6Vv
line((0,0), (2,1), stroke: gray)
cetz.decorations.coil(line((0,0), (2,1)), amplitude: .25, start: 10%, stop: 90%)

```

![](<Base64-Image-Removed>)

#### target:

drawable

[​](https://cetz-package.github.io/docs/api/libraries/decorations/path/coil/#target "Direct link to target")

Target path

#### close:

[auto](https://typst.app/docs/reference/foundations/auto/) or [bool](https://typst.app/docs/reference/foundations/bool)

Default: `auto` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/coil/#close "Direct link to close")

Close the path

#### name:

[none](https://typst.app/docs/reference/foundations/none/) or string

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/coil/#name "Direct link to name")

Element name

#### ..style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/libraries/decorations/path/coil/#style "Direct link to ..style")

Style

## Styling [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/coil/\#styling "Direct link to Styling")

_Root_: `coil`

#### factor:

[ratio](https://typst.app/docs/reference/layout/ratio)

Default: `150%` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/coil/#factor "Direct link to factor")

Factor of how much the coil overextends its length to form a curl.

- [Styling](https://cetz-package.github.io/docs/api/libraries/decorations/path/coil/#styling)

## Wave Path Decoration
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/decorations/path/wave/#__docusaurus_skipToContent_fallback)

On this page

```
wave(
target: drawable,close: autobool,name: nonestring,..style: style,)
```

Draw a wave along a path using a catmull-rom curve

The number of phases can be controlled via the `segments` or `segment-length` style key, and the width via `amplitude`.

```codeBlockLines_e6Vv
line((0,0), (2,1), stroke: gray)
cetz.decorations.wave(line((0,0), (2,1)), amplitude: .25, start: 10%, stop: 90%)

```

![](<Base64-Image-Removed>)

#### target:

drawable

[​](https://cetz-package.github.io/docs/api/libraries/decorations/path/wave/#target "Direct link to target")

Target path

#### close:

[auto](https://typst.app/docs/reference/foundations/auto/) or [bool](https://typst.app/docs/reference/foundations/bool)

Default: `auto` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/wave/#close "Direct link to close")

Close the path

#### name:

[none](https://typst.app/docs/reference/foundations/none/) or string

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/wave/#name "Direct link to name")

Element name

#### ..style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/libraries/decorations/path/wave/#style "Direct link to ..style")

Style

## Styling [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/wave/\#styling "Direct link to Styling")

_Root_: `wave`

- tension (float) = 0.5 Catmull-Rom curve tension, see [Catmull](https://cetz-package.github.io/docs/api/draw-functions/shapes/catmull)

- [Styling](https://cetz-package.github.io/docs/api/libraries/decorations/path/wave/#styling)

## Zigzag Path Decoration
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/decorations/path/zigzag/#__docusaurus_skipToContent_fallback)

On this page

```
zigzag(
target: drawable,name: nonestring,close: autobool,..style: style,)
```

Draw a zig-zag or saw-tooth wave along a path.

The number of tooths can be controlled via the `segments` or `segment-length` style key, and the width via `amplitude`.

```codeBlockLines_e6Vv
line((0,0), (2,1), stroke: gray)
cetz.decorations.zigzag(line((0,0), (2,1)), amplitude: .25, start: 10%, stop: 90%)

```

![](<Base64-Image-Removed>)

#### target:

drawable

[​](https://cetz-package.github.io/docs/api/libraries/decorations/path/zigzag/#target "Direct link to target")

Target path

#### close:

[auto](https://typst.app/docs/reference/foundations/auto/) or [bool](https://typst.app/docs/reference/foundations/bool)

Default: `auto` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/zigzag/#close "Direct link to close")

Close the path

#### name:

[none](https://typst.app/docs/reference/foundations/none/) or string

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/zigzag/#name "Direct link to name")

Element name

#### ..style:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

[​](https://cetz-package.github.io/docs/api/libraries/decorations/path/zigzag/#style "Direct link to ..style")

Style

## Styling [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/zigzag/\#styling "Direct link to Styling")

_Root_: `zigzag`

#### factor:

[ratio](https://typst.app/docs/reference/layout/ratio)

Default: `100%` [​](https://cetz-package.github.io/docs/api/libraries/decorations/path/zigzag/#factor "Direct link to factor")

Triangle mid between its start and end. Setting this to 0% leads to a falling sawtooth shape, while 100% results in a raising sawtooth.

- [Styling](https://cetz-package.github.io/docs/api/libraries/decorations/path/zigzag/#styling)

## Palette Functions Overview
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/palette/#__docusaurus_skipToContent_fallback)

On this page

A palette is a function of the form `index => style` that takes an index, that can be any [int](https://typst.app/docs/reference/foundations/int) and returns a canvas style dictionary. If passed the string `"len"` it must return the length of its unique styles. An example use for palette functions is the plot library, which can use palettes to apply different styles per plot.

## Predefined Palettes [​](https://cetz-package.github.io/docs/api/libraries/palette/\#predefined-palettes "Direct link to Predefined Palettes")

- [Predefined Palettes](https://cetz-package.github.io/docs/api/libraries/palette/#predefined-palettes)

## New Color Palette
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/palette/new/#__docusaurus_skipToContent_fallback)

```
new(
base: style,colors: nonearray,dash: nonearray,) -> function
```

Create a new palette based on a base style

```codeBlockLines_e6Vv
let p = cetz.palette.new(colors: (red, blue, green))
for i in range(0, p("len")) {
  set-style(..p(i))
  circle((0,0), radius: .5)
  set-origin((1.1, 0))
}

```

![](<Base64-Image-Removed>)

The functions returned by this function have the following named arguments:

#### fill:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `true` [​](https://cetz-package.github.io/docs/api/libraries/palette/new/#fill "Direct link to fill")

If true, the returned fill color is one of the colors from the `colors` list, otherwise the base styles fill is used.

#### stroke:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/api/libraries/palette/new/#stroke "Direct link to stroke")

If true, the returned stroke color is one of the colors from the `colors` list, otherwise the base styles stroke color is used.

You can use a palette for stroking via: `red.with(stroke: true)`.

#### base:

[style](https://cetz-package.github.io/docs/basics/custom-types#style)

Default: `base-style` [​](https://cetz-package.github.io/docs/api/libraries/palette/new/#base "Direct link to base")

Style dictionary to use as base style for the styles generated per color

#### colors:

[none](https://typst.app/docs/reference/foundations/none/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `()` [​](https://cetz-package.github.io/docs/api/libraries/palette/new/#colors "Direct link to colors")

List of colors the returned palette should return styles with.

#### dash:

[none](https://typst.app/docs/reference/foundations/none/) or [array](https://typst.app/docs/reference/foundations/array)

Default: `()` [​](https://cetz-package.github.io/docs/api/libraries/palette/new/#dash "Direct link to dash")

List of stroke dash patterns the returned palette should return styles with.

## Tree Library Documentation
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/tree/#__docusaurus_skipToContent_fallback)

The tree library allows the drawing diagrams with simple tree layout algorithms.

## Tree Structure Rendering
[Skip to main content](https://cetz-package.github.io/docs/api/libraries/tree/tree/#__docusaurus_skipToContent_fallback)

```
tree(
root: array,draw-node: autofunction,draw-edge: noneautofunction,direction: str,parent-position: str,grow: float,spread: float,name: nonestr,node-layer: int,edge-layer: int,)
```

Lays out and renders tree nodes.

For each node, the `tree` function creates an anchor of the format `"node-<depth>-<child-index>"` that can be used to query a nodes position on the canvas.

```codeBlockLines_e6Vv
import cetz.tree
set-style(content: (padding: .1))
tree.tree(([Root], ([A], [A.A], [A.B]), ([B], [B.A])))

```

![](https://cetz-package.github.io/docs/assets/images/b38bd5-c657e346680fd4a2a9928a3f8defa620.svg)

#### root:

[array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#root "Direct link to root")

A nested array of content that describes the structure the tree should take. Example: `([root], [child 1], ([child 2], [grandchild 1]))`

#### draw-node:

[auto](https://typst.app/docs/reference/foundations/auto/) or [function](https://typst.app/docs/reference/foundations/function)

Default: `auto` [​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#drawnode "Direct link to draw-node")

The function to call to draw a node. The function will be passed two positional arguments, the node to draw and the node's parent, and is expected to return elements ( `(node, parent-node) => elements`). The node's position is accessible through the "center" anchor or by using the previous position coordinate `()`. If `auto` is given, just the node's value will be drawn as content. The following predefined styles can be used:

#### draw-edge:

[none](https://typst.app/docs/reference/foundations/none/) or [auto](https://typst.app/docs/reference/foundations/auto/) or [function](https://typst.app/docs/reference/foundations/function)

Default: `auto` [​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#drawedge "Direct link to draw-edge")

The function to call draw an edge between two nodes. The function will be passed the name of the starting node, the name of the ending node, the start node, the end node, and is expected to return elements ( `(source-name, target-name, parent-node, child-node) => elements`). If `auto` is given, a straight line will be drawn between nodes.

#### direction:

[str](https://typst.app/docs/reference/foundations/str)

Default: `"down"` [​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#direction "Direct link to direction")

A string describing the direction the tree should grow in ("up", "down", "left", "right")

#### parent-position:

[str](https://typst.app/docs/reference/foundations/str)

Default: `"center"` [​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#parentposition "Direct link to parent-position")

Positioning of parent nodes (begin, center, end)

#### grow:

[float](https://typst.app/docs/reference/foundations/float)

Default: `1` [​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#grow "Direct link to grow")

Depth grow factor

#### spread:

[float](https://typst.app/docs/reference/foundations/float)

Default: `1` [​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#spread "Direct link to spread")

Sibling spread factor

#### name:

[none](https://typst.app/docs/reference/foundations/none/) or [str](https://typst.app/docs/reference/foundations/str)

Default: `none` [​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#name "Direct link to name")

The tree element's name

#### node-layer:

[int](https://typst.app/docs/reference/foundations/int)

Default: `1` [​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#nodelayer "Direct link to node-layer")

Layer to draw nodes on

#### edge-layer:

[int](https://typst.app/docs/reference/foundations/int)

Default: `0` [​](https://cetz-package.github.io/docs/api/libraries/tree/tree/#edgelayer "Direct link to edge-layer")

Layer to draw edges on

## CeTZ Package Functions
[Skip to main content](https://cetz-package.github.io/docs/api/overview/#__docusaurus_skipToContent_fallback)

This section is a reference for all functions in the CeTZ package and its libraries.

## CeTZ Basics
[Skip to main content](https://cetz-package.github.io/docs/basics/#__docusaurus_skipToContent_fallback)

The following chapters are about the basic and core concepts of CeTZ. They are recommended reading for basic usage.

## Anchors in Element Positioning
[Skip to main content](https://cetz-package.github.io/docs/basics/anchors/#__docusaurus_skipToContent_fallback)

On this page

You can refer to a position relative to an element by using its anchors. Anchors come in three different variations but can all be used in two ways.

The first is by using the `anchor` argument on an element. When given, the element will be translated such that the given anchor will be where the given position is. This is supported by all elements that have the `anchor` argument.

```codeBlockLines_e6Vv
// Draw a circle and place its "west" anchor at the origin.
circle((0,0), anchor: "west")

// Draw a smaller red circle at the origin.
fill(red)
stroke(none)
circle((0,0), radius: 0.3)

```

![](<Base64-Image-Removed>)

The second is by using [anchor coordinates](https://cetz-package.github.io/docs/basics/coordinate-systems#anchor). You must first give the element a name by passing a string to its `name` argument, you can then use its anchors to place other elements. Note that this is only available for elements that have a `name` argument.

```codeBlockLines_e6Vv
// Name the circle
circle((0,0), name: "circle")

// Draw a smaller red circle at "circle"'s east anchor
fill(red)
stroke(none)
circle("circle.east", radius: 0.3)

```

![](<Base64-Image-Removed>)

## Named [​](https://cetz-package.github.io/docs/basics/anchors/\#named "Direct link to Named")

Named anchors are normally unique to the type of element, such as a bezier curve's control points. Other border and path anchors specify their own named anchors that are available to all elements that support border or path anchors.

Elements that have an `anchor` argument also have a "default" named anchor. You can use it by just giving the element's name without an anchor.

## Border [​](https://cetz-package.github.io/docs/basics/anchors/\#border "Direct link to Border")

A border anchor refers to a point on the element's border where a ray is cast from the element's center at a given angle and hits the border.

They are given as angles where `0deg` is towards the right and `90deg` is up.

Border anchors also specify named compass directions such as "north", "north-east", etc. Border anchors also specify a "center" named anchor which is where the ray cast originates from.

```codeBlockLines_e6Vv
circle((0, 0), name: "circle", radius: 1)

set-style(content: (frame: "rect", stroke: none, fill: white, padding: .1))
content((name: "circle", anchor: 0deg), [0deg], anchor: "west")
content((name: "circle", anchor: 160deg), [160deg], anchor: "south-east")
content("circle.north", [North], anchor: "south")
content("circle.south-east", [South East], anchor: "north-west")
content("circle.south-west", [South West], anchor: "north-east")

```

![](https://cetz-package.github.io/docs/assets/images/9110d0-02a656ff5cd0f9920bf6f1f73bbb76f0.svg)

## Path [​](https://cetz-package.github.io/docs/basics/anchors/\#path "Direct link to Path")

A path anchor refers to a point along the path of an element. They can be given as either a [number](https://cetz-package.github.io/docs/basics/custom-types#number) for an absolute distance along the path, or a [ratio](https://typst.app/docs/reference/layout/ratio) for a relative distance along the path.

Path anchors also specify three anchors "start", "mid" and "end".

```codeBlockLines_e6Vv
line((0,0), (10, 1), name: "line")

set-style(content: (frame: "rect", stroke: none, fill: white, padding: .1))
content("line.start", [0%, 0, "start"], anchor: "east")
content("line.mid", [50%, "mid"])
content("line.end", [100%, "end"], anchor: "west")

content((name: "line", anchor: 75%), [75%])
content((name: "line", anchor: 50pt), [50pt])

```

![](https://cetz-package.github.io/docs/assets/images/95542d-fa16d36295e07768ef60d214a82fe5af.svg)

- [Named](https://cetz-package.github.io/docs/basics/anchors/#named)
- [Border](https://cetz-package.github.io/docs/basics/anchors/#border)
- [Path](https://cetz-package.github.io/docs/basics/anchors/#path)

## Canvas Function Guide
[Skip to main content](https://cetz-package.github.io/docs/basics/canvas/#__docusaurus_skipToContent_fallback)

The [`canvas`](https://cetz-package.github.io/docs/api/internal/canvas) function is what handles all of the logic and processing in order to produce drawings. It's usually called with a code block `{...}` as argument. The content of the curly braces is the _body_ of the canvas. Import all the draw functions you need at the top of the body:

```codeBlockLines_e6Vv
#cetz.canvas({
  import cetz.draw: *

})

```

You can now call the draw functions within the body and they'll produce some graphics! Typst will evaluate the code block and pass the result to the `canvas` function for rendering.

The canvas does not have typical `width` and `height` parameters. Instead its size will grow and shrink to fit the drawn graphic.

By default 1 [coordinate](https://cetz-package.github.io/docs/basics/coordinate-systems) unit is `1cm`, this can be changed by setting the `length` parameter. If a ratio is given, the length will be the size of the canvas' parent's width!

## Coordinate Systems Overview
[Skip to main content](https://cetz-package.github.io/docs/basics/coordinate-systems/#__docusaurus_skipToContent_fallback)

On this page

A [coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate) is a position on the canvas on which the picture is drawn. They take the form of dictionaries and the following sub-sections define the key value pairs for each system. Some systems have a more implicit form as an array of values and CeTZ attempts to infer the system based on the element types.

## XYZ [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#xyz "Direct link to XYZ")

Defines a point `x` units right, `y` units upward and `z` units away.

#### x:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0` [​](https://cetz-package.github.io/docs/basics/coordinate-systems/#x "Direct link to x")

The number of units in the `x` direction.

#### y:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0` [​](https://cetz-package.github.io/docs/basics/coordinate-systems/#y "Direct link to y")

The number of units in the `y` direction.

#### z:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0` [​](https://cetz-package.github.io/docs/basics/coordinate-systems/#z "Direct link to z")

The number of units in the `z` direction.

The implicit form can be given as an [array](https://typst.app/docs/reference/foundations/array) of two or three [number](https://cetz-package.github.io/docs/basics/custom-types#number)s, as in `(x, y)` or `(x, y, z)`

```codeBlockLines_e6Vv
line((0,0), (x: 1))
line((0,0), (y: 1))
line((0,0), (z: 1))

// Implicit form
line((2, 0), (3, 0))
line((2, 0), (2, 1, 0))
line((2, 0), (2, 0, 1))

```

![](<Base64-Image-Removed>)

## Previous [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#previous "Direct link to Previous")

Use this to reference the position of the previous coordinate passed to a draw function. It takes the form of an empty [array](https://typst.app/docs/reference/foundations/array) `()` and the previous position initially will be `(0, 0, 0)`. This will never reference the position of a coordinate used to define another coordinate.

```codeBlockLines_e6Vv
line((0,0), (1, 1))

// Draws a circle at (1,1)
circle(())

```

![](<Base64-Image-Removed>)

## Relative [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#relative "Direct link to Relative")

Places the given coordinate relative to the previous coordinate. Or in other words, for the given coordinate, the previous coordinate will be used as the origin. Another coordinate can be given to act as the previous coordinate instead.

#### rel:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#rel "Direct link to rel")

The coordinate to place relative to the previous coordinate.

#### update:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `true` [​](https://cetz-package.github.io/docs/basics/coordinate-systems/#update "Direct link to update")

When false the previous the previous position will not be updated.

#### to:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

Default: `()` [​](https://cetz-package.github.io/docs/basics/coordinate-systems/#to "Direct link to to")

The coordinate to treat as the previous coordinate.

In the example below, the red circle is placed one unit to the right of the blue circle. If the blue circle was to be moved a different position, the red circle will move with the blue circle to stay one unit to the right.

```codeBlockLines_e6Vv
circle((0, 0), stroke: blue)
circle((rel: (1, 0)), stroke: red)

```

![](<Base64-Image-Removed>)

## Polar [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#polar "Direct link to Polar")

Defines a point that is `radius` distance away from the origin at the given angle.

#### angle:

[angle](https://typst.app/docs/reference/layout/angle)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#angle "Direct link to angle")

The angle of the coordinate. An value of `0deg` is to the right, a degree of `90deg` is upward.

#### radius:

[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [array](https://typst.app/docs/reference/foundations/array)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#radius "Direct link to radius")

The distance from the origin. An [array](https://typst.app/docs/reference/foundations/array) of [number](https://cetz-package.github.io/docs/basics/custom-types#number) can be given, in the form `(x, y)`, to define the `x` and `y` radii of an ellipse instead of a circle.

```codeBlockLines_e6Vv
line((0, 0), (angle: 30deg, radius: 1))

```

![](<Base64-Image-Removed>)

The implicit form is an array of the angle then the radius `(angle, radius)` or `(angle, (x, y))`.

```codeBlockLines_e6Vv
line(
  (0, 0),
  (30deg, 1),
  (60deg, 1),
  (90deg, 1),
  (120deg, 1),
  (150deg, 1),
  (180deg, 1)
)

```

![](<Base64-Image-Removed>)

## Barycentric [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#barycentric "Direct link to Barycentric")

In the barycentric coordinate system a point is expressed as the linear combination of multiple vectors. The idea is that you specify vectors v1,v2,...,vnv\_1, v\_2, ..., v\_nv1​,v2​,...,vn​ and numbers α1,α2,...,αn\\alpha\_1, \\alpha\_2, ..., \\alpha\_nα1​,α2​,...,αn​. Then the barycentric coordinate specified by these vectors and numbers is

α1v1+α2v2+⋯+αnvnα1+α2+⋯+αn\\frac{\\alpha\_1 v\_1 + \\alpha\_2 v\_2 + \\cdots + \\alpha\_n v\_n}{\\alpha\_1 + \\alpha\_2 + \\cdots + \\alpha\_n}α1​+α2​+⋯+αn​α1​v1​+α2​v2​+⋯+αn​vn​​

#### bary:

[dictionary](https://typst.app/docs/reference/foundations/dictionary)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#bary "Direct link to bary")

A dictionary where the key is a named element and the value is a
[float](https://typst.app/docs/reference/foundations/float). The `center` anchor of the named element is used as vvv
and the value is used as α\\alphaα

```codeBlockLines_e6Vv
circle((90deg, 3), radius: 0, name: "content")
circle((210deg, 3), radius: 0, name: "structure")
circle((-30deg, 3), radius: 0, name: "form")

for (c, a) in (
  ("content", "south"),
  ("structure", "north"),
  ("form", "north")
) {
  content(c, align(center, c + [\ oriented]), padding: .1, anchor: a)
}

stroke(gray + 1.2pt)
line("content", "structure", "form", close: true)

for (c, s, f, cont) in (
  (0.5, 0.1, 1, "PostScript"),
  (1, 0, 0.4, "DVI"),
  (0.5, 0.5, 1, "PDF"),
  (0, 0.25, 1, "CSS"),
  (0.5, 1, 0, "XML"),
  (0.5, 1, 0.4, "HTML"),
  (1, 0.2, 0.8, "LaTeX"),
  (1, 0.6, 0.8, "TeX"),
  (0.8, 0.8, 1, "Word"),
  (1, 0.05, 0.05, "ASCII")
) {
  content(
    (bary: (
      content: c,
      structure: s,
      form: f
    )),
    cont,
    fill: rgb(50, 50, 255, 100),
    stroke: none,
    frame: "circle"
  )
}

```

![](https://cetz-package.github.io/docs/assets/images/de0d6c-5623d312f94192f4e71c606487817416.svg)

## Anchor [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#anchor "Direct link to Anchor")

Defines a point relative to a named element using anchors, see [Anchors](https://cetz-package.github.io/docs/basics/anchors).

#### name:

[str](https://typst.app/docs/reference/foundations/str)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#name "Direct link to name")

The name of the element that you wish to use to specify a coordinate.

#### anchor:

[str](https://typst.app/docs/reference/foundations/str) or [angle](https://typst.app/docs/reference/layout/angle) or [number](https://cetz-package.github.io/docs/basics/custom-types#number) or [ratio](https://typst.app/docs/reference/layout/ratio) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/basics/coordinate-systems/#anchor "Direct link to anchor")

The anchor of the element. Strings are named anchors, angles are border
anchors and numbers and ratios are path anchors. If not given, the default
anchor will be used, on most elements this is `center` but it can be different or not exist at all!

```codeBlockLines_e6Vv
circle((0,0), name: "circle")
// Anchor at 30 degree
content((name: "circle", anchor: 30deg), box(fill: white, $ 30 degree $))
// Anchor at 30% of the path length
content((name: "circle", anchor: 30%), box(fill: white, $ 30 % $))
// Anchor at 3.14 of the path
content((name: "circle", anchor: 3.14), box(fill: white, $ p = 3.14 $))

```

![](https://cetz-package.github.io/docs/assets/images/cb3f57-b032b8e7fed214db12dfe2b2ece16de7.svg)

You can also use implicit syntax of a dot separated string in the form `"name.anchor"` for all anchors.

```codeBlockLines_e6Vv
line((0, 0), (4, 3), name: "line")
circle("line.75%", name: "circle")
rect("line.start", "circle.east")

```

![](<Base64-Image-Removed>)

When using named elements within a group, you can access the element's anchors outside of the group by using the implicit anchor coordinate. e.g. `"a.b.north"`

```codeBlockLines_e6Vv
group(name: "a", {
  circle((), name: "b")
})
circle("a.b.south", radius: 0.2)
circle((name: "a", anchor: "b.north"), radius: 0.2)

```

![](<Base64-Image-Removed>)

## Tangent [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#tangent "Direct link to Tangent")

This system allows you to compute the point that lies tangent to a shape. In detail, consider an element and a point. Now draw a straight line from the point so that it "touches" the element (more formally, so that it is _tangent_ to this element). The point where the line touches the shape is the point referred to by this coordinate system.

#### element:

[str](https://typst.app/docs/reference/foundations/str)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#element )

The name of the element on whose border the tangent should lie.

#### point:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#point "Direct link to point")

The point through which the tangent should go.

#### solution:

[int](https://typst.app/docs/reference/foundations/int)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#solution "Direct link to solution")

Which solution should be used if there are more than one.

A special algorithm is needed in order to compute the tangent for a given shape. Currently it does this by assuming the distance between the center and top anchor (See [Anchors](https://cetz-package.github.io/docs/basics/anchors)) is the radius of a circle.

```codeBlockLines_e6Vv
grid((0,0), (3,2), help-lines: true)

circle((3,2), name: "a", radius: 2pt)
circle((1,1), name: "c", radius: 0.75)
content("c", $ c $, anchor: "north-east", padding: .1)

line(
  // The starting point or element
  "a",
  // The tangent coordinate
  (element: "c", point: "a", solution: 1),
  // The center of the circle
  "c",
  // The other tangent coordinate
  (element: "c", point: "a", solution: 2),
  "a",
  stroke: red
)

```

![](<Base64-Image-Removed>)

## Perpendicular [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#perpendicular "Direct link to Perpendicular")

Can be used to find the intersection of a vertical line going through a point ppp and a horizontal line going through some other point qqq.

#### horizontal:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#horizontal "Direct link to horizontal")

The coordinate through which the horizontal line passes.

#### vertical:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#vertical "Direct link to vertical")

The coordinate through which the vertical line passes.

You can use the implicit syntax of `(horizontal, "|-", vertical)` or `(vertical, "-|", horizontal)`.

```codeBlockLines_e6Vv
set-style(content: (padding: .05))
content((30deg, 1), $ p_1 $, name: "p1")
content((75deg, 1), $ p_2 $, name: "p2")

line((-0.2, 0), (1.2, 0), name: "xline")
content("xline.end", $ q_1 $, anchor: "west")

line((2, -0.2), (2, 1.2), name: "yline")
content("yline.end", $ q_2 $, anchor: "south")

line("p1.south-east", (horizontal: (), vertical: "xline.end"))
line("p2.south-east", ((), "|-", "xline.end")) // Short form
line("p1.south-east", (vertical: (), horizontal: "yline.end"))
line("p2.south-east", ((), "-|", "yline.end")) // Short form

```

![](https://cetz-package.github.io/docs/assets/images/1995f3-cc79df0f8aff087b99c308563762537b.svg)

## Interpolation [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#interpolation "Direct link to Interpolation")

Use this to linearly interpolate between two coordinates `a` and `b` with a given distance `number`. If `number` is a [number](https://cetz-package.github.io/docs/basics/custom-types#number) the position will be at the absolute distance away from `a` towards `b`, a [ratio](https://typst.app/docs/reference/layout/ratio) can be given instead to be the relative distance between `a` and `b`. An [angle](https://typst.app/docs/reference/layout/angle) can also be given for the general meaning: "First consider the line from `a` to `b`. Then rotate this line by `angle` around point `a`. Then the two endpoints of this line will be `a` and some point `c`. Use the point `c` for the subsequent computation."

#### a:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#a "Direct link to a")

The coordinate to interpolate from.

#### b:

[coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#b "Direct link to b")

The coordinate to interpolate to.

#### number:

[ratio](https://typst.app/docs/reference/layout/ratio) or [number](https://cetz-package.github.io/docs/basics/custom-types#number)

[​](https://cetz-package.github.io/docs/basics/coordinate-systems/#number "Direct link to number")

The distance between `a` and `b`. A [ratio](https://typst.app/docs/reference/layout/ratio) will be the relative
distance between the two points, a [number](https://cetz-package.github.io/docs/basics/custom-types#number) will be the absolute
distance between the two points.

#### angle:

[angle](https://typst.app/docs/reference/layout/angle)

Default: `0deg` [​](https://cetz-package.github.io/docs/basics/coordinate-systems/#angle "Direct link to angle")

Angle between AB⃗\\vec{AB}AB and AP⃗\\vec{AP}AP, where PPP is the resulting
coordinate. This can be used to get the _normal_ for a tangent between two
points.

Can be used implicitly as an array in the form `(a, number, b)` or `(a, number, angle, b)`.

```codeBlockLines_e6Vv
grid((0,0), (3,3), help-lines: true)

line((0,0), (2,2), name: "a")
for i in (0%, 20%, 50%, 80%, 100%, 125%) { // Relative distance
  content(("a.start", i, "a.end"),
  box(fill: white, inset: 1pt, [#i]))
}

line((1,0), (3,2), name: "b")
for i in (0, 0.5, 1, 2) { // Absolute distance
  content(("b.start", i, "b.end"),
  box(fill: white, inset: 1pt, text(red, [#i])))
}

```

![](https://cetz-package.github.io/docs/assets/images/855609-463c3b6309e10a6cc4fa5e1d5157150b.svg)

* * *

```codeBlockLines_e6Vv
grid((0,0), (3,3), help-lines: true)
line((1,0), (3,2))
line((1,0), ((1, 0), 1, 10deg, (3,2)))
fill(red)
stroke(none)
circle(((1, 0), 50%, 10deg, (3, 2)), radius: 2pt)

```

![](<Base64-Image-Removed>)

* * *

```codeBlockLines_e6Vv
grid((0,0), (4,4), help-lines: true)

fill(black)
stroke(none)
let n = 16
for i in range(0, n+1) {
  circle(((2,2), i / 8, i * 22.5deg, (3,2)), radius: 2pt)
}

```

![](<Base64-Image-Removed>)

You can even chain them together!

```codeBlockLines_e6Vv
grid((0,0), (3, 2), help-lines: true)
line((0,0), (3,2))
stroke(red)
line(((0,0), 0.3, (3,2)), (3,0))
fill(red)
stroke(none)
circle(
  ( // a
    (((0, 0), .3, (3, 2))),
    0.7,
    (3,0)
  ),
  radius: 2pt
)

```

![](<Base64-Image-Removed>)

* * *

```codeBlockLines_e6Vv
grid((0,0), (3, 2), help-lines: true)
line((1,0), (3,2))
for (l, c) in ((0cm, "0cm"), (1cm, "1cm"), (15mm, "15mm")) {
  content(((1,0), l, (3,2)), box(fill: white, $ #c $))
}

```

![](https://cetz-package.github.io/docs/assets/images/c93ddb-8b0ba2bfbf60b9981a3c0b487805bf7a.svg)

Interpolation coordinates can be used to get the _normal_ on a tangent:

```codeBlockLines_e6Vv
let (a, b) = ((0,0), (3,2))
line(a, b)
// Get normal for tangent from a to () with distance .5, at a
circle(a, radius: .1, fill: black)
line((a, .7, b), (a: (), b: a, number: .5, angle: 90deg), stroke: red)

```

![](<Base64-Image-Removed>)

## Function [​](https://cetz-package.github.io/docs/basics/coordinate-systems/\#function "Direct link to Function")

An array where the first element is a function and the rest are coordinates will cause the function to be called with the resolved coordinates. The resolved coordinates will be given as a [vector](https://cetz-package.github.io/docs/api/internal/vector) that represents an xyz point in space.

The example below shows how to use this system to create an offset from an anchor, however this could easily be replaced with a [relative coordinate](https://cetz-package.github.io/docs/basics/coordinate-systems/#relative) with the `to` argument set.

```codeBlockLines_e6Vv
circle((0, 0), name: "c")
fill(red)
circle((v => cetz.vector.add(v, (0, -1)), "c.west"), radius: 0.3)

```

![](<Base64-Image-Removed>)

- [XYZ](https://cetz-package.github.io/docs/basics/coordinate-systems/#xyz)
- [Previous](https://cetz-package.github.io/docs/basics/coordinate-systems/#previous)
- [Relative](https://cetz-package.github.io/docs/basics/coordinate-systems/#relative)
- [Polar](https://cetz-package.github.io/docs/basics/coordinate-systems/#polar)
- [Barycentric](https://cetz-package.github.io/docs/basics/coordinate-systems/#barycentric)
- [Anchor](https://cetz-package.github.io/docs/basics/coordinate-systems/#anchor)
- [Tangent](https://cetz-package.github.io/docs/basics/coordinate-systems/#tangent)
- [Perpendicular](https://cetz-package.github.io/docs/basics/coordinate-systems/#perpendicular)
- [Interpolation](https://cetz-package.github.io/docs/basics/coordinate-systems/#interpolation)
- [Function](https://cetz-package.github.io/docs/basics/coordinate-systems/#function)

## CeTZ Custom Types
[Skip to main content](https://cetz-package.github.io/docs/basics/custom-types/#__docusaurus_skipToContent_fallback)

On this page

Many CeTZ functions expect data in certain formats which we will call types. Note that these are actually made up of Typst primitives.

## [coordinate](https://cetz-package.github.io/docs/basics/custom-types\#coordinate) [​](https://cetz-package.github.io/docs/basics/custom-types/\#coordinate "Direct link to coordinate")

A position on the canvas specified by any coordinate system. See [Coordinate Systems](https://cetz-package.github.io/docs/basics/coordinate-systems).

## [number](https://cetz-package.github.io/docs/basics/custom-types\#number) [​](https://cetz-package.github.io/docs/basics/custom-types/\#number "Direct link to number")

Any of [float](https://typst.app/docs/reference/foundations/float), [int](https://typst.app/docs/reference/foundations/int) or [length](https://typst.app/docs/reference/layout/length).

## [style](https://cetz-package.github.io/docs/basics/custom-types\#style) [​](https://cetz-package.github.io/docs/basics/custom-types/\#style "Direct link to style")

Represents options passed to draw functions that affect how elements are drawn. They are normally taken in the form of named arguments to the draw functions or sometimes can be a dictionary for a single argument.

- [coordinate](https://cetz-package.github.io/docs/basics/custom-types/#coordinate)
- [number](https://cetz-package.github.io/docs/basics/custom-types/#number)
- [style](https://cetz-package.github.io/docs/basics/custom-types/#style)

## Customizing Arrow Marks
[Skip to main content](https://cetz-package.github.io/docs/basics/marks/#__docusaurus_skipToContent_fallback)

Marks are arrow tips that can be added to the end of path based elements that support the `mark` style key, or can be directly drawn by using the `mark` draw function. Marks are specified by giving their names (or shorthand) as strings and have several options to customise them. You can give an array of names to have multiple marks, and dictionaries can be used in the array for per mark styling.

![](https://cetz-package.github.io/docs/assets/images/c7cf4f-ecab5962b0ab77b3172c2b6b7bc1ee0c.svg)

```codeBlockLines_e6Vv
let c = ((rel: (0, -1)), (rel: (2, 0), update: false)) // Coordinates to draw the line, it is not necessary to understand this for this example.

// No marks
line((), (rel: (1, 0), update: false))

// Draws a triangle mark at both ends of the line.
set-style(mark: (symbol: ">"))
line(..c)

// Overrides the end mark to be a diamond but the start is still a triangle.
set-style(mark: (end: "<>"))
line(..c)

// Draws two triangle marks at both ends but the first mark of end is still a diamond.
set-style(mark: (symbol: (">", ">")))
line(..c)

// Sets the stroke of first mark in the sequence to red but the end mark overrides it to be blue.
set-style(mark: (symbol: ((symbol: ">", stroke: red), ">"), end: (stroke: blue)))
line(..c)

```

![](<Base64-Image-Removed>)

* * *

#### symbol:

[none](https://typst.app/docs/reference/foundations/none/) or [str](https://typst.app/docs/reference/foundations/str) or [array](https://typst.app/docs/reference/foundations/array) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

Default: `none` [​](https://cetz-package.github.io/docs/basics/marks/#symbol "Direct link to symbol")

This option sets the mark to draw when using the `mark` draw function, or
applies styling to both mark ends of path based elements. The mark's name or
shorthand can be given. Multiple marks can be drawn by passing an array of
names or shorthands. When `none`, no marks will be drawn. A style
[dictionary](https://typst.app/docs/reference/foundations/dictionary) can be given instead of a [str](https://typst.app/docs/reference/foundations/str) to override
styling for that particular mark, just make sure to still give the mark name
using the `symbol` key otherwise nothing will be drawn!

#### start:

[none](https://typst.app/docs/reference/foundations/none/) or [str](https://typst.app/docs/reference/foundations/str) or [array](https://typst.app/docs/reference/foundations/array) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

Default: `none` [​](https://cetz-package.github.io/docs/basics/marks/#start "Direct link to start")

This option sets the mark to draw at the start of a path based element. It
will override all options of the `symbol` key and will not affect marks drawn
using the `mark` draw function.

#### end:

[none](https://typst.app/docs/reference/foundations/none/) or [str](https://typst.app/docs/reference/foundations/str) or [array](https://typst.app/docs/reference/foundations/array) or [dictionary](https://typst.app/docs/reference/foundations/dictionary)

Default: `none` [​](https://cetz-package.github.io/docs/basics/marks/#end "Direct link to end")

Like `start` but for the mark at the end of a path.

#### length:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0.2cm` [​](https://cetz-package.github.io/docs/basics/marks/#length "Direct link to length")

The size of the mark in the direction it is pointing.

#### width:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0.15cm` [​](https://cetz-package.github.io/docs/basics/marks/#width "Direct link to width")

The size of the mark along the normal of its direction.

#### inset:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0.05cm` [​](https://cetz-package.github.io/docs/basics/marks/#inset "Direct link to inset")

It specifies a distance by which something inside the arrow tip is set
inwards; for the stealth arrow tip it is the distance by which the back angle
is moved inwards.

#### scale:

[float](https://typst.app/docs/reference/foundations/float)

Default: `1` [​](https://cetz-package.github.io/docs/basics/marks/#scale "Direct link to scale")

A factor that is applied to the mark's length, width and inset.

#### sep:

[number](https://cetz-package.github.io/docs/basics/custom-types#number)

Default: `0.1cm` [​](https://cetz-package.github.io/docs/basics/marks/#sep "Direct link to sep")

The distance between multiple marks along their path.

#### flex:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `true` [​](https://cetz-package.github.io/docs/basics/marks/#flex "Direct link to flex")

Only applicable when marks are used on curves such as bezier and hobby. If
true, the mark will point along the secant of the curve. If false, the tangent
at the mark's tip will be used.

#### position-samples:

[int](https://typst.app/docs/reference/foundations/int)

Default: `30` [​](https://cetz-package.github.io/docs/basics/marks/#positionsamples "Direct link to position-samples")

Only applicable when marks are used on curves such as bezier and hobby. The
maximum number of samples to use for calculating curve positions. A higher
number gives better results but may slow down compilation

#### pos:

[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [ratio](https://typst.app/docs/reference/layout/ratio) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/basics/marks/#pos "Direct link to pos")

Overrides the mark's position along a path. A number will move it an absolute
distance, while a ratio will be a distance relative to the length of the path.
Note that this may be removed in the future in preference of a different
method.

#### offset:

[number](https://cetz-package.github.io/docs/basics/custom-types#number) or [ratio](https://typst.app/docs/reference/layout/ratio) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/basics/marks/#offset "Direct link to offset")

Like `pos` but it advances the position of the mark instead of overriding it.

#### anchor:

[str](https://typst.app/docs/reference/foundations/str)

Default: `tip` [​](https://cetz-package.github.io/docs/basics/marks/#anchor "Direct link to anchor")

Anchor to position the mark at. Can be one of `base`, `center` or `tip`.

#### slant:

[ratio](https://typst.app/docs/reference/layout/ratio)

Default: `0%` [​](https://cetz-package.github.io/docs/basics/marks/#slant "Direct link to slant")

How much to slant the mark relative to the axis of the arrow. 0% means no
slant 100% slants at 45 degrees.

#### harpoon:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/basics/marks/#harpoon "Direct link to harpoon")

When true only the top half of the mark is drawn.

#### flip:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/basics/marks/#flip "Direct link to flip")

When true the mark is flipped along its axis.

#### reverse:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `false` [​](https://cetz-package.github.io/docs/basics/marks/#reverse "Direct link to reverse")

Reverses the direction of the mark.

#### xy-up:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

Default: `(0, 0, 1)` [​](https://cetz-package.github.io/docs/basics/marks/#xyup "Direct link to xy-up")

The direction which is "up" for use when drawing 2D marks.

#### z-up:

[vector](https://cetz-package.github.io/docs/api/internal/vector)

Default: `(0, 1, 0)` [​](https://cetz-package.github.io/docs/basics/marks/#zup "Direct link to z-up")

The direction which is "up" for use when drawing 3D marks.

#### shorten-to:

[int](https://typst.app/docs/reference/foundations/int) or [auto](https://typst.app/docs/reference/foundations/auto/) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `auto` [​](https://cetz-package.github.io/docs/basics/marks/#shortento "Direct link to shorten-to")

Which mark to shorten the path to when multiple marks are given. `auto` will
shorten to the last mark, `none` will shorten to the first mark (effectively
disabling path shortening). An integer can be given to select the mark's
index.

#### transform-shape:

[bool](https://typst.app/docs/reference/foundations/bool)

Default: `true` [​](https://cetz-package.github.io/docs/basics/marks/#transformshape "Direct link to transform-shape")

When `false` marks will not be stretched/affected by the current
transformation, marks will be placed after the path is transformed.

## Styling Draw Elements
[Skip to main content](https://cetz-package.github.io/docs/basics/styling/#__docusaurus_skipToContent_fallback)

You can style draw elements by passing the relevant named arguments to their draw functions. All elements that draw something have stroke and fill styling unless said otherwise.

#### fill:

[color](https://typst.app/docs/reference/visualize/color/) or [none](https://typst.app/docs/reference/foundations/none/)

Default: `none` [​](https://cetz-package.github.io/docs/basics/styling/#fill "Direct link to fill")

How to fill the drawn element.

#### stroke:

[none](https://typst.app/docs/reference/foundations/none/) or [auto](https://typst.app/docs/reference/foundations/auto/) or [length](https://typst.app/docs/reference/layout/length) or [color](https://typst.app/docs/reference/visualize/color/) or [dictionary](https://typst.app/docs/reference/foundations/dictionary) or [stroke](https://typst.app/docs/reference/visualize/stroke)

Default: `black` [​](https://cetz-package.github.io/docs/basics/styling/#stroke "Direct link to stroke")

How to stroke the border or the path of the draw element. [See Typst's line\\
documentation for more\\
details.](https://typst.app/docs/reference/visualize/line/#parameters-stroke)

#### fill-rule:

string

Default: `"non-zero"` [​](https://cetz-package.github.io/docs/basics/styling/#fillrule "Direct link to fill-rule")

How to fill self-intersecting paths. Can be "non-zero" or "even-odd".
[See Typst's path documentation for more details.](https://typst.app/docs/reference/visualize/path/#parameters-fill-rule)

```codeBlockLines_e6Vv
// Draws a red circle with a blue border
circle((0, 0), fill: red, stroke: blue)

// Draws a green line
line((0, 0), (1, 1), stroke: green)

```

![](<Base64-Image-Removed>)

Instead of having to specify the same styling for each time you want to draw an element, you can use the [`set-style`](https://cetz-package.github.io/docs/api/draw-functions/styling/set-style) function to change the style for all elements after it, like a Typst `set` rule. You can still pass styling to a draw function to override what has been set with `set-style`. You can also use the [`fill`](https://cetz-package.github.io/docs/api/draw-functions/styling/fill) and [`stroke`](https://cetz-package.github.io/docs/api/draw-functions/styling/stroke) functions as a shorthand to set the fill and stroke respectively.

```codeBlockLines_e6Vv
// Draws an empty square with a black border
rect((-1, -1), (1, 1))

// Sets the global style to have a fill of red and a stroke of blue
set-style(stroke: blue, fill: red)
circle((0,0))

// Draws a green line despite the global stroke being blue
line((), (1,1), stroke: green)

```

![](<Base64-Image-Removed>)

When using a dictionary for a style, it is important to note that they update each other instead of overriding the entire option like a non-dictionary value would. For example, if the stroke is set to `(paint: red, thickness: 5pt)` and you pass `(paint: blue)`, the stroke would become `(paint: blue, thickness: 5pt)`.

```codeBlockLines_e6Vv
// Sets the stroke to red with a thickness of 5pt
set-style(stroke: (paint: red, thickness: 5pt))

// Draws a line with the global stroke
line((0,0), (1,0))

// Draws a blue line with a thickness of 5pt because dictionaries update the style
line((0,0), (1,1), stroke: (paint: blue))

// Draws a yellow line with a thickness of 1pt because other values override the style
line((0,0), (0,1), stroke: yellow)

```

![](<Base64-Image-Removed>)

You can also specify styling for each type of element. Note that dictionary values will still update with its global value, the full hierarchy is `function > element type > global`. When the value of a style is [auto](https://typst.app/docs/reference/foundations/auto/), it will become exactly its parent style.

```codeBlockLines_e6Vv
set-style(
  // Global fill and stroke
  fill: green,
  stroke: (thickness: 5pt),
  // Stroke and fill for only rectangles
  rect: (stroke: (dash: "dashed"), fill: blue),
)
rect((0,0), (1,1))
circle((2.5, 0.5))
rect((4, 0), (5, 1), stroke: (thickness: 1pt))

```

![](<Base64-Image-Removed>)

## CeTZ New User Guide
[Skip to main content](https://cetz-package.github.io/docs/category/tutorials/#__docusaurus_skipToContent_fallback)

[**📄️ A Picture for Karl's New Students** \\
This tutorial is intended for new users of CeTZ. It does not give an exhaustive account of all the features of CeTZ, just of those you are likely to use right away. This tutorial also acts as a parallel to TikZ's tutorial A Picture for Karl's Students.](https://cetz-package.github.io/docs/tutorials/karl)

## CETZ Package Guide
[Skip to main content](https://cetz-package.github.io/docs/getting-started/#__docusaurus_skipToContent_fallback)

On this page

## Usage [​](https://cetz-package.github.io/docs/getting-started/\#usage "Direct link to Usage")

This is the minimal starting point in a `.typ` file:

```codeBlockLines_e6Vv
#import "@preview/cetz:0.3.4"
#cetz.canvas({
  import cetz.draw: *
  ...
})

```

Note that draw functions are imported inside the scope of the `canvas` block. This is recommended as some draw functions override Typst's functions such as `line`.

## Examples [​](https://cetz-package.github.io/docs/getting-started/\#examples "Direct link to Examples")

From this point on only the code inside the `canvas` block will be shown in examples unless specified otherwise.

```codeBlockLines_e6Vv
circle((0, 0))
line((0, 0), (2, 1))

```

![](<Base64-Image-Removed>)

- [Usage](https://cetz-package.github.io/docs/getting-started/#usage)
- [Examples](https://cetz-package.github.io/docs/getting-started/#examples)

## CeTZ Internals
[Skip to main content](https://cetz-package.github.io/docs/internals/#__docusaurus_skipToContent_fallback)

CeTZ is made up of several parts which can be daunting and complicated to figure out. Here we plan to detail how CeTZ actually works and explain the ideas.

This is not required reading for typical usage!

## CeTZ Drawing Libraries
[Skip to main content](https://cetz-package.github.io/docs/libraries/#__docusaurus_skipToContent_fallback)

CeTZ provides more specialised and focused functions in order to draw plots, charts, angles etc. They have been separated from the `draw` module into separate libraries for the sake of organisation and clarity.

We are planning to move them into their own packages. We don't know when but most likely once the current Typst package handling system gets improved.

## Data Plotting Library
[Skip to main content](https://cetz-package.github.io/docs/libraries/plot/#__docusaurus_skipToContent_fallback)

On this page

The plot library allows the plotting of data.

## Types [​](https://cetz-package.github.io/docs/libraries/plot/\#types "Direct link to Types")

The following types are commonly used by functions of this library

### domain [​](https://cetz-package.github.io/docs/libraries/plot/\#domain "Direct link to domain")

A tuple representing a mathematical function's domain as a closed interval. Example domains are `(0, 1)` for \[0,1\]\[0,1\]\[0,1\] or `(-calc.pi, calc.pi)` for \[−π,π\]\[-\\pi, \\pi\]\[−π,π\].

### axes [​](https://cetz-package.github.io/docs/libraries/plot/\#axes "Direct link to axes")

A tuple of axis names. Functions that take axes will use those axes as their `x` and `y` axis for plotting. To rotate a plot, you can simply swap its axes such as `("y", "x")`.

## Usage [​](https://cetz-package.github.io/docs/libraries/plot/\#usage "Direct link to Usage")

...

- [Types](https://cetz-package.github.io/docs/libraries/plot/#types)
  - [domain](https://cetz-package.github.io/docs/libraries/plot/#domain)
  - [axes](https://cetz-package.github.io/docs/libraries/plot/#axes)
- [Usage](https://cetz-package.github.io/docs/libraries/plot/#usage)

## Tree Library Guide
[Skip to main content](https://cetz-package.github.io/docs/libraries/tree/#__docusaurus_skipToContent_fallback)

On this page

The tree library allows the drawing of diagrams with simple tree layout algorithms.

## Nodes [​](https://cetz-package.github.io/docs/libraries/tree/\#nodes "Direct link to Nodes")

A tree node is an array consisting of the node's value at index 0 followed by its child nodes. For the default `draw-node` function, the value (the first item) of a node must be of type [content](https://typst.app/docs/reference/foundations/content).

Example of a list of nodes:

```codeBlockLines_e6Vv
cetz.tree.tree(
  (
    [A],
    (
      [B],
      (
        [C],
        ([D],)
      )
    )
  ),
  direction: "right"
)

```

![](<Base64-Image-Removed>)

Example of a tree of nodes:

```codeBlockLines_e6Vv
cetz.tree.tree(
  (
    [A],
    (
      [B],
      [C]
    ),
    (
      [D],
      [E]
    )
  ),
  direction: "right"
)

```

![](https://cetz-package.github.io/docs/assets/images/4858d8-9ea059346e0381f243926bba3740ecc8.svg)

## Drawing and Styling Tree Nodes [​](https://cetz-package.github.io/docs/libraries/tree/\#drawing-and-styling-tree-nodes "Direct link to Drawing and Styling Tree Nodes")

The `tree()` function takes an optional `draw-node:` and `draw-edge:` callback function that can be used to customice node and edge drawing.

The `draw-node` function must take the current node and its parents node anchor as arguments and return one or more elements.

For drawing edges between nodes, the `draw-edge` function must take two node anchors and the target node as arguments and return one or more elements.

```codeBlockLines_e6Vv
import cetz.tree
let data = ([\*], ([A], [A.A], [A.B]), ([B], [B.A]))
tree.tree(
  data,
  direction: "right",
  draw-node: (node, ..) => {
    circle((), radius: .35, fill: blue, stroke: none)
    content((), text(white, [#node.content]))
  },
  draw-edge: (from, to, ..) => {
    let (a, b) = (from + ".center", to + ".center")
    line((a, .4, b), (b, .4, a))
  }
)

```

![](https://cetz-package.github.io/docs/assets/images/7be38c-0d9a015752ae30cf4b82074481c62974.svg)

- [Nodes](https://cetz-package.github.io/docs/libraries/tree/#nodes)
- [Drawing and Styling Tree Nodes](https://cetz-package.github.io/docs/libraries/tree/#drawing-and-styling-tree-nodes)

## CeTZ Graphics Tutorial
[Skip to main content](https://cetz-package.github.io/docs/tutorials/karl/#__docusaurus_skipToContent_fallback)

On this page

This tutorial is intended for new users of CeTZ. It does not give an exhaustive account of all the features of CeTZ, just of those you are likely to use right away. This tutorial also acts as a parallel to Ti _k_ Z's tutorial [A Picture for Karl's Students](https://tikz.dev/tutorial).

Karl is a math and chemistry high-school teacher. He used to create the graphics in his worksheets and exams using the Ti _k_ Z package with LaTeX\\LaTeXLATE​X. While the results were acceptable, Karl, for his own reasons, has started using Typst instead. He looks through the provided packages in [Typst: Universe](https://typst.app/universe/) and finds CeTZ, which is supposed to stand for "CeTZ, ein Typst Zeichenpaket" and appears appropriate.

## Problem Statement [​](https://cetz-package.github.io/docs/tutorials/karl/\#problem-statement "Direct link to Problem Statement")

Karl wants to put a graphic on the next worksheet for his students. He is currently teaching his students about sine and cosine. He already has the graphic drawn with Ti _k_ Z and would like to keep it as close to it as possible:

```codeBlockLines_e6Vv
Either the example gets rendered using a block or we pre-render it I'm not sure yet.

```

## Setting up the Environment [​](https://cetz-package.github.io/docs/tutorials/karl/\#setting-up-the-environment "Direct link to Setting up the Environment")

In CeTZ, to draw a picture, two imports and a function call is all you need. Karl sets up his file as follows:

```codeBlockLines_e6Vv
#set page(width: auto, height: auto)
#import "@preview/cetz:0.3.4"

We are working on
#cetz.canvas({
  import cetz.draw: *
  line((-1.5, 0), (1.5, 0))
  line((0, -1.5), (0, 1.5))
})

```

When compiled via the Typst web app or the Typst command line interface, the resulting output will contain something that looks like this:

```codeBlockLines_e6Vv
We are working on
#cetz.canvas({
  import cetz.draw: *
  line((-1.5, 0), (1.5, 0))
  line((0, -1.5), (0, 1.5))
})

```

![](https://cetz-package.github.io/docs/assets/images/205214-5b73c9dc5cc34f7b4842bec8fae4c904.svg)

Admittedly, not quite the whole picture, yet, but we do have the axes established. Well, not quite, but we have the lines that make up the axes drawn. Karl suddenly has a sinking feeling that the picture is still some way off.

Let's have a more detailed look at the code. First, the package `cetz` is imported. The `canvas` function in the `cetz` module is then called and a pair of curly braces are placed as the function's first (and only) positional argument. The braces create a scope or body, in which more functions can be called, but first must be imported from the `draw` module.

Inside the body there are two `line` functions. They are draw functions that draw straight lines between given positions. The first `line` function is given the parameters `(-1.5, 0), (1.5, 0)`, which refer to a point at position (−1.5,0)(-1.5, 0)(−1.5,0) and (1.5,0)(1.5, 0)(1.5,0). Here, the positions are specified within a special coordinate system in which, initially, one unit is 1cm.

Karl is quite pleased to note that the environment automatically reserves enough space to encompass the picture.

## Line Construction [​](https://cetz-package.github.io/docs/tutorials/karl/\#line-construction "Direct link to Line Construction")

The basic building block of all pictures in CeTZ are draw functions. A draw function is a function that can be called inside the canvas body in order to create the graphic, such as `line`, `bezier`, `rect` and many more (not all draw functions _actually_ draw something, like `set-style`, but still effect the outcome of the picture).

In order to draw a path of straight lines, the `line` draw function can be used. You specify the coordinates of the start position by passing an array with two numbers (a [coordinate](https://cetz-package.github.io/docs/basics/custom-types#coordinate) type) to the first parameter of `line`. The second coordinate must be given as the second parameter of the function otherwise it will panic. Subsequent coordinates can be passed to the function to draw additional lines between the previous and next coordinates.

```codeBlockLines_e6Vv
line((-1.5, 0), (1.5, 0), (0, -1.5), (0, 1.5))

```

![](<Base64-Image-Removed>)

Note that the `canvas` function and import statements have been omitted from the code as they are boiler plate and don't always need to be shown. They are very much still required in order to produce the picture, so just remember they are there okay.

## Curve Construction [​](https://cetz-package.github.io/docs/tutorials/karl/\#curve-construction "Direct link to Curve Construction")

The next think Karl wants to do is to draw the circle. For this, straight lines obviously will not do. Instead, we need some way to draw curves. For this, CeTZ provides several other draw functions, the most useful here would be the `bezier` function. As the name suggests, it can draw a bezier curve when a start and end coordinate is given, as well as one or two control points.

Here is an example (the control points have been added for clarity):

```codeBlockLines_e6Vv
// start and end
circle((0, 0), radius: 2pt, fill: gray)
circle((2, 0), radius: 2pt, fill: gray)
// control points
circle((1, 1), radius: 2pt, fill: gray)
circle((2, 1), radius: 2pt, fill: gray)

bezier((0, 0), (2, 0), (1, 1), (2, 1))

```

![](<Base64-Image-Removed>)

So, Karl can now add the first half circle to the picture:

```codeBlockLines_e6Vv
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))

bezier((-1, 0), (0, 1), (-1, 0.555), (-0.555, 1))
bezier((0, 1), (1, 0), (0.555, 1), (1, 0.555))

```

![](<Base64-Image-Removed>)

Karl is happy with the result, but finds specifying circles in this way to be extremely awkward. Fortunately, there is a much simpler way.

## Circle Construction [​](https://cetz-package.github.io/docs/tutorials/karl/\#circle-construction "Direct link to Circle Construction")

In order to draw a circle, the `circle` draw function can be used:

```codeBlockLines_e6Vv
circle((0, 0), radius: 10pt)

```

![](<Base64-Image-Removed>)

You can also draw an ellipse with this draw function by passing an array of two numbers to the `radius` argument:

```codeBlockLines_e6Vv
circle((0, 0), radius: (20pt, 10pt))

```

![](<Base64-Image-Removed>)

To draw an ellipse whose axes are not horizontal and vertical, but point in an arbitrary direction you can use transformations, which are explained later.

So, returning to Karl's problem, he can write `circle((0, 0))` to draw the circle as, by default, the `radius` argument is `1`:

```codeBlockLines_e6Vv
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))

circle((0, 0))

```

![](<Base64-Image-Removed>)

At this point, Karl is a bit alarmed that the circle is so small when he wants the final picture to be much bigger. He is pleased to learn that CeTZ has transformation draw functions and scaling everything by a factor of three is very easy. But let us leave the size as it is for the moment to save some space.

## Rectangle Construction [​](https://cetz-package.github.io/docs/tutorials/karl/\#rectangle-construction "Direct link to Rectangle Construction")

The next things we would like to have is the grid in the background. There are several ways to produce it. For example, one might draw lots of rectangles. To do so, the `rect` draw function can be used. Two coordinates should be passed as arguments, they specify the corners of the rectangle:

```codeBlockLines_e6Vv
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))
circle((0, 0))

rect((0, 0), (0.5, 0.5))
rect((-0.5, -0.5), (-1, -1))

```

![](<Base64-Image-Removed>)

While this may be nice in other situations, this is not really leading anywhere with Karl's problem: First, we would need an awful lot of these rectangles and then there is the border that is not "closed".

So, Karl is about to resort to simply drawing four vertical and four horizontal lines using the nice `line` draw function, when he learns that there is a `grid` draw function.

## Grid Construction [​](https://cetz-package.github.io/docs/tutorials/karl/\#grid-construction "Direct link to Grid Construction")

The `grid` draw function adds a grid to the picture. It will add lines making up a grid that fills the rectangle specified by two coordinates passed to it.

For Karl, the following code could be used:

```codeBlockLines_e6Vv
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))
circle((0, 0))

grid((-1.5, -1.5), (1.5, 1.5), step: 0.5)

```

![](<Base64-Image-Removed>)

Having another look at his desired picture, karl notices that it would be nice for the grid to be more subdued. To subdue the grid, Karl adds more named arguments to the `grid` draw function. First, he uses the color `gray` for the grid lines. Second, he reduces the line width to `0.2pt` (Ti _k_ Z's `very thin`). Finally, he swaps the ordering of the commands so that the grid is drawn first and everything else on top.

```codeBlockLines_e6Vv
grid((-1.5, -1.5), (1.5, 1.5), step: 0.5, stroke: gray + 0.2pt)
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))
circle((0, 0))

```

![](<Base64-Image-Removed>)

## Adding a Touch of Style [​](https://cetz-package.github.io/docs/tutorials/karl/\#adding-a-touch-of-style "Direct link to Adding a Touch of Style")

Karl notices that the thickness of the circle and axes paths are much greater than the grid's thickness. He learns that CeTZ's default stroke thickness is actually `1pt` and not Ti _k_ Z's `0.4pt`. Karl decides that he would like to use the thinner lines to keep this new picture as close to the original as possible.

We can use the `set-style` draw function to apply styling to all subsequent draw functions, similar to how Typst's `set` and `show` rules work. To set the stroke's thickness he uses the named argument `stroke: 0.4pt`:

```codeBlockLines_e6Vv
set-style(stroke: 0.4pt)
grid((-1.5, -1.5), (1.5, 1.5), step: 0.5, stroke: gray + 0.2pt)
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))
circle((0, 0))

```

![](<Base64-Image-Removed>)

Karl can also move the grid's styling into the same `set-style` function by passing it as a dictionary to the `grid` named argument:

```codeBlockLines_e6Vv
set-style(
  stroke: 0.4pt,
  grid: (
    stroke: gray + 0.2pt,
    step: 0.5
  )
)
grid((-1.5, -1.5), (1.5, 1.5))
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))
circle((0, 0))

```

## Arc Construction [​](https://cetz-package.github.io/docs/tutorials/karl/\#arc-construction "Direct link to Arc Construction")

Our next obstacle is to draw the arc for the angle. For this, the `arc` draw function can be used, which draws part of a circle or ellipse. This function requires arguments to specify the arc. An example would be `arc((0, 0), start: 10deg, stop: 80deg, radius: 10pt)`, which creates an arc starting at (0,0)(0, 0)(0,0) at an angle of 10°10°10° to 80°80°80° with a radius of `10pt`. Karl obviously needs an arc from 0°0°0° to 30°30°30°. The radius should be something relatively small, perhaps around one third of the circle's radius.

```codeBlockLines_e6Vv
set-style(
  stroke: 0.4pt,
  grid: (
    stroke: gray + 0.2pt,
    step: 0.5
  )
)
grid((-1.5, -1.5), (1.5, 1.5))
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))
circle((0, 0))
arc((3mm, 0), start: 0deg, stop: 30deg, radius: 3mm)

```

![](<Base64-Image-Removed>)

Karl thinks this is really a bit small and he cannot continue unless he learns how to do scaling. For this, he can use the `scale` draw function at the start of the canvas body

```codeBlockLines_e6Vv
set-style(
  stroke: 0.4pt,
  grid: (
    stroke: gray + 0.2pt,
    step: 0.5
  )
)
scale(3)
grid((-1.5, -1.5), (1.5, 1.5))
line((-1.5, 0), (1.5, 0))
line((0, -1.5), (0, 1.5))
circle((0, 0))
arc((3mm, 0), start: 0deg, stop: 30deg, radius: 3mm)

```

![](<Base64-Image-Removed>)

As for circles, you can specify the radius as an array of two numbers to get an elliptical arc.

```codeBlockLines_e6Vv
arc((0, 0), start: 0deg, stop: 315deg, radius: (1.75, 1))

```

![](<Base64-Image-Removed>)

## Not Really Path Clipping [​](https://cetz-package.github.io/docs/tutorials/karl/\#not-really-path-clipping "Direct link to Not Really Path Clipping")

In order to save space in this manual, it would be nice to clip Karl's graphics a bit so we can focus on the "interesting" parts. Unfortunately clipping is not currently possible in CeTZ. So instead we can replace the circle with an arc and modify the grid.

```codeBlockLines_e6Vv
set-style(
  stroke: 0.4pt,
  grid: (
    stroke: gray + 0.2pt,
    step: 0.5
  )
)
scale(3)
grid((-0.5, -0.5), (1, 1))
line((-0.5, 0), (1, 0))
line((0, -0.5), (0, 1))
arc((0, 1), start: 90deg, delta: -120deg)
arc((3mm, 0), start: 0deg, stop: 30deg, radius: 3mm)

```

![](<Base64-Image-Removed>)

## Filling and Drawing [​](https://cetz-package.github.io/docs/tutorials/karl/\#filling-and-drawing "Direct link to Filling and Drawing")

Returning to the picture, Karl now wants the angle to be "filled" with a very light green. For this he uses the `fill` styling parameter. Here is what Karl does:

```codeBlockLines_e6Vv
set-style(
  stroke: 0.4pt,
  grid: (
    stroke: gray + 0.2pt,
    step: 0.5
  )
)
scale(3)
grid((-0.5, -0.5), (1, 1))
line((-0.5, 0), (1, 0))
line((0, -0.5), (0, 1))
arc((0, 1), start: 90deg, delta: -120deg)
arc(
  (3mm, 0),
  start: 0deg,
  stop: 30deg,
  radius: 3mm,
  mode: "PIE",
  fill: color.mix((green, 20%), white),
)

```

![](<Base64-Image-Removed>)

The color `color.mix((green, 20%), white)` means 20% green and 80% white mixed together. In fact `fill` can take any value of type [color](https://typst.app/docs/reference/visualize/color/), you can even do shading!

By default arcs are in "OPEN" mode where only the curve is drawn and only the chord of the arc will be filled. By using `mode: "PIE"` the arc will be closed around its origin leaving you with a shape akin to a slice of pie, or in this case an angle which can be properly filled.

## Specifying Coordinates [​](https://cetz-package.github.io/docs/tutorials/karl/\#specifying-coordinates "Direct link to Specifying Coordinates")

Karl now wants to add the sine and cosine lines. He knows already that he can use the `stroke:` styling parameter to set the lines' colors. So, what is the best way to specify the coordinates?

There are different ways of specifying coordinates. The easiest way is to say something like `(10pt, 2cm)`. This means 10pt in xxx-direction and 2cm in yyy-directions. Alternatively, you can also leave out the units as in `(1, 2)`, which means "one times the unit length in the xxx-direction and twice the unit length in the yyy-direction". The unit length defaults to 1cm in both directions.

In order to specify points in polar coordinates, use an [array](https://typst.app/docs/reference/foundations/array) of the form `(30deg, 1cm)`, which means 1cm in direction 30 degree. This is obviously quite useful to "get to the point (cos⁡30°,sin⁡30°)(\\cos 30\\degree, \\sin 30 \\degree)(cos30°,sin30°) on the circle".

You can wrap a coordinate in a [dictionary](https://typst.app/docs/reference/foundations/dictionary) with the key `rel` as in `(rel: (0cm, 1cm))`. Such coordinates are interpreted differently: They mean "1cm upwards from the previous specified position, making this the new specified position". You can include the key and value `update: false` in the coordinate `(rel: (2cm, 0cm), update: false)` which means "2cm to the right of the previous specified position and do not change the previous position". For example, we an draw the sine line as follows:

```codeBlockLines_e6Vv
set-style(
  stroke: 0.4pt,
  grid: (
    stroke: gray + 0.2pt,
    step: 0.5
  )
)
scale(3)
grid((-0.5, -0.5), (1, 1))
line((-0.5, 0), (1, 0))
line((0, -0.5), (0, 1))
arc((0, 1), start: 90deg, delta: -120deg)
arc(
  (3mm, 0),
  start: 0deg,
  stop: 30deg,
  radius: 3mm,
  mode: "PIE",
  fill: color.mix((green, 20%), white),
)
line((30deg, 1cm), (rel: (0, -0.5)), stroke: red + 1.2pt)

```

![](<Base64-Image-Removed>)

Karl used the fact sin⁡30°=1/2\\sin 30 \\degree = 1/2sin30°=1/2. However, he very much doubts that his students know this, so it would be nice to have a way of specifying "the point straight down from `(30deg, 1cm)` that lies on the xxx-axis". This is, indeed, possible using a special coordinate: Karl can write `((30deg, 1cm), "|-", (0, 0))`. In general, the meaning of `(p, "|-", q)` is "the intersection of a vertical line through ppp and a horizontal line through qqq".

Next, let us draw the cosine line. One way would be to use `line(((30deg, 1cm), "|-", (0, 0)), (0, 0))`. Another way is the following: we "continue" from where the sine ends:

```codeBlockLines_e6Vv
set-style(
  stroke: 0.4pt,
  grid: (
    stroke: gray + 0.2pt,
    step: 0.5
  )
)
scale(3)
grid((-0.5, -0.5), (1, 1))
line((-0.5, 0), (1, 0))
line((0, -0.5), (0, 1))
arc((0, 1), start: 90deg, delta: -120deg)
arc(
  (3mm, 0),
  start: 0deg,
  stop: 30deg,
  radius: 3mm,
  mode: "PIE",
  fill: color.mix((green, 20%), white),
)
line((30deg, 1cm), (rel: (0, -0.5)), stroke: red + 1.2pt)
line((), (0, 0), stroke: blue + 1.2pt)

```

![](<Base64-Image-Removed>)

Note that an empty array `()` is given as the line's starting coordinate. This value means "the previous specified coordinate", which in this case is the end of the cosine line.

## Intersecting Paths [​](https://cetz-package.github.io/docs/tutorials/karl/\#intersecting-paths "Direct link to Intersecting Paths")

Karl is left with the line for tan⁡α\\tan \\alphatanα, which seems difficult to specify using transformations and polar coordinates. The first - and easiest - thing he can do is so simply use the coordinate `(1, calc.tan(30deg))`.

Karl can, however, also use a more elaborate, but also more "geometric" way of computing the length of the orange line: He can specify intersections of paths as coordinates. The line for tan⁡α\\tan \\alphatanα starts at (1,0)(1, 0)(1,0) and goes upward to a point that is at the intersection of a line going "up" and a line going from the origin through `(30deg, 1cm)`. Such computations are made available by the `intersections` function.

What Karl must do is to create two "invisible" paths that intersect at the position of interest. Creating lines that are not otherwise seen can be done by either setting their stroke to [none](https://typst.app/docs/reference/foundations/none/) or by wrapping them in the `hide` function. Then, Karl can add the `name` parameter to the lines for later reference. Once the lines have been constructed, Karl can use the `intersections` function to get the coordinate for later reference.

```codeBlockLines_e6Vv
hide({
  line((1, 0), (1, 1), name: "upward line")
  line((0, 0), (30deg, 1.5cm), name: "sloped line") // a bit longer, so that there is an intersection
})

intersections("x", "upward line", "sloped line")
line((1, 0), "x.0", stroke: orange + 1.2pt)

```

## Adding Marks [​](https://cetz-package.github.io/docs/tutorials/karl/\#adding-marks "Direct link to Adding Marks")

Karl now wants to add the little arrow tips at the end of the axes. He has noticed that in many plots, even in scientific journals, these arrow tips seem to be missing, presumably because the generating programs cannot produce them. Karl thinks arrow tips belong at the end of axes. His son agrees. His students do not care about arrow tips.

It turns out that adding arrow tips is pretty easy: Karl adds the `mark` styling parameter with the value `(end: ">")` to the line functions for the axes:

```codeBlockLines_e6Vv
set-style(
  stroke: 0.4pt,
  grid: (
    stroke: gray + 0.2pt,
    step: 0.5
  )
)
scale(3)
grid((-0.5, -0.5), (1.5, 1.5))
line((-0.5, 0), (1.5, 0), mark: (end: ">"))
line((0, -0.5), (0, 1.5), mark: (end: ">"))
arc((0, 0), start: 120deg, stop: -30deg, anchor: "origin")
arc(
  (3mm, 0),
  start: 0deg,
  stop: 30deg,
  radius: 3mm,
  mode: "PIE",
  fill: color.mix((green, 20%), white),
)
line((30deg, 1cm), (rel: (0, -0.5)), stroke: red + 1.2pt)
line((), (0, 0), stroke: blue + 1.2pt)

hide({
  line((1, 0), (1, 1), name: "upward line")
  line((0, 0), (30deg, 1.5cm), name: "sloped line")
})
intersections("x", "upward line", "sloped line")
line((1, 0), "x.0", stroke: orange + 1.2pt)

```

![](<Base64-Image-Removed>)

If Karl had used the value `(start: ">")` instead of `(end: ">")`, arrow tips would have been put at the beginning of the path. The value `(start: ">", end: ">")` or `(symbol: ">")` puts the marks at both ends of the path.

Some elements do not support marks. As a rule of thumb, you can add marks only to elements that do not have a closed path.

Karl notices that the marks are unnaturally large, this is because the shape of marks are transformed by default. So the marks are three times as big. This can be resolved by setting the `transform-shape: false` styling parameter. He also wants the mark to be filled and to have a different shape. As done earlier, the `fill` styling parameter can be used to fill marks and a different shape can be obtained by referring to the table of currently [supported marks](https://cetz-package.github.io/docs/tutorials/basics/marks).

## Repeating Things: For-Loops [​](https://cetz-package.github.io/docs/tutorials/karl/\#repeating-things-for-loops "Direct link to Repeating Things: For-Loops")

Karl's next aim is to add little ticks on the axes at positions −1-1−1, −1/2-1/2−1/2, 1/21/21/2, and 111. For this, it would be nice to use some kind of "loop", especially since he wishes to do the same thing at each of these positions. Thankfully Typst [has built in loops](https://typst.app/docs/reference/scripting/#loops).

Karl can then use the following code:

```codeBlockLines_e6Vv
set-style(
  stroke: 0.4pt,
  grid: (
    stroke: gray + 0.2pt,
    step: 0.5
  ),
  mark: (
    transform-shape: false,
    fill: black
  )
)
scale(3)
grid((-1, -1), (1.5, 1.5))
line((-1, 0), (1.5, 0), mark: (end: "stealth"))
line((0, -1), (0, 1.5), mark: (end: "stealth"))
circle((0, 0))
arc(
  (3mm, 0),
  start: 0deg,
  stop: 30deg,
  radius: 3mm,
  mode: "PIE",
  fill: color.mix((green, 20%), white),
)

for x in (-1, -0.5, 1) {
  line((x, -1pt), (x, 1pt))
}
for y in (-1, -0.5, 0.5, 1) {
  line((-1pt, y), (1pt, y))
}

```

![](<Base64-Image-Removed>)

## Adding Text [​](https://cetz-package.github.io/docs/tutorials/karl/\#adding-text "Direct link to Adding Text")

Karl is, by now, quite satisfied with the picture. However, the most important parts, namely the labels, are still missing!

CeTZ has the `content` draw function which allows you to place any content onto the canvas at a specified position.

- [Problem Statement](https://cetz-package.github.io/docs/tutorials/karl/#problem-statement)
- [Setting up the Environment](https://cetz-package.github.io/docs/tutorials/karl/#setting-up-the-environment)
- [Line Construction](https://cetz-package.github.io/docs/tutorials/karl/#line-construction)
- [Curve Construction](https://cetz-package.github.io/docs/tutorials/karl/#curve-construction)
- [Circle Construction](https://cetz-package.github.io/docs/tutorials/karl/#circle-construction)
- [Rectangle Construction](https://cetz-package.github.io/docs/tutorials/karl/#rectangle-construction)
- [Grid Construction](https://cetz-package.github.io/docs/tutorials/karl/#grid-construction)
- [Adding a Touch of Style](https://cetz-package.github.io/docs/tutorials/karl/#adding-a-touch-of-style)
- [Arc Construction](https://cetz-package.github.io/docs/tutorials/karl/#arc-construction)
- [Not Really Path Clipping](https://cetz-package.github.io/docs/tutorials/karl/#not-really-path-clipping)
- [Filling and Drawing](https://cetz-package.github.io/docs/tutorials/karl/#filling-and-drawing)
- [Specifying Coordinates](https://cetz-package.github.io/docs/tutorials/karl/#specifying-coordinates)
- [Intersecting Paths](https://cetz-package.github.io/docs/tutorials/karl/#intersecting-paths)
- [Adding Marks](https://cetz-package.github.io/docs/tutorials/karl/#adding-marks)
- [Repeating Things: For-Loops](https://cetz-package.github.io/docs/tutorials/karl/#repeating-things-for-loops)
- [Adding Text](https://cetz-package.github.io/docs/tutorials/karl/#adding-text)

