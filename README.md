# L.Control.Overview
Provides an overview map that responds to base layer changes.

## Layer setup
The same layer instance cannot be used in the main map and the overview at the same
time, so separate layers must be created. Because there are multiple layers of the same 
type involved, each layer must contain a 'name' attribute so the control can keep the
two maps in sync with each during base layer changes.

## License
L.Control.Overview is free software, and may be redistributed under the MIT-LICENSE.
