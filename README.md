A collection of some Juju charms I'm working on. Each charm resides in its own git repo, this project pulls them all into a local Juju charm repository directory structure, so that you can deploy them from one place.

## Set up the submodules
	$ git submodule init
	$ git submodule update

## Deploy an OpenPGP keyserver pool

### Deploy Hockeypuck
	$ juju deploy --repository=. local:precise/hockeypuck
	$ juju deploy postgresql
	$ juju add-relation hockeypuck postgresql
	$ juju expose hockeypuck

### Deploy an SKS
	$ juju deploy --repository=. local:precise/sks

#### Or two
The SKS charm automatically synchronizes when clustered.

	$ juju add-unit sks

### Set up synchronization
	$ juju add-relation hockeypuck:gossip sks:peer

## Deploy an anonymous blog
Use the tor:hidden-website relation to publish any http service as a [Tor hidden service](https://www.torproject.org/docs/tor-hidden-service.html.en).

### Start with a typical Wordpress blog
	$ juju deploy wordpress
	$ juju deploy mysql
	$ juju add-relation wordpress mysql

### Publish anonymously
	$ juju deploy --repository=. local:precise/tor
	$ juju add-relation wordpress tor
