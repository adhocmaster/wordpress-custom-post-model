# wordpress-custom-post-model
A eloquent class that helps you to create new data models using wordpress custom post types

# minimal Example

## Required properties

1. const POST_TYPE

All you need to do is define a single constant (**POST_TYPE**) in your class and extend the Model class like this

```PHP

class Crowd_Fundraiser_Campaign extends Adhocmaster_Model {


	/**
	 * id of the custom post type
	 *
	 * @since    1.0.0
	 * @access   public
	 */

	const POST_TYPE = "campaign";

}

```

Now you can use your new class like this


