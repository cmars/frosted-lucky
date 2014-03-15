A collection of some Juju charms I'm working on. Each charm resides in its own git repo, this project pulls them all into a local Juju charm repository directory structure, so that you can deploy them from one place.

### Set up the submodules
	$ git submodule init
	$ git submodule update

### Deploy stuff like
	$ juju deploy --repository=. local:precise/tor-service
