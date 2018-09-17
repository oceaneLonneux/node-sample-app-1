# Sparta Node Sample App

## Instructions
Add to the README.md instructions that explain the steps the developer will need to go through to use this environment i.e they'll need to install vagrant and virtual box, install all the plugins and know where to put their app code.

### Virtual Machine
Don't forget to install Virtual Box before! You might have an issue with securtiy.
If so, go to privacy in Settings, then accept the Oracle part.

### Vagrant
You have to download Vagrant first. It won't appear in the Applications folder afterards.
To install vagrant :
`'vagrant init ubuntu/xenial64'
go into the hosts file to know your IP.
'cat /etc/hosts'
'atom .'`
In atom, go into the Vagrantfile and enter:
`'Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.network("private_network", ip: "192.168.10.100")
  config.hostsupdater.aliases = ["development.local"]
end'`
Go back to your terminal after saving.
Launch vagrant.
`'vagrant up'
'vagrant plugin install vagrant-hostsupdater'
'vagrant ssh'`
in vagrant@ubuntu-xenial : `'sudo apt-get install nginx'`

## Bonus
The goal is that the developers should be able to simply clone your repo and run "vagrant up". Can you automate the installation of the required vagrant plugins?
`required_plugins = %w( vagrant-hostmanager vagrant-someotherplugin )
  required_plugins.each do |plugin|
  system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end`

## Description

This app is intended for use with the Sparta Global Devops Stream as a sample app. You can clone the repo and use it as is but no changes will be accepted on this branch.

To use the repo within your course you should fork it.

The app is a node app with three pages.

### Homepage

``localhost:3000``

Displays a simple homepage displaying a Sparta logo and message. This page should return a 200 response.

### Blog

``localhost:3000/posts``

This page displays a logo and 100 randomly generated blog posts. The posts are generated during the seeding step.

This page and the seeding is only accessible when a database is available and the DB_HOST environment variable has been set with it's location.

### A fibonacci number generator

``localhost:3000/fibonacci/{index}``

This page has be implemented poorly on purpose to produce a slow running function. This can be used for performance testing and crash recovery testing.

The higher the fibonacci number requested the longer the request will take. A very large number can crash or block the process.


### Hackable code

``localhost:3000/hack/{code}``

There is a commented route that opens a serious security vulnerability. This should only be enabled when looking at user security and then disabled immediately afterwards

## Usage

Clone the app

```
npm install
npm start
```

You can then access the app on port 3000 at one of the urls given above.

## Tests

There is a basic test framework available that uses the Mocha/Chai framework

```
npm test
```

The test for posts will fail ( as expected ) if the database has not been correctly setup.
