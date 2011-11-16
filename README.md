This is a Codeigniter wrapper around the Shopify PHP API

**This is till a work in progress, and is FAR from complete! DO NOT USE THIS TILL IT'S DONE!**

Usage
======================

1. Register an application
2. Set the return URL to a controller function (something like 'shop/authenticate')
3. Copy 'shopify_api.php' and 'cishopify.php' to application/libraries
4. Set up the following authenticate() function (or whatever function name you used in step 2)

		function authenticate()
		{
			if($this->input->get('shop') && $this->input->get('t'))
			{
				$shop = $this->input->get('shop',TRUE);
				$token = $this->input->get('t',TRUE);
				$this->cishopify->setapi($shop, $token);	
			}
		}
5. Open up the cishopify.php library file, and set the constants at the top
6. Visit the authenticate url (either 'shop/authenticate', or whatever else you used), and grant permissions to the app
7. Look at the examples below to see what you can do

Reference
======================

## $this->cishopify->getProducts($collection_id = 0, $params = array(), $cache = false)
##### *Description*

Gets an array of products, optionally belonging to a particular collection

##### *Parameters*

*$collection_id*: If specified, will only return products that belong to that collection

*$params*: A key/value array of additional parameters as described below

	limit — Amount of results (default: 50) (maximum: 250)
	page — Page to show (default: 1)
	since_id — Restrict results to after the specified ID
	vendor — Filter by product vendor
	handle — Filter by product handle
	product_type — Filter by product type
	created_at_min — Show products created after date (format: 2008-01-01 03:00)
	created_at_max — Show products created before date (format: 2008-01-01 03:00)
	updated_at_min — Show products last updated after date (format: 2008-01-01 03:00)
	updated_at_max — Show products last updated before date (format: 2008-01-01 03:00)
	published_at_min — Show products published after date (format: 2008-01-01 03:00)
	published_at_max — Show products published before date (format: 2008-01-01 03:00)
	published_status
		published - Show only published products
		unpublished - Show only unpublished products
		any - Show all products (default)
	fields — comma-separated list of fields to include in the response
	
*$cache*: Specifies whether the products should be loaded from cache or fetched fresh from the server. Defaults to false.

##### *Return Value*

*Array*: containing products returned which match the specified criteria

##### *Example*

Fetch up to 5 products in the collection 5531852, where the product type is set to "socks";

<pre>
$this->cishopify->getProducts('5531852',array('limit'=>'5','product_type'=>'socks'));
</pre>

## $this->cishopify->getProduct($product_id, $cache = false)
##### *Description*

Fetches a product by ID

##### *Parameters*

*$product_id*: ID of the product being fetched
	
*$cache*: Specifies whether the product should be loaded from cache or fetched fresh from the server. Defaults to false.

##### *Return Value*

*Array*: Contains the returned product

##### *Example*

Fetch product with id "112345"

<pre>
$this->cishopify->getProduct('112345');
</pre>


Dependencies
======================

This uses the [official shopify PHP API](https://github.com/Shopify/shopify_php_api)