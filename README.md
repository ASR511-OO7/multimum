# Multimum
This Python script allows you to execute a specified command template on multiple IP pairs concurrently. It uses multithreading to run the commands on multiple targets at once, making it a powerful tool for automated tasks such as scanning, network tests, or service checks across a range of hosts.

# Features
Concurrent Execution: The script uses multithreading to execute commands on multiple IP
pairs simultaneously, allowing for faster completion.
Custom Command Template: You can specify a custom command with placeholders for IP and PORT, enabling flexibility in the commands you run.
Error Handling: The script captures both standard output and error output from the command, providing comprehensive feedback on the execution.
Input Validation: The script skips invalid lines in the input file that do not conform to the expected IP
format.

## Prerequisites
**Python 3.x:** This script is written in Python 3 and requires Python 3.x to run.

## Required Modules
The script uses the standard libraries argparse, subprocess, threading, and queue. No external modules are needed.

# Installation
**Clone the Repository:**
```bash
git clone https://github.com/ASR511-OO7/multimum.git
cd multimum
```

**Ensure Python 3 is Installed:**
Make sure Python 3 is installed on your system. You can check by running:
```python
python3 --version
```
# Usage
**Prepare the IP List:**
Create a text file that contains a list of IP pairs, each on a new line. For example:
```text
192.168.1.1:22
192.168.1.2:80
10.0.0.1:443
```
**Run the Script:**
Use the following command to execute the script:
```bash
python3 multimum.py -l path/to/ip_port_list.txt -c "your_command_template" [-t number_of_threads]
-l, --list: Path to the file containing IP pairs.
-c, --command: Command template to run, with "IP" and "PORT" as placeholders.
-t, --threads: Number of concurrent threads to use (default is 4).
```
# Example:
```bash
python3 multimum.py -l targets.txt -c "nmap -p PORT IP" -t 10
```
This command would run Nmap scans on all the IP pairs listed in targets.txt using 10/defined concurrent threads.
**Output:**
The script prints the output of the command for each IP pair. If any errors occur during command execution, they will also be displayed.
# Example Commands
**Ping Test:**
```bash
python3 multimum.py -l ips.txt -c "ping -c 3 IP" -t 5
```
**Port Scan with Nmap:**
```bash
python3 multimum.py -l targets.txt -c "nmap -p PORT IP" -t 10
```
**HTTP GET Request:**
```bash
python3 multimum.py -l web_servers.txt -c "curl http://IP:PORT" -t 8
```
**Notes:**
Ensure that the command template you use is valid for the type of target you're running it against.
Adjust the number of threads (-t) based on your system's capability and the number of targets to balance performance and resource usage.
