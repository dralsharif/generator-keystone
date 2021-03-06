# Keystone Generator

A [Yeoman](http://yeoman.io) generator for [KeystoneJS](http://keystonejs.com), the model-driven cms for node.js built on Express and MongoDB.

`yo keystone` will scaffold a new KeystoneJS project for you, and offer to set up blog, gallery, and enquiry (contact form) models + views.

## Getting Started

First up, you'll need Node.js >= 0.12 and MongoDB >= 3.0 installed. If you don't have them, follow the **Dependencies** instructions below.

Create an empty directory for your new KeystoneJS Project, then run the generator:

````
$ mkdir myproject
$ cd myproject
$ npx -p yo -p generator-keystone yo keystone
````

_NOTE: If you see errors, check the [problems](#err-please-try-running-this-command-again-as-rootadministrator) section below._

The generator will ask you a few questions about which features to include, then prompt you for Cloudinary and Mailgun account details.

**These accounts are optional**, but Cloudinary is used to host the images for the blog and gallery templates. You can get a free account for each at:

* [Cloudinary](https://cloudinary.com/users/register/free) - Image serving and management in the cloud
* [Mailgun](https://app.mailgun.com/signup) - Easy email integration

### I want the default keystone start project

You can run

```
yo keystone auto
```

to generate a starter project with all default options selected. This is good for experimenting with keystone, but will require adjustment to use as an ongoing project, most importantly:

* Replace default cloudinary credentials with your own cloudinary credentials
* Set up email

### Keystone Beta vs. Stable

As of v5.0, the generator will install the latest Keystone 4.0 beta. The beta version is generally safe for production use; the only things blocking a final release are updated documentation, guides and minor cosmetic tweaks.

If you'd prefer to use the old v0.3.x release of Keystone, simply downgrade the version of keystone in the `package.json` the generator creates and reinstall all dependencies.

### Node 0.12 Notes

Both KeystoneJS 4.0 and the generator are compatible with Node 0.12, however we'll be bumping this requirement to Node v6+ in the next version.

Please note that the bundled version of ESLint is only compatible with Node 4+ so if you use this generator with 0.12, make sure you downgrade or remove that dependency.

### What next?

When you've got your new project, check out the [KeystoneJS Documentation](http://keystonejs.com/docs) to learn more about how to get started with KeystoneJS.

## Problems?

### ERR! Please try running this command again as root/Administrator.

When running `npm install -g generator-keystone`, you may get an **EACCES** error asking you to run the command again as root/Administrator. This indicates that there is a permissions issue.

On your development system you can change directory ownership to the current $USER so you do not have to run `sudo` while installing untrusted code:

````
sudo chown -R $USER /usr/local

# Other directories may be required depending on your O/S
sudo chown -R $USER /usr/lib/node_modules/
````

For a production/shared environment you may wish to re-run the `npm` command with the `sudo` prefix:

````
sudo npm install -g generator-keystone
````

For more information, see the ["What, no sudo?"](http://foohack.com/2010/08/intro-to-npm/#what_no_sudo) of the Intro to npm by Isaac Schlueter.

### What do you mean it couldn't find my Database?

By default, KeystoneJS will look for a MongoDB server running on `localhost` on the default port, and connect to it. If you're getting errors related to the MongoDB connection, make sure your MongoDB server is running.

If you haven't installed MongoDB yet, follow the instructions below.

To connect to a server **other** than `localhost`, add a `MONGO_URI` setting to the `.env` file in your Keystone project directory:

````
MONGO_URI=mongodb://your-server/database-name
````
### What do you mean 'yo: command not found'?

When running 'yo keystone', you'll run into this problem if you don't have [Yeoman](http://yeoman.io/) installed. Yeoman is a generator ecosystem.

```
One Line Install
npm install -g yo
```

For more information, see the [Yeoman Getting Started Page](http://yeoman.io/learning/index.html).

## Dependencies

### Install Node.js

Download and install the node.js binaries for your platform from the [Node.js download page](http://nodejs.org/download/).

### Install MongoDB

If you're on a mac, the easiest way to install MongoDB is to use the [homebrew package manager for OS X](http://brew.sh/). To install it, run this in your terminal:

````
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
````

With Homebrew installed, run this in your terminal to download and install MongoDB:

````
brew install mongodb
````

This may generate a warning message

'Warning: You have not agreed to the Xcode license.  Builds will fail! Agree to the license by opening Xcode.app or running: xcodebuild -license.'  If you see this message, run:

````
sudo xcodebuild -license
````

Hit 'enter' if prompted to view and agree to the licenses, navigate to the bottom using the 'space' key, then type 'agree' before attempting the install command again.

For other platforms, see the [MongoDB installation guides](http://docs.mongodb.org/manual/installation/).


## License

[MIT License](http://en.wikipedia.org/wiki/MIT_License). Copyright (c) 2016 Jed Watson.
