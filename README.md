<img align="right" width="300" src="foreman.png" />

# Forkedman
Forkedman is a fork of the popular toolchain manager [Foreman](https://github.com/Roblox/foreman) that intends to continue development on this tool since for some reason Roblox abandoned development on Foreman.

## Installation

### GitHub Releases
You can download pre-built Foreman releases for Windows, macOS, and Linux from the [Releases](https://github.com/Roblox/foreman/releases) page.

### From Source
If you have [Rust](https://www.rust-lang.org/) 1.41.0 or newer installed, you can also compile Forkedman by cloning this repository and installing the binary from source:

```bash
cargo install --path .
```

## Usage
Forkedman downloads tools from GitHub and references them by their `user/repo` name, like `Roblox/foreman`.

On first run (try `foreman list`), Forkedman will create a `.foreman` directory in your user folder (usually `~/.foreman` on Unix systems, `%USERPROFILE%/.foreman` on Windows).

It's recommended that you **add `~/.foreman/bin` to your `PATH`** to make the tools that Foreman installs for you accessible on your system.

### System Tools
To start using Forkedman to manage your system's default tools, create the file `~/.foreman/foreman.toml`.

A Forkedman config that lists Rojo could look like:

```toml
[tools]
rojo = { source = "rojo-rbx/rojo", version = "0.5.0" }
```

Run `foreman install` from any directory to have Foreman pick up and install the tools listed in your system's Foreman config.

Now, if you run `rojo` inside of a directory that doesn't specify its own version of Rojo, Forkedman will run the most recent 0.5.x release for you!

### Project Tools
Managing a project's tools with Forkedman is similar to managing system tools. Just create a `foreman.toml` file in the root of your project.

A Forkedman config that lists Remodel might look like this:

```toml
[tools]
remodel = { source = "rojo-rbx/remodel", version = "0.6.1" }
```

Run `foreman install` to tell Forkedman to install any new binaries from this config file.

When inside this directory, the `remodel` command will run the latest 0.6.x release of Remodel installed on your system.

### Authentication
To install tools from a private GitHub repository, Forkedman supports authenticating with a [Personal Access Token](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line).

Use `foreman github-auth` to pass an authentication token to Forkedman, or open `~/.foreman/auth.toml` and follow the contained instructions.

## Troubleshooting
Forkedman is a work in progress tool and has some known issues. Check out [the issue tracker](https://github.com/Roblox/foreman/issues) for known bugs.

If you have issues with configuration, you can delete `~/.foreman` to delete all cached data and start from scratch. This directory contains all of Forkedman's installed tools and configuration.

## License
Forkedman is available under the MIT license. See [LICENSE.txt](LICENSE.txt) or <https://opensource.org/licenses/MIT> for details.