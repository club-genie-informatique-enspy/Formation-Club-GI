# Lesson 2: Installing and Configuring Git

Now that we know what Git is, it's time to install and configure it on your machine.

## Installing Git

Git is compatible with all major operating systems.

### Windows

The easiest way to install Git on Windows is to download and install **Git for Windows** from the official website: [https://git-scm.com/download/win](https://git-scm.com/download/win).

The installer will guide you. You can leave the default options, as they are generally well-suited for beginners.

### macOS

If you already have the Xcode developer tools, Git is likely already installed. To check, open a terminal and type:

```bash
git --version
```

If you don't have it, the easiest way is to install it with **Homebrew**, a package manager for macOS. If you don't have Homebrew, install it first. Then, in the terminal, type:

```bash
brew install git
```

### Linux (Debian/Ubuntu)

On Debian-based distributions like Ubuntu, you can easily install it via the `apt` package manager. Open a terminal and type:

```bash
sudo apt update
sudo apt install git
```

## Initial Configuration

Once Git is installed, there are two essential configurations to make. They are important because they will be used to identify the author of every commit you make.

Open a terminal (or Git Bash on Windows) and type the following commands, replacing the examples with your own information.

### 1. Configure your username

This name will be visible in the history of your projects.

```bash
git config --global user.name "Your Name"
```

### 2. Configure your email address

This email address will also be attached to your commits. Use the same email address as your GitHub account if you have one.

```bash
git config --global user.email "your.email@example.com"
```

The `--global` option means that this configuration will apply to all Git projects you use on your machine. You can also configure this information for a single project by omitting the `--global` option and running the command from the project's directory.

## Verifying your configuration

To check that the information has been saved correctly, you can use the following command:

```bash
git config --list
```

You should see, among other options, the `user.name` and `user.email` lines that you just set.

And that's it! Git is installed and ready to be used. In the next lesson, we will create our first repository and learn the basic commands.
