# Korbit AI Mentor

Korbit mentor CLI will allow you to analyze any local files of your computer. You must have an account on www.korbit.ai to use it.

## How to

### PIP

Using `pip` you can install the CLI and start running analysis.

```sh
pip install korbit-mentor
```

### Binary

#### Linux - MacOS

1. Automatically installation

```sh
curl https://mentor-resources.korbit.ai/cli/installer.sh | bash
```

1. Linux and Macos x86

```sh
wget https://mentor-resources.korbit.ai/cli/korbit-x86_64 -O /usr/bin/local/korbit
```

1. MacOS arm64

```sh
wget https://mentor-resources.korbit.ai/cli/korbit-aarch64 -O /usr/bin/local/korbit
```

#### Windows

```sh
wget https://mentor-resources.korbit.ai/cli/korbit-win.exe -O korbit.exe
```

## Usage

You can first use the following command to get an overview of what you can do with the korbit tool.

```
korbit --help
```

There are 2 steps in order to be able to scan your local files. First you will need to authenticate with your **Korbit** account. Second, you will need be able to specify the file or folder you want **Korbit AI mentor** to analyze for you.

### Login

In order to use the CLI you will need to login using credentials generated on your https://mentor.korbit.ai account.

#### Generate keys

Go to your [profile page](https://mentor.korbit.ai/profile), you will see a **Secrets** section. Click **Create** button.

#### Command

You need to use the command, this will propose you to input the secret id/key pair:

```sh
korbit login
```

> Please enter your secret ID:
> Please enter your secret key:

Or you can directly specify the values as arguments

```sh
korbit login --secret_id=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx --secret_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
korbit login xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

This command will ask you to fill your secret_id and secret_key. We will see in the next section how to generate those.

If you want to learn more about the login command please user:

```sh
korbit login --help
```

You can also use environment variables to be logged in and run the scan command.
Doing the following will replace the need of running the `korbit login` command.

```sh
export KORBIT_SECRET_ID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
export KORBIT_SECRET_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Scan

Now that you are all setup, you can start running your first scan:

```sh
korbit scan /path/to/folder ## Absolute path
korbit scan ../to/folder    ## Relative path
korbit scan .               ## Curent folder anlaysis
```

You can also see what are the available options with the scan command this way:

```sh
korbit scan --help
```

## Contact

If you have any questions or need further assistance, feel free to reach out to us at [support@korbit.ai](mailto:support@korbit.ai).
