# Implementing JWT Authentication for WooCommerce REST API

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Step-by-Step Instructions](#step-by-step-instructions)
4. [Testing the API](#testing-the-api)
5. [Key Points to Consider](#key-points-to-consider)
6. [Troubleshooting](#troubleshooting)
7. [Contributing](#contributing)
8. [License](#license)

## Introduction

This guide provides step-by-step instructions for implementing JWT authentication for the WooCommerce REST API. By following these steps, you'll be able to secure your WooCommerce API endpoints using JSON Web Tokens (JWT).

## Prerequisites

- WooCommerce installed and configured on your WordPress site
- Basic understanding of WordPress and WooCommerce
- Access to your WordPress dashboard

## Step-by-Step Instructions

1. Install the Simple JWT Login plugin on your WordPress site.

2. Go to Settings > Simple JWT Login in your WordPress dashboard.

3. On the General tab, set a JWT Decryption Key.

4. On the Authentication tab:
   - Enable "Allow authentication"
   - In the JWT Payload parameters section, check all options

5. On the Protect Endpoints tab:
   - Enable "Protect endpoints"
   - Set "Apply on specific REST endpoints"

6. Add your WooCommerce endpoint(s) to make them work with JWT. For example:
/wp-json/wc/v3/orders


7. Create a custom PHP script in your theme's `functions.php` file:

php function add_cors_http_header() { header("Access-Control-Allow-Origin: *"); header('Access-Control-Allow-Methods: GET, POST, PATCH, PUT, DELETE, OPTIONS, READ'); header('Access-Control-Allow-Headers: Origin, X-Auth-Token,authorization,XMLHttpRequest'); header("Access-Control-Allow-Credentials: true");

if ('OPTIONS' == _SERVER['REQUEST_METHOD']) { status_header(200); if(!str_contains(_SERVER['REQUEST_URI'], "simple-jwt-login")) { exit(); } } }

add_action('init', 'add_cors_http_header');




## Testing the API

Use a tool like Postman to test making authenticated requests to your WooCommerce API endpoints using the JWT token.

## Key Points to Consider

- Implement proper error handling for expired tokens.
- Regularly rotate your JWT secret keys for enhanced security.

## Troubleshooting

If you encounter issues:
- Double-check all configuration steps.
- Verify that your WordPress and WooCommerce installations are up-to-date.
- Consult the Simple JWT Login plugin documentation for troubleshooting tips.

## Contributing

Contributions to this guide are welcome. Please feel free to submit a Pull Request if you'd like to improve or expand on these instructions.

## License

This guide is released under the [MIT License](https://opensource.org/licenses/MIT).
