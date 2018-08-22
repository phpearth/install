# PHP installation wizard

This wizard is available online at https://install.php.earth

## Local installation

To install this application locally:

```bash
composer install
```

and then build static files:

```bash
php vendor/bin/sculpin generate --watch --server
```

Your newly generated PHP installation wizard is now accessible at
`http://localhost:8000/`.

## Previewing development builds

By default the site will be generated in `output_dev/`. This is the location of
your development build.

To preview it with Sculpin's built in webserver, run either of the following
commands. This will start a simple webserver listening at `localhost:8000`.

### Using Sculpin's internal webserver

#### Generate command

To serve files right after generating them, use the `generate` command with
the `--server` option:

    php vendor/bin/sculpin generate --server

To listen on a different port, specify the `--port` option:

    php vendor/bin/sculpin generate --server --port=9999

Combine with `--watch` to have Sculpin pick up changes as you make them:

    php vendor/bin/sculpin generate --server --watch

#### Server command

To serve files that have already been generated, use the `serve` command:

    php vendor/bin/sculpin serve

To listen on a different port, specify the `--port` option:

    php vendor/bin/sculpin serve --port=9999

### Using a standard webserver

The only special consideration that needs to be taken into account for standard
webservers **in development** is the fact that the URLs generated may not match
the path at which the site is installed.

This can be solved by overriding the `site.url` configuration option when
generating the site.

    sculpin generate --url=http://my.dev.host/blog-skeleton/output_dev

With this option passed, `{{ site.url }}/about` will now be generated as
`http://my.dev.host/blog-skelton/output_dev/about` instead of `/about`.


## Publishing production builds

When `--env=prod` is specified, the site will be generated in `output_prod/`.
This is the location of the production build.

    php vendor/bin/sculpin generate --env=prod

These files are suitable to be transferred directly to a production host.

Deployment is done automatically using Travis on push and successful build.

## License and contributing

[Contributions](docs/CONTRIBUTING.md) are most welcome. This repository is
released under the [MIT license](LICENSE). This project also includes a
[code of conduct](docs/CODE_OF_CONDUCT.md).
