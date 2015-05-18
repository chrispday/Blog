my-element.html

	<link rel="import" href="../bower_components/polymer/polymer.html">
	<dom-module id="my-element">
	  <template>
		<content></content>
		<span style$="{{thecolor}}">Hello <i>{{xyzcolor}}</i> from <b>my-element</b>. This is my Shadow DOM</span>
		<p>The owner is <b>{{owner}}</b></p>
		<p><input type="text" value="{{owner::input}}" /></p>
		<p><input type="text" value="{{thecolor::input}}" /></p>
	  </template>
	</dom-module>
	<script>
	Polymer({
		is: "my-element",
		properties: {
			xyzcolor: {
				type: String,
				value: "red",
				notify: true
			},
			thecolor: {
				type: String,
				value: "color:red;",
				notify: true
			}
		}
	});
	</script>

my-element2.html

	<link rel="import" href="../bower_components/polymer/polymer.html">
	<dom-module id="my-element2">
	  <template>
	    <span><span>{{something.hello}}</span> from <span>{{something.world}}</span> <b>my-element2</b>. This is my Shadow DOM</span>
	  </template>
	</dom-module>
	<script>
	Polymer({
		is: "my-element2",
		properties: {
			something: {
				type:Object,
				value: {"hello": "oldhello", "world":"oldworld"}
			}
		},
		somethingChanged: function (newValue, oldValue) {
			alert(newValue);
		}
	});
	</script>

my-element3.html

	<link rel="import" href="../bower_components/polymer/polymer.html">
	<dom-module id="my-element3">
	  <template>
		<span>{{mycustomattr}}</span>
		<span>{{othercustomattr}}</span>
	  </template>
	</dom-module>
	<script>
	Polymer({
		is: "my-element3",
		properties: {
			mycustomattr: {
				type: String,
				notify: true
			},
			othercustomattr: {
				type: String,
				notify: true,
				value: "something"
			}
		}
	});
	</script>

index.html

	<!DOCTYPE html>
	<html ng-app>
	    <head>
			<script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>
			<link rel="import" href="elements/my-element.html">
			<link rel="import" href="elements/my-element2.html">
			<link rel="import" href="elements/my-element3.html">
			<script src="https://code.jquery.com/jquery-1.11.3.js"></script>
			<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.15/angular.min.js"></script>
	    </head>
	    <body>
			<input type="text" ng-model="yourName" placeholder="Enter a name here"><hr/>
			<my-element>
				{{yourName}}
				<p>some content</p>
				<p><my-element2 something='{ "hello": "newhello", "world": "newworld" }' /></p>
			</my-element>
			<my-element3 mycustomattr="{{yourName}}"></my-element3>
			<input id="clickme" type="button" value="Click Me"></input>
			<div style="display:flex;width:800px;margin:0 auto;">
				<div style="flex-grow:1;background-color:red;">One<br/>One</div>
				<div style="flex-grow:2;background-color:green;">Two</div>
				<div style="flex-grow:1;background-color:blue;">Three</div>
			</div>
			<script>
				/// <reference path="typings/tsd.d.ts"/>
				$("#clickme").click(function() {
					$("my-element2")[0].something = { "hello": "proghello", "world": "progworld" };
				});
			</script>
		</body>
	</html>
