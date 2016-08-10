# doko

## Installation

```sh
curl https://raw.githubusercontent.com/pedrofernandezm/doko/master/install.sh | bash
```

## Usage

### Build

It builds the docker image in the project. Doko looks for `docker/build.sh` to build the image, if it doesn't find the file then Doko tries to build the image using the docker-compose file.

### Clean

This command helps you free space from your computer removing containers and images that are not used.

The containers to be removed are the ones that exited weeks ago.

**Note:** *Have in mind that Data Volume Containers usually are not running, this means that they might be lost when you clean containers.*

Next, it will ask confirmation to remove dangling or untagged images.

> These images occur when a new build of an image takes the `repo:tag` away from the image ID, leaving it as `<none>:<none>` or untagged.
>
> -- <cite>Docker team</cite>

### Upgrade

Use this to download the latest version of Doko. It will display the downloaded version when it finishes.

### Version

Display the current version of Doko.

### Setup

First Doko will look for `docker/setup.sh` to run the custom setup, otherwise will follow these steps:

1. Start Postgres container.
2. Run `doko build` to build the necessary images.
3. Run `rake db:setup`.
4. Spin up the containers using docker-compose.

### Up

An alias for `docker-compose up`.

### Troubleshoot

It fixes a problem when sometimes the server PID file already exists. Doko removes the file, stop the web container, removes it and start the service again.

### Rails and Rake

Doko executes `rails` and `rake` commands in a web service container.

### Stop, ps, rm and up

Doko runs docker-compose commands. You can pass options for each command.
