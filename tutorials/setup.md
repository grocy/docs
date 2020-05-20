# Setup

## Installation

Grocy can be installed in many ways.
- Windows application (runs as a normal windows application).
- Docker Container.
- Home Assistant Add-on.
- On your existing PHP enabled web server.

### Windows Application
Installed as a normal application. For more information see [grocy-desktop readme](https://github.com/grocy/grocy-desktop).

### Docker Container
There are two maintained docker images, [grocy/grocy-docker](https://github.com/grocy/grocy-docker) and [linuxserver/docker-grocy](https://github.com/linuxserver/docker-grocy). The official docker container comes with everything needed to get started from scratch, the linuxserver container is more suitable if you already got a reverse proxy solution running.

If you do not have docker and docker-compose installed you have to install them by following [these instructions for docker](https://docs.docker.com/get-docker/) and [these for docker-compose](https://docs.docker.com/compose/install/).

Now you have to download the files, either manually from [grocy/grocy-docker](https://github.com/grocy/grocy-docker) or with git.

In a terminal, navigate to where you want your install to be. Then run the following commands:
```
git clone https://github.com/grocy/grocy-docker
cd grocy-docker
docker-compose pull
docker-compose up
```
depending on your setup you might need to write ´sudo docker-compose´ instead of ´docker-compose´ 

Your grocy server should now be accessible from (if you are at the server):
- http://localhost 
- https://localhost 

or (if it is a remote server):

- http://< ip-address-of-your-server >
- https://< ip-address-of-your-server >

### Home Assistant Add-on

If you have an extra Raspberry Pi this might be the easiest solution. Home Assistant is a home automation system that have grocy as an add-on.
[Follow these instructions to get Home Assistant running on you Raspberry Pi](https://www.home-assistant.io/getting-started/).

When you have entered home assistant and see this screen select the supervisor, add-on store, search for grocy, select grocy, click install, start the add-on, click the "OPEN WEB UI" to get to the grocy screen.

![Home Assistant](/images/homeassistantsetup.png)

### Existing web server

If you have a web server running and would like to run grocy on it. The [How to install] (https://github.com/grocy/grocy#how-to-install) on the github is probably enough to get you up and running.

## Setting up users

You can set up your users once you log in with the default admin account (user admin with same password - you should change this for security reasons, of course, by clicking the username and selecting change password). 

Choose the main settings (wrench icon on the top right), and select Manage users. Here you can Add new users, edit and delete existing ones. New users require at minimum a username and a password.

! All users have administrator rights.

## User specific settings

User specific setting control basic interface settings. They can for example be used to hinder an always on tablet in the kitchen to go to sleep or have a less bright appearance at night. The kitchen tablet in this example would be its own user.

![user settings](/images/usersettings.png)

## Grocy Settings

Many important settings in grocy such as the language of your grocy server, currency, first day of the week and disabling of features are changed by editing a text file.

In your grocy install you will find a folder named `data` in that folder you will find a file named `config.php`. This config file can be opened with any text editor.

On a linux server this file can be opened by
```
nano path-to-grocy/data/config.php
```

Part of the config file is seen below:

```
# Either "production", "dev", "demo" or "prerelease"
# When not "production", authentication will be disabled and
# demo data will be populated during database migrations
Setting('MODE', 'production');

# Either "en" or "de" or the directory name of
# one of the other available localization folders in the "/localization" directory
Setting('CULTURE', 'en');

# This is used to define the first day of a week for calendar views in the frontend,
# leave empty to use the locale default
# Needs to be a number where Sunday = 0, Monday = 1 and so forth
Setting('CALENDAR_FIRST_DAY_OF_WEEK', '0');
```
A line that starts with `#` is a comment to help you as a user understand following setting and how you can edit it. The comment is ignored by grocy.

By changing `production` to `demo` your grocy will be filled with example data. Same as in this [demo](https://en.demo.grocy.info/).

```
Setting('MODE', 'demo');
```

When you use grocy to manage your home you want `MODE` setting to be set to `production`. All other options are more dependent on how you want grocy to behave. (Tip: To actually make Grocy usable for your home and routines, disabling features can often be the key.)

Depending on how you run your grocy instance, you might need to restart it after changes to the config.