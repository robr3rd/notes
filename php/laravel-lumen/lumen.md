# Lumen

## Add compatibility for most Laravel 5 packages
Many pakages that were originally intended for Laravel and never properly tested for Lumen will report errors about undefined functions. These functions, indeed, are *not* defined in Lumen, but are instead specific for Laravel. That being said, there is no reason why they can't just be added.

Let's do that!

1. Save [this file](https://gist.github.com/vluzrmos/30defc977877e0eba7b2) as `app/helpers.php`
2. Update your `composer.json` to include:

```json
"autoload-dev": {
	// ...
	"files": [
		"app/helpers.php"
	]
},
```
