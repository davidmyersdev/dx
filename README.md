# dx

Execute commands in a sandbox. Docker is the only dependency.

![](.images/screenshot.png)

## Use

You can run `dx -h` for usage info and examples.

```shell
Usage
    dx [-hs][-i <image>] <command>

Options
    -h          show usage info
    -i <image>  specify a docker image to use (e.g. node:lts-alpine)
    -s          launch an interactive shell

Examples
    dx npx cowsay hello
    dx bundle exec rails c
    dx -i node:lts-alpine npm init
    dx -s ruby
```

### Example

```shell
dx npm init -y
```

The current directory is mounted in a Docker [volume](https://docs.docker.com/engine/reference/commandline/run/#mount-volume--v---read-only) and set as the [working directory](https://docs.docker.com/engine/reference/commandline/run/#set-working-directory--w) inside the container at `/dxdir`.

### Supported commands

- `node` `npm` `npx` `yarn`
- `php` `composer`
- `python` `pip`
- `ruby` `bundle` `bundler` `gem` `irb`

### Run any command by specifying an image

Specify an image with the `-i` flag.

```shell
dx -i node:lts-alpine npm init
```

### Run multiple commands by launching an interactive shell

Launch an interactive shell for a given command with the `-s` flag.

```shell
dx -s composer
```

## Install

Installation is quick.

```shell
# clone the repo
git clone https://github.com/voraciousdev/dx.git

# make it available anywhere
mv ./dx/dx /usr/local/bin
```