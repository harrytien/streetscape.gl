# XVIZMetricComponent (React Component)

The base component for rendering a Declarative UI
[metric](https://github.com/uber/xviz/blob/master/docs/protocol-schema/declarative-ui.md#metric)
component.

> Do not use this component directly unless implementing your own UI component. See
> [XVIZPanel](/docs/api-reference/xviz-panel) for how to render generic Declarative UI
> configurations.

## Properties

### UI Configuration

##### width (Number|String, optional)

The width of the chart. Default `100%`.

##### height (Number|String, optional)

The height of the chart. Default `160`.

##### margin (Object, optional)

The margin of the chart in pixles, must have the following fields:

- `left`
- `right`
- `top`
- `bottom`

Default: `{left: 45, right: 10, top: 10, bottom: 20}`

##### getColor (Object|Function|String, optional)

The color accessor of a the line/area series.

- Type `string`: a CSS color string.
- Type `object`: a map from stream name to its CSS color.
- Type `function`: a callback that receives a stream name and returns its CSS color.

##### xTicks (Number, optional)

Number of ticks to show on the x axis. Default `0`.

##### yTicks (Number, optional)

Number of ticks to show on the y axis. Default `3`.

##### formatXTick (Function, optional)

Format the label along the x axis.

Default: `x => String(x)``

##### formatYTick (Function, optional)

Format the label along the y axis.

Default: `y => String(y)``

##### horizontalGridLines (Number, optional)

Number of horizontal grid lines. Default `3`.

##### verticalGridLines (Number, optional)

Number of vertical grid lines. Default `0`.

##### onClick (Function, optional)

Called when the chart is clicked.

Parameters:

- `x` (number) - x value at the pointer position.

### Declarative UI Component Descriptor

The following props are automatically populated when this component is rendered via `XVIZPanel`. See
Declarative UI specification for details.

##### streams (Array)

##### title (String)

##### description (String)

### Log Info

The following props are automatically populated when this component is rendered via `XVIZPanel`.
Supply these props manually if the component is used without a `XVIZLoader` instance, e.g. connected
with a Redux store.

##### currentTime (Number)

The current playback position of the log.

##### timeSeries (Number)

An object mapping from stream names to objects in the following shape:

- `data` (Array) - list of objects to be rendered as a time series
- `getX` (Function) - accessor of x value from each item in `data`
- `getY` (Function) - accessor of y value from each item in `data`
- `unit` (String) - unit of the metric

##### timeDomain (Array)

Domain of the x axis in the shape of `[startTime, endTime]`.