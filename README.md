# dhall-nginx

Have a look at https://github.com/denizdogan/dhall-nginx for a more complete/maintained version.

I doubt that I'll be working on this anytime soon, if you've any issues/PRs you want to submit I'll have a look at them regardless.

## Tryout some of the examples

`dhall text <<< './Server/makeServer ./Server/Spec.example'`

```nginx
server {
    server_name example.com;
    listen localhost:3000;


    error_log /var/log/nginx/example.com_error.log;


    location ~* ^/admin {
      rewrite regex replacement;
      add_header X-Custom Custom;

      proxy_set_header X-Forward-Proto https;

      proxy_pass localhost:3000;
  }

}
```

## Content

Every directory contains a `Spec` file which is the specification for the folder `name`, i.e. `Location/Spec` is the specification for the `location` directive.

Most directories contain a `Spec.empty` and `Spec.example` file, where `.empty` populates the record with default values and `.example` provides a record with example values.
