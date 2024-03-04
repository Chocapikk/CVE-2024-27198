# TeamCity Exploit Script 🛠️

This script is designed to demonstrate a potential exploit on TeamCity servers by attempting Remote Code Execution (RCE) through exposed REST APIs. It includes functionality to add users with system administration roles and execute commands remotely.

## Features 🌟

- **Add User**: Creates a new user with random credentials and system administration role. (`--url` option required)
- **Execute Command**: Attempts to execute a command on the TeamCity server through an interactive shell. (Only available with `--url` and after adding a user)
- **Batch Processing**: Scans a list of URLs to identify potentially vulnerable TeamCity servers. (Using the `--list` option)

## Usage 📖

### Single Target

To assess a single TeamCity server for vulnerabilities and attempt Remote Code Execution (RCE), you can use the following command:

```bash
python exploit.py --url https://example.com --add-user
```

This command tries to add a new user with system administrator privileges to test the RCE capability. If successful, it initiates an interactive shell, allowing further commands to be executed as the newly added user.

Without the `--add-user` option, the script will still make a request to the specified server and attempt to list users, which can indicate whether the server is potentially vulnerable:

```bash
python exploit.py --url https://example.com
```

### Batch Processing

To scan a list of URLs for potentially vulnerable TeamCity servers:

```bash
python exploit.py --list urls.txt --output output.txt
```

This process checks each URL in the provided file and writes those that appear to be vulnerable to the specified output file. Please note that in batch mode, the script assesses the vulnerability based on the server's response to a standard request and does not attempt RCE or user creation.

**Note**: The `--add-user` functionality is exclusively available with the `--url` option for targeted testing and does not apply to batch processing with the `--list` option. Batch processing is designed to identify servers that may be vulnerable to further investigation and does not interact with the server beyond initial assessment requests.

## Methodology 💡

This script uses known endpoints and methods for interacting with TeamCity servers. It attempts an older method for RCE that may not work on all configurations or updated versions of TeamCity. There may be other methods for achieving RCE on TeamCity servers that are not covered by this script.

## Legal and Ethical Disclaimer ⚠️

This tool is intended for educational purposes and ethical security testing only where explicit, authorized permission has been granted. The use of this script on any server, application, or network without such permission is strictly prohibited. Unauthorized testing is illegal and unethical. The author or contributors are not responsible for any misuse or damage caused by this script. Use this tool responsibly and always comply with all applicable laws and regulations.
