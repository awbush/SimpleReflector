SimpleReflector is an easy-to-use reflection class for exposing an object's identity so problems can be debugged quickly.

It does correct null/true/false/empty string detection.  A string just gets output directly, whereas objects will have their class interfaces exposed. Everything dumped to screen is correctly escaped for HTML output so the rest of the page doesn't break.

The following information is displayed for objects:

- Class file/line location (especially useful when the same name class is defined multiple times in the filesystem)
- Methods in the class, including parameter names.
- Contents of the object (simple print_r that is HTML escaped)

Example Usage:

	// echo info to screen
	SimpleReflector::jam($object);
	
	// returns info as a string
	$str = SimpleReflector::jam($object, true);
	
	// echo info to screen with a custom title instead of "SimpleReflector"
	SimpleReflector::jam($object, false, 'mysterious object');

For quicker use, consider adding a short function to your applications:

	function jam() { $args = func_get_args(); call_user_func_array(array('SimpleReflector', 'jam'), $args); }

Then instead of typing `SimpleReflector::jam(...)` you can just type `jam(...)`.
