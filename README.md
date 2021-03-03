# webgl
[![GoDoc](https://godoc.org/github.com/gopherjs/webgl?status.svg)](https://godoc.org/github.com/gopherjs/webgl)
[![Go Report Card](https://goreportcard.com/badge/github.com/n2d/webgl)](https://goreportcard.com/report/github.com/n2d/webgl)

change from https://godoc.org/github.com/gopherjs/webgl support "syscall/js"

## Example

![Screenshot](https://cloud.githubusercontent.com/assets/1924134/3566022/5d81f2d0-0ae0-11e4-82e4-3cb33b83d8d3.png)

webgl_example.go:

```Go
package main

import (
	"syscall/js"
	"github.com/gopherjs/webgl"
)

func main() {
	var canvas js.Value = js.
		Global().
		Get("document").
		Call("getElementById", "canvas")


	canvas.Set("height", 600)
	canvas.Set("width", 800)

	gl, _ := webgl.NewContext(canvas)

	gl.ClearColor(1, 0, 0, 1)
	gl.Clear(gl.COLOR_BUFFER_BIT)
}
```

webgl_example.html:

```html
<html><body><script src="webgl_example.js"></script><canvas id='canvas'></canvas></br></body></html>
```

To produce `webgl_example.js` file, run `gopherjs build webgl_example.go`.
