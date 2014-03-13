A collection of some Juju charms I'm working on. Each charm resides in its own git repo, this project pulls them all into a local Juju charm repository directory structure, so that you can deploy them from one place.

1. Clone this repo
2. 
  $ git submodule init
3.
  $ git submodule update
4. Deploy stuff with
  $ juju deploy --repository=. local:precise/tor-service
  or whatever else you like.
