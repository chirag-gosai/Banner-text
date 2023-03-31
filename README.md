# Load Check and Disk usage

## 📖 Table of Contents
- [❓ Description](#-Description-)
- [✨ Prerequisite](#-Prerequisite-)
- [💾 Installation](#-installation-)
- [💾 Configuration](#-configuration-)
- [💾 Installation2](#-installation2-)
- [🧰 Contributing](#️-Contributing-)
- [⚠️ License](#-License-)

## ❓ Description [🔝](#-table-of-contents)

Bash scripting is a powerful way to automate tasks on a Linux server and can be used to save time and efficiency when managing a server. One task that is useful to script is to check the load and disk usage on a server. This can be done in a bash script for Linux servers. The script will first check the server's load and collect the output of the [uptime](https://man7.org/linux/man-pages/man1/uptime.1.html) command. This command displays the load for the last 1, 5, and 15 minutes. From the output, the script can compare this against a set threshold, and if it exceeds the threshold, then an alert is sent to the administrator. The script will then run the [df](https://man7.org/linux/man-pages/man1/df.1.html) command to check the disk usage. This command displays the size, used, available and percentage of usage for each of the mounted file systems. The script can then compare currently used space with the threshold percentage, if it exceeds then the alert will send to administrator. Finally, the script can also be used to report on the total disk usage of the server. This can provide a quick view of the trends and if action needs to be taken to free up disk space. All of this can be done by a single bash script for a Linux server.

## ✨ Prerequisite [🔝](#-table-of-contents)
- [mutt](https://linux.die.net/man/1/mutt) installed and configured in system (guide [here](https://www.fosstechnix.com/install-and-configure-mutt-on-ubuntu-centos/)).
- linux server with Internet connection.
- script file with default.config.

## 💾 Installation [🔝](#-table-of-contents)

To get auto alerts add this script in [crontab](https://man7.org/linux/man-pages/man5/crontab.5.html). (Below cron runs at every minute.)

```bash
# replace '/path/to/script' with actual path of script.
* * * * * bash /path/to/script/run.sh
```

Also, you can directly run the script by going into script directory and invoking it or directly run it with full path.
```bash
# must use 'bash' or './' to invoke the script.

# by going into script directory and invoking
bash run.sh
# or
./run.sh

# using full path
bash /path/to/script/run.sh
# or
./path/to/script/run.sh
```
## 💾 Installation2 [🔝](#-table-of-contents)

## Configuration [🔝](#-table-of-contents)

### CUSTOM_CONFIG
it is used for enabling support of custom configuration. it supports binary values ('0' or '1'). where '0' is for disabling and '1' is for enabling this function. default value is '0'. if you set it '1' then **'CUSTOM_CONFIG_PATH'** is must provided.

### CUSTOM_CONFIG_PATH
it is used to specify the path of custom configuration that is going to be loaded to the script. it's not required if **'CUSTOM_CONFIG'** is set to '0' but, it is must if you set **'CUSTOM_CONFIG'** to '1'. if file not found or not existed then default configuration file will be loaded and error mail will send to administrator.

### load_check
load check is a function that checks the load of Linux system followed by 1,5 and 15 minutes ago. this function can be enabled or disable using Boolean value. default value of load_check is 'load_check=true'.

### disk_usage
disk usage is a function that checks the current disk usage of Linux system. this function can be enabled or disable using Boolean value. default value of load_check is 'load_check=true'.

### recipient
is mail address of receiver. default value is recipient="alticon-alert@alticon.in".

### BASE_FILE_PATH
is directory of where the script is stored. default value is BASE_FILE_PATH="/root/miscellaneous".

### BASE_LOG_PATH
is directory for logs. default value is BASE_LOG_PATH="/var/log/alticon/miscellaneous".

### Use only for load_check function

#### LOAD_THRESHOLD
is used to store value if load average cross that limit then it'll trigger email. default value is LOAD_THRESHOLD="50".

#### JSTACK_THRESHOLD
is used to trigger JSTACK to Java running servers and it'll send JSTACK in email. default value is JSTACK_THRESHOLD="100".

#### JSTACK_CALL_SCRIPT
is used to store the location of Get Jstack script which trigger if load average is over JSTACK_THRESHOLD. default value is JSTACK_CALL_SCRIPT="/root/miscellaneous/connector.sh".

### Use only for disk_usage function

#### WARNING_PERCENTAGE
is used to store the value in percentage. if disk usage of cross that limit then it'll trigger email. default value is WARNING_PERCENTAGE="70".

#### MAX_USAGE_PERCENTAGE
is used to trigger mail to **recipient** if disk usage percentage is over then **MAX_USAGE_PERCENTAGE**. default value is MAX_USAGE_PERCENTAGE="90".

```bash
NOTE: A Default configuration is provided with script do not remove it else script will not function.
      if you want to make any changes in default.conf make copy of that file and use it as custom 
      config by setting 'CUSTOM_CONFIG' to '1' and setting path of custom config into
      'CUSTOM_CONFIG_PATH' it is recomanded method.
```
 
## 🧰 Contributing [🔝](#-table-of-contents)

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## ⚠️ License [🔝](#-table-of-contents)

Thank you for your interest in our script. This license agreement (the "Agreement") governs the use of the script (the "Product") provided by Alticon PVT LTD. ("Company") to the individual or entity ("Licensee") who has acquired the Private License.

By using the Product, Licensee agrees to be bound by the terms and conditions of this Agreement. If Licensee does not agree to the terms and conditions of this Agreement, Licensee may not use the Product and must immediately cease any use of the Product.
