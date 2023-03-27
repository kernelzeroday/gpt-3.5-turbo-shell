# GPT-3.5-turbo Shell :rocket: :snake:

Welcome to GPT-3.5-turbo Shell, a powerful command-line tool that leverages the power of OpenAI's GPT-3.5-turbo to help you with your tasks! Written in Python, this tool is perfect for automating tasks, troubleshooting, and learning more about the Linux shell environment.

:warning: **Note**: This program sends shell output back to OpenAI for context. Please do not use this in production environments where sensitive data might be exposed.

## Warnings this software is buggy and not ready for production use
I wrote this over the weekend and it is not ready for production use. 
I am not responsible for any damage this software may cause.
Please use at your own risk.
I am planning multiple refactors and improvements to this software.
I may not fix issues with this software.
I may not respond to issues with this software.
I may not respond to pull requests with this software.
I will do my best to work on this but I have a full time job and a family.


## Donate :moneybag:

BTC: bc1q9cful5qm8z43xwpc5g4693ju3m66fqhvggmzat


ETH: 0xFA87BdE65c0bFe7302e3b267cEB360105b77D225

## Installation :wrench:

1. Clone this repository.
2. Install the required Python packages by running:
    ```
    pip install -r requirements.txt
    ```
3. Set your OpenAI API key directly in the `gptsh0.11.py` file:
    ```
    openai.api_key = "YOUR_API_KEY"
    ```

## Usage :computer:

To start the GPT-3.5-turbo Shell, simply run the following command:


Run the GPT-3.5-turbo Shell:
```sh
python gptsh0.11.py
```

Enter your desired command and let the AI assist you!


```
usage: gptsh0.11.py [-h] [-i INPUT_FILE] [--log-level LOG_LEVEL] [--api-key API_KEY] [--engine ENGINE] [--auto_exec] [--retry]
                    [--max-retries MAX_RETRIES] [--max-tries MAX_TRIES] [--tokens TOKENS] [--color] [--os OS]

GPT-3.5-turbo Shell

options:
  -h, --help            show this help message and exit
  -i INPUT_FILE, --input-file INPUT_FILE
                        File with scripted commands
  --log-level LOG_LEVEL
                        Logging level (DEBUG, INFO, WARNING, ERROR, CRITICAL)
  --api-key API_KEY     OpenAI API key
  --engine ENGINE       OpenAI engine to use
  --auto_exec           Auto execute the command
  --retry               Auto retry the command
  --max-retries MAX_RETRIES
                        Max retries for the command
  --max-tries MAX_TRIES
                        Max tries for the command
  --tokens TOKENS       Max tokens for the command
  --color               Color the output
  --os OS               Operating system
  ```



## Examples :bulb: :computer:

# Natural Language interface

```
$ python3 gptsh0.11.py --auto_exec --os 'Darwin 22'
Welcome to the GPT-3.5-turbo Shell!
Type a command or type 'exit' to quit.
> get my kernel info
To get the kernel information on Darwin, we can use the 'uname' command with the '-a' option.

uname -a
Darwin m1.local 22.3.0 Darwin Kernel Version 22.3.0: Mon Jan 30 20:39:35 PST 2023; root:xnu-8792.81.3~2/RELEASE_ARM64_T8103 arm64
> get my cpu info
To get CPU information on Darwin, we can use the `sysctl` command with the `machdep.cpu` parameter.

sysctl machdep.cpu
machdep.cpu.cores_per_package: 8
machdep.cpu.core_count: 8
machdep.cpu.logical_per_package: 8
machdep.cpu.thread_count: 8
machdep.cpu.brand_string: Apple M1
> get the gpu model
The command to get the GPU model in Darwin 22 is to use the `system_profiler` command with the `SPDisplaysDataType` option to get information about the display, which includes the GPU model.

system_profiler SPDisplaysDataType | grep Chipset
      Chipset Model: Apple M1
> get the disk space
To get the disk space, we can use the 'df' command which stands for 'disk free'. This command displays the amount of disk space available on the file system containing each file name argument.

df -h
Filesystem                             Size   Used  Avail Capacity iused     ifree %iused  Mounted on
/dev/disk3s1s1                        228Gi  8.3Gi   14Gi    39%  349475 142227720    0%   /
devfs                                 204Ki  204Ki    0Bi   100%     706         0  100%   /dev
/dev/disk3s6                          228Gi  7.0Gi   14Gi    35%       7 142227720    0%   /System/Volumes/VM
/dev/disk3s2                          228Gi  4.5Gi   14Gi    25%     907 142227720    0%   /System/Volumes/Preboot
/dev/disk3s4                          228Gi   28Mi   14Gi     1%      52 142227720    0%   /System/Volumes/Update
/dev/disk1s2                          500Mi  6.0Mi  482Mi     2%       3   4940000    0%   /System/Volumes/xarts
/dev/disk1s1                          500Mi  6.1Mi  482Mi     2%      32   4940000    0%   /System/Volumes/iSCPreboot
/dev/disk1s3                          500Mi  700Ki  482Mi     1%      36   4940000    0%   /System/Volumes/Hardware
/dev/disk3s5                          228Gi  194Gi   14Gi    94% 2910235 142227720    2%   /System/Volumes/Data
map auto_home                           0Bi    0Bi    0Bi   100%       0         0  100%   /System/Volumes/Data/home
```
# Shell command interface also works

```
$ python3 gptsh0.11.py --auto_exec --os 'Darwin 22'
Welcome to the GPT-3.5-turbo Shell!
Type a command or type 'exit' to quit.
> id
Displays the user and group IDs of the current user.

id
uid=501(kod) gid=20(staff) groups=20(staff),12(everyone),61(localaccounts),79(_appserverusr),80(admin),81(_appserveradm),98(_lpadmin),701(com.apple.sharepoint.group.1),33(_appstore),100(_lpoperator),204(_developer),250(_analyticsusers),395(com.apple.access_ftp),398(com.apple.access_screensharing),399(com.apple.access_ssh),400(com.apple.access_remote_ae)
> whoami
Displays the username associated with the current effective user ID.

whoami
kod
> ps
The 'ps' command is used to display information about running processes. The previous command output shows the user ID, group ID, and group membership of the current user.

ps
  PID TTY           TIME CMD
98987 ttys001    0:01.43 -bash
43043 ttys002    0:01.57 -bash
86422 ttys004    0:00.01 /bin/bash -c ps; echo $?
 5257 ttys005    0:00.43 -bash
28528 ttys006    0:00.60 -bash
85856 ttys011    0:00.25 -bash
41630 ttys013    0:03.36 -bash
42215 ttys013    0:00.67 vi gpt_shell.py
86401 ttys013    0:02.22 /opt/homebrew/Cellar/python@3.11/3.11.2_1/Frameworks/P
25408 ttys018    0:00.16 /opt/homebrew/bin/bash --init-file /Applications/Visua
12788 ttys043    0:00.17 /opt/homebrew/bin/bash --init-file /Applications/Visua
16488 ttys045    0:01.76 -bash
80414 ttys045    0:00.52 /opt/homebrew/Cellar/python@3.11/3.11.2_1/Frameworks/P
80432 ttys045    0:00.30 /opt/homebrew/bin/ssh -t -i /Users/kod/.ssh/google_com
> uname -a
The 'uname' command is used to print system information. The '-a' option prints all information, including the kernel name, network node hostname, kernel release, kernel version, machine hardware name, and operating system.

uname -a
Darwin m1.local 22.3.0 Darwin Kernel Version 22.3.0: Mon Jan 30 20:39:35 PST 2023; root:xnu-8792.81.3~2/RELEASE_ARM64_T8103 arm64
```


## Codebase Overview :file_folder:

- `gptsh0.11.py`: The main Python script that powers the GPT-3.5-turbo Shell.
- `install_apt.sh`: A shell script to install the required dependencies for the project.
- `requirements.txt`: A file containing the Python packages required for the project.
- `README.md`: This file, which provides an overview and instructions for the GPT-3.5-turbo Shell.

Enjoy using the GPT-3.5-turbo Shell! :tada:
