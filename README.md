### reusableComponents
###### Angular directives for UI components
***

### Table of Contents
* [Motivation](#motivation)
* [Components](#components)
* [Design Paradigm](#design-paradigm)
* [Usage](#usage)
* [Install](#install)
* [License](#license)

### <a name="motivation"></a>Motivation
reusableComponents is an AngularJS module containing directives for UI components. It relies on the directives of the [reusableBehaviors](https://github.com/Sranderley/reusableBehaviors) module. These directives contain light, configurable interface elements which can be restyled.

### <a name="components"></a>Components
* Checkbox - Exactly what you'd expect
* Toggle - A slider toggle

### <a name="design-paradigm"></a>Design Paradigm
* Directives are named in the typical angular fashion, beginning with a two-character mnemonic, followed by a single word which is descriptive of the behavior that the directive provides. (e.g. rc-checkbox, rc-toggle)
* Each directive exposes its API to the DOM using an attribute called [behavior]-api. (e.g. toggle-api, relay-api)
* APIs include both properties and methods, see the [demo page](https://sranderley.github.io) to view the directives along with their markup
* Some of the directives rely on additional attributes for configuration, see the [demo page](https://sranderley.github.io) for more details
* Some directives depend on services, please just go to the [demo page](https://sranderley.github.io) already

### <a name="usage"></a>Usage
These directives are meant for use with the ng-class directive and a strong knowledge of CSS and CSS transitions. They can be used to provide behaviors to standalone elements, or they can be invoked inside of other directives with styles already applied, providing behavior to the contents of the container directive.

####Example

This is the source code for the rb-toggle directive.
````javascript
angular
	.module('reusableBehaviors')
	.directive('rbToggle', rbToggle);

function rbToggle(){
	return {
		restrict: 'A',
		scope: {
			toggleApi: '='
		},
		link: function(scope, elem, attr){
			scope.toggleApi = {
				active: false,
				toggle: toggle
			};

			function toggle(){
				scope.toggleApi.active = !scope.toggleApi.active;
			}
		}
	}
}
````
And this is an example of the rb-toggle directive being used in the DOM
````HTML
<button
	rb-toggle
	toggle-api="window"
	ng-click="window.toggle()"
>
	Click me to open the window!
</button>

<div
	class="window"
	ng-class="{
		closed: !window.active,
		open: window.active
	}"
>
	<div>The Great Outdoors</div>
</div>
````
In this example, the directive is instantiated on the button and its API is defined as "window". This API is then used by the `<button>` element, which invokes the directive's toggle method whenever it is clicked. The result of invoking the toggle method is that the boolean `window.active` changes its state.

The following CSS applies a transition whenever `window.toggle` is invoked.
````CSS
.window {
	width: 100%
	background-color: #B4D455
	transition: height 0.1s
}

.window.closed {
	height: 0;
}

.window.open {
	height: 100%
}
````

### <a name="install"></a>Install
Installation is very simple.
* Include rb.js or rb.min.js file in your project directory
* Inside of your index.html, include a `<script>` tag which points to rb.js or rb.min.js
* In the declarration of your angular app, pass 'reusable-behaviors' as a dependency, like:
````javascript
angular.module('myApp', ['reusable-behaviors']);
````

### <a name="license"></a>License
MIT License can be viewed [here](/LICENSE)