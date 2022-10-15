# Setup

## Installation

Grocy can be installed in many ways.
- Windows application (runs as a normal windows application).
- Docker or Podman Container.
- Home Assistant Add-on.
- On your existing PHP enabled web server.

### Windows Application
Installed as a normal application. For more information see [grocy-desktop readme](https://github.com/grocy/grocy-desktop).

### Docker Container
There are two maintained docker images, [grocy/grocy-docker](https://github.com/grocy/grocy-docker) and [linuxserver/docker-grocy](https://github.com/linuxserver/docker-grocy). The official docker container comes with everything needed to get started from scratch, the linuxserver container is more suitable if you already got a reverse proxy solution running.

If you do not have docker and docker-compose installed you have to install them by following [these instructions for docker](https://docs.docker.com/get-docker/) and [these for docker-compose](https://docs.docker.com/compose/install/). If you are using Podman you may or may not want to use [podman-compose](https://www.redhat.com/sysadmin/podman-compose-docker-compose).

Now you have to download the files, either manually from [grocy/grocy-docker](https://github.com/grocy/grocy-docker) or with git.

In a terminal, navigate to where you want your install to be. Then run the following commands:
```
git clone https://github.com/grocy/grocy-docker
cd grocy-docker
docker-compose pull
docker-compose up -d
```
depending on your setup you might need to write `sudo docker-compose` instead of `docker-compose`.

If your container is running on the same computer as your web browser you can access it here:
- http://localhost 
- https://localhost 

Or if it is running on a remote server access, it like this instead:

- http://< ip-address-of-your-server >
- https://< ip-address-of-your-server >

### Home Assistant Add-on

If you have an extra Raspberry Pi this might be the easiest solution. Home Assistant is a home automation system that has grocy as an add-on.
[Follow these instructions to get Home Assistant running on you Raspberry Pi](https://www.home-assistant.io/getting-started/).

When you have entered Home Assistant and see this screen select the supervisor, add-on store, search for grocy, select grocy, click install, start the add-on, click the "OPEN WEB UI" to get to the grocy screen.

![Home Assistant](/images/homeassistantsetup.png)

### Existing web server

If you have a web server running and would like to run grocy on it. The [How to install](https://github.com/grocy/grocy#how-to-install) documentation on GitHub is probably enough to get you up and running.

## Setting up users

You can set up your users once you log in with the default admin account (user admin with same password - you should change this for security reasons, of course, by clicking the username and selecting change password). 

Choose the main settings (wrench icon on the top right), and select Manage users. Here you can Add new users, edit and delete existing ones. New users require at minimum a username and a password.

! All users have administrator rights.

## User specific settings

User specific settings control basic interface settings. They can, for example, be used to prevent a tablet being used in the kitchen from going to sleep or cause it to have a less bright appearance at night. The kitchen tablet in this example would be its own user.

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/usersettings.png" width="35%"></img>

## Grocy Settings

Many important settings in grocy such as the language, currency and first day of the week (Sunday, Monday, etc.), used by your Grocy server, as well as disabling unwanted features, are changed by editing a text file.

You will find a folder named `data` inside the folder you installed Grocy into. In that folder you will find a file named `config.php`. This config file can be opened with any text editor.

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

Please see the [example](/examples/examples.md) section for some ideas of how you can setup grocy.

## Helpful tools

There are some great tools that can interact with Grocy that might be useful for you. Here is a short list that is most likely complete:
- [PantryParty](https://pantryparty.app) - iOS and Android app.
- [Barcode Buddy](https://barcodebuddy-documentation.readthedocs.io/en/latest/) - Barcode scanner tool. To make using physical scanner more efficient.
- [Home Assistant](https://www.home-assistant.io) - Home automation project with a Grocy Add-on and custom component for integration.
- pygrocy
- pygrocydm
- grocy-pyscanner
