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
reusableComponents is an AngularJS module containing directives for light, configurable UI components which can be restyled. It relies on the directives of the [reusableBehaviors](https://github.com/Sranderley/reusableBehaviors) module.

### <a name="components"></a>Components
* Checkbox - Exactly what you'd expect
* Toggle - A slider toggle

### <a name="design-paradigm"></a>Design Paradigm
* Directives are named in the typical angular fashion, beginning with a two-character mnemonic, followed by a single word which is descriptive of the behavior that the directive provides. (e.g. rc-checkbox, rc-toggle)
* Some of the directives rely on attributes for configuration, see the [demos page](https://sranderley.github.io) for more details
* Some directives depend on services, check out the [demos page](https://sranderley.github.io) for more info

### <a name="usage"></a>Usage
These directives are meant for use with the ng-class directive and a strong knowledge of CSS and CSS transitions. They can be used to provide behaviors to standalone elements, or they can be invoked inside of other directives with styles already applied, providing behavior to the contents of the container directive.

####Example

This is the source code for the rc-toggle directive.
````javascript

````
And this is an example of the rc-toggle directive being used in the DOM
````HTML

````
In this example, the directive is instantiated on the button and its API is defined as "window". This API is then used by the `<button>` element, which invokes the directive's toggle method whenever it is clicked. The result of invoking the toggle method is that the boolean `window.active` changes its state.

The following CSS applies a transition whenever `window.toggle` is invoked.
````CSS

````

### <a name="install"></a>Install
Installation is very simple.
* Include rc.js or rc.min.js file in your project directory
* Inside of your index.html, include a `<script>` tag which points to rc.js or rc.min.js
* In the declarration of your angular app, pass 'reusable-components' as a dependency, like:
````javascript
angular.module('myApp', ['reusable-components']);
````

### <a name="license"></a>License
MIT License can be viewed [here](/LICENSE)