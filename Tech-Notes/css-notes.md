# CSS Notes

## Element sizing
	- rem *best for responsive websites
		- size relative to the root element (generally HTML font size)

	- em
		- size relative to the parent element

	- vh - viewport height
		- screen/viewport is split into 100 slices vertically
		- vh size uses the 100 slices to size things

	- vw - viewport width
		- screen/viewport is split into 100 slices horizontally
		- vw size uses the 100 slices to size things

## Selectors
	- insert content before or after content
		- :before
			- Ex: .spinner:before {content="", ...}
		- :after
