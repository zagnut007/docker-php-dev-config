# docker-php-dev-config
A Docker Compose configuration for PHP development along with Apache and MySQL

I created this configuration to match the packages in use on a production web application. This configuration allows you to replace a tool such as MAMP or XAMP on your development machine. It requires Docker and Docker Compose to be installed on your machine and available via your command line.

This configuration is set to use all standard ports for Apache and MySQL. If you have other instances or services running on your machine, you may need to adjust these ports in the docker-compose.yml file for proper operation.

## Starting Up

After you have changed the files for your environment/setup, the command to run is:

```
docker-compose up
```

If you haven't configured any virtual hosts/sites, you can just put http://localhost in your browser to see your site.

## Which files to edit

### File: .env

This is your environment file for the Docker config. 

Switch the PHP and Apache versions to match your production configuration.

Be sure to update your PROJECT_ROOT to where your working PHP and HTML files are.

### File: docker-compose.yml

I use Apache environment variables to change configuration on the app. You will see these as APPMODE. You can edit and add to these environment variables if this is something you use in your configuration.

The default MySQL root password is set to "root" in this file. This can be changed if desired.

### File: php/Dockerfile

Change the first line to specify the flavor of PHP you want to install. You can find the appropriate values at https://hub.docker.com/_/php/

### File: apache/Dockerfile

Update the first line to match the version/flavor of Apache you want to run. Info found at https://hub.docker.com/_/httpd

### File: apache/demo.apache.conf

You can add additional entries to this file for "virtual" sites. Each virtual site should be a subfolder under your PROJECT_ROOT so it's available to the Apache docker container.

## Additional configuration

I recommend adding entries to your "hosts" file for domains that match virtual sites in your Apache config. This will allow you to run multiple sites under the single Docker config. You will need admin access to edit this file.

On macOS, the hosts file is at /etc/hosts

On Windows, the hosts files is at c:\windows\system32\drivers\etc\hosts

### Example Entry

This should be added at the end of the file. Do not edit existing entries or you might disable services on your machine.

```
127.0.0.1	kevinblank.local
```