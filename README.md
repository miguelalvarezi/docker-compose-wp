# docker-compose-wp
WordPress development environment based on Docker Compose.

## How to use

* Create src directory:

`# mkdir src`

* Download your WP project to src directory.

* Start containers:

`# docker-compose up -d`

* Now WP should be running on [http://locahost/](http://locahost/). Install it or configure it however you prefer, using the following configuration parameters for the database:
  * Host: db
  * Name: wordpress
  * User: root
  * Password: root
