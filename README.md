# Wordpress Custom Post Model

A eloquent class that helps you to create new data models using wordpress custom post types. Benefits of using this class

* You make custom wordpress plugins using wordpress post table. You mostly don't need to create new tables. This is wordpress recommendation. Whenever you need a new entity start thinking of a new custom post type. It can be a car, an account, a date, etc.
* Wordpress post table has indices on several fields which are good enough for most common searches.
* This class does the basic operations and field mappings quite easy. You can setup your custom post ORM in a few minutes. 
* This class handles dynamic properties well. You can save properties *WITHOUT* even defining them! Feels like a schema-less table.

## minimal Example

### Extend the class

Required properties

1. const POST_TYPE

Model does all the queries and manipulation based on your post-type. So, to start using the model, all you need to do is define a single constant (**POST_TYPE**) in your class and extend the Model class like this

```PHP

require_once "path-to/class-adhocmaster-model.php";

// Your custom class
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

### Usage

Now you can use your new class like this anywhere.

#### Creating & storing a new item

```PHP

$obj = new Crowd_Fundraiser_Campaign();

// A Dynamic property which will be saved as post meta data
$obj->my_new_property = "Hello World"; 

// A wordpress post table field. Will be save in the post table
$obj->post_author = get_current_user_id();

// Saving the whole form data as a serialized array! Never do it like this, we will need to sanitize data and clear up a bit
$obj->post_content = serialize($_POST);

// Now just save
$obj->save();

```

#### Retriving item

When you retrive an item, it pulls all the data from post table and also meta table. So, you get all the properties of your custom post type in a single object. Just access them as object properties.

```PHP

$obj = new Crowd_Fundraiser_Campaign( $post_id );

echo $obj->my_new_property; // outputs data saved in "my_new_property" meta 
echo $obj->post_author;     // outputs data saved in post_author field in post table

````

## Advanced Example

## Contribution Needed

This Wordpress ORM class needs a lot of contribution. Interested people just start a issue thread with discussion as I fail to check emails. Several aspect I am looking for

1. Search and Get functions
2. **Enttity relation mappings** ( like say one type has multiple other types )
3. Data export
4. Data and relation visualization (core wordpress management tools are not enough)



