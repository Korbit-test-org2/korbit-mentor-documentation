# Korbit AI Mentor

To use Korbit to analyze your local files, you can make use of our CLI tool. This tool is simple to install and allows you to pass Korbit local files as the targets for its scans to identify issues the same ways it does for your PRs.

Pick the install method to the right that best matches your local machine, click on a button to copy the command to your clipboard and run it using your terminal to get started.

**Note:** you need an account on https://mentor.korbit.ai to use the CLI tool (you will need an authentication key associated to your account).

## How to Install

### PIP

Using `pip` you can install the CLI and start running analysis.

```sh
pip install korbit-mentor
```

### Binary

#### Linux - MacOS

1. Automatically installation

```sh
sudo curl https://mentor-resources.korbit.ai/cli/install.sh | sudo bash
```

1. Linux and Macos x86

```sh
sudo wget https://mentor-resources.korbit.ai/cli/latest/korbit-x86_64 -O /usr/local/bin/korbit
sudo chmod +x /usr/local/bin/korbit
```

1. MacOS arm64

```sh
sudo wget https://mentor-resources.korbit.ai/cli/latest/korbit-aarch64 -O /usr/local/bin/korbit
sudo chmod +x /usr/local/bin/korbit
```

#### Windows

```sh
wget https://mentor-resources.korbit.ai/cli/latest/korbit-win.exe -O korbit.exe
```

## Usage

To get an overview of what you can do with the korbit tool you can use the help command as follows:

```
korbit --help
```

There are 2 steps in order to be able to scan your local files:
1. you will need to authenticate with your **Korbit** account. 
2. you will need be able to specify the file or folder you want **Korbit AI mentor** to analyze for you.

### Login

In order to use the CLI you will need to authenticate your CLI by logging in using credentials generated on your https://mentor.korbit.ai account.

#### Generate keys

To generate your ID/Key pair, either create an account or login and visit your [profile page](https://mentor.korbit.ai/profile).

On your profile page you will see a **Secrets** section. Click the **Create** button and copy the ID and Key pairs.

#### Command

To authenticate your CLI instance you with your ID/Key pair, you need to use the login command, this will prompt you to input the secret id/key pair:

```sh
korbit login
```
You will see the following two prompts after activating this command:
> Please enter your secret ID:
> Please enter your secret key:

Alternatively, can directly specify the id/key pair values as arguments

```sh
korbit login --secret_id=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx --secret_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
korbit login xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

If you want to learn more about the login command you can specify login with the help command:

```sh
korbit login --help
```

You can also use environment variables to remain logged in as you run scans with korbit.
Use the following commands to avoid needing to run the `korbit login` command in every session.

```sh
export KORBIT_SECRET_ID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
export KORBIT_SECRET_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Scan

Now that you are authenticated, you can start running your first scan. To do so you need to use the `korbit scan` command and indicate the `path` of the folder/file your are looking to have korbit analyze:

```sh
korbit scan /path/to/folder ## Absolute path
korbit scan ../to/folder    ## Relative path
korbit scan .               ## Curent folder anlaysis
```

You can also review available options for Korbt scan pathing with the scan and help commands:

```sh
korbit scan --help
```


#### Output

We introduce the ability to run a scan headless, meaning that there will be no output in the terminal. But in the following default path:

```sh
# In the working directory where the korbit scan command has been executed.
cat .korbit/scan.log
```

If Korbit AI mentor find issues the command will exit with a specific code number (see `--headless` option documentation).

```sh
korbit scan --help
```

This `korbit scan --headless` flag option will be used mainly in CI/CD pipelines, to automatically stop it.
Along with the --headless command you can specify certain thresholds for only 2 metrics at the moment:

1. confidence (scale 1-10): represents how confident Korbit AI Mentor is that a particular issue is real. A higher confidence score indicates a greater level of certainty that the identified issue is valid and requires attention.
1. priority (scale 1-10): represents the level of importance or urgency assigned by Korbit AI Mentor to a particular issue. A higher priority score indicates a greater sense of urgency and the need for immediate attention to address the identified issue.

```sh
korbit scan --headless
```

**Note**: You can use the `--thresholds-*` even if the scan isn't in headless mode, this will filter the issue found and display only the one that matters for you.

#### Progress view

After you start to run a `korbit scan` command and that our system accepted the request (might take some time regarding load on our server), you will see in your terminal the progress of the scan. Each files will be updated in real time with their status.

```sh
Analysis in progress (1/1)
├── afile.js ⏳
└── afile.py ✅
Analyzing files (2)... ━━━━━━━━━━━━━━━━━━━━╺━━━━━━━━━━━━━━━━━━━  50% -:--:--
```

#### Result

At the end when every file will be analyzed you will see in your terminal different tables containing the issues' descriptions and their placement in the given file. Along that will see the priority and confidence about that issue.

```sh
                                         Category: Critical Errors
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━┓
┃ Error Description                                  ┃ File Path                  ┃ Confidence ┃ Priority ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━┩
│ There is an error on the line X, because...        │ folder/afile.js            │ 10         │ 9        │
└────────────────────────────────────────────────────┴────────────────────────────┴────────────┴──────────┘
```


## Contact

If you have any questions or need further assistance, feel free to reach out to us at [support@korbit.ai](mailto:support@korbit.ai).
