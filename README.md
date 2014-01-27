Using Playstation DualShock 3 or DualShock 4 in ImpactJS
===========================================================

Use Sony Playstation DualShock 3 or DualShock 4 Wireless Controller in your ImpactJS game on your web browser. The plugin maps the buttons of the DS3 or DS4 with the keyboard.

*Compatibilities: Google Chrome 21+, Mozilla Firefox 24+*

Usage
-----
Copy **gamepad-dualshock.js** to your **lib/plugins/** directory.

Edit **lib/game/main.js** :
```
ig.module( 
	'game.main'
)
.requires(
	//... ,
	'plugins.gamepad-dualshock',
	// ...
)
.defines(function(){

	MyGame = ig.Game.extend({
		// ...
		gamepad: new ig.GamepadDualshock(),
		// ...
		init: function() {
			// ...
			ig.input.bind( ig.KEY.LEFT_ARROW, 'left' );
			ig.input.bind( ig.KEY.RIGHT_ARROW, 'right' );
			ig.input.bind( ig.KEY.UP_ARROW, 'jump' );
		
			this.gamepad
				.mapping( ig.DUALSHOCK_KEY.LEFT		, ig.KEY.LEFT_ARROW )
				.mapping( ig.DUALSHOCK_KEY.LS_LEFT	, ig.KEY.LEFT_ARROW )
				.mapping( ig.DUALSHOCK_KEY.RIGHT	, ig.KEY.RIGHT_ARROW )
				.mapping( ig.DUALSHOCK_KEY.LS_RIGHT	, ig.KEY.RIGHT_ARROW )
				.mapping( ig.DUALSHOCK_KEY.CROSS	, ig.KEY.UP_ARROW )
				;
			// ...
		},
		update: function() {
			this.gamepad.update();
		
			// ...
			this.parent();
		},
		// ...
	});
});
```

Documentation
-------------
* https://developer.mozilla.org/en-US/docs/Web/Guide/API/Gamepad
* http://luser.github.io/gamepadtest/

Note: As of Firefox 24, the Gamepad API is available behind a preference. You can enable it by loading **about:config** and setting the **dom.gamepad.enabled** preference to **true**.

