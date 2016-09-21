# docker-compose-wp
WordPress development environment based on Docker Compose.

## How to use

* Clone this repository and change into it's directory.

* Download your WP project to a newly created src directory. For example:

`# git clone git@github.com:you/your-repo.git src`

* Start containers:

`# docker-compose up -d`

* Now WP should be running on [http://locahost/](http://locahost/). Install it or configure it however you prefer, using the following configuration parameters for the database:
  * Host: db
  * Name: wordpress
  * User: root
  * Password: root
