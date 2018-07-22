# Gunsen

Gunsen is a framework for writing your own Sensu plugins in Go.

## Check Plugin

Start writing your own check plugin by importing Gunsen:

```
package main

import "github.com/sensu-go-plugins/gunsen/plugin"

// MyCheck represents our check plugin
type MyCheck struct {
	cmd plugin.Command
}

func main() {
	// Initialize our check
	c := &MyCheck{
		cmd: plugin.NewCommand("MyCheck"),
	}

	// Execute the check
	plugin.Execute(c)
}

// Command returns the plugin command
func (c *MyCheck) Command() plugin.Command {
	return c.cmd
}

// Run executes the plugin
func (c *MyCheck) Run() error {
	return &plugin.Exit{Msg: "Success", Status: plugin.OK}
}
```