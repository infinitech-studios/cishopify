This is a Codeigniter wrapper around the Shopify PHP API

This is till a work in progress, and is FAR from complete!

# Usage

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

# Reference

Coming soon...