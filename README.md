# Web Hacking ToolKit

[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/signedsecurity/web-hacking-toolkit/🎉%20CI%20to%20Docker%20Hub)](https://github.com/signedsecurity/web-hacking-toolkit/actions)
[![Docker Image Size Badge](https://img.shields.io/docker/image-size/signedsecurity/web-hacking-toolkit/latest)](https://hub.docker.com/r/signedsecurity/web-hacking-toolkit/)
[![Docker Pulls Badge](https://img.shields.io/docker/pulls/signedsecurity/web-hacking-toolkit)](https://hub.docker.com/r/signedsecurity/web-hacking-toolkit/)
[![PRs Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)](http://makeapullrequest.com)


A multiplatform web hacking toolkit Docker image.

## Resources

* [Installation](#installation)
    * [Docker](#docker)
    * [Docker Compose](#docker-compose)
    * [Build from Source](#build-from-source)
* [GUI Support](#gui-support)
    * [Using SSH with X11 forwarding](#using-ssh-with-x11-forwarding)
* [Installed](#installed)
    * [Tools](#tools)
    * [Wordlists](#wordlists)

## Installation

### Docker

You can pull the Docker image from Docker Hub as below.

```bash
docker pull signedsecurity/web-hacking-toolkit
```

or:

```bash
docker run -it signedsecurity/web-hacking-toolkit /bin/bash
```

### Docker Compose

Docker-Compose can also be used.

```yaml
version: "3.9"

services:
    web-hacking-toolkit:
        image: signedsecurity/web-hacking-toolkit:latest
        container_name: web-hacking-toolkit
        hostname: web-hacking-toolkit
        stdin_open: true
        ports:
            - "22:22"
        volumes:
            - ./data:/root/data
        restart: unless-stopped
```

### Build from Source

```bash
git clone https://github.com/signedsecurity/web-hacking-toolkit.git && \
cd web-hacking-toolkit && \
make build
```

## GUI Support

By default, no GUI tools can be run in a Docker container as no X11 server is available. To run them, you must change that. What is required to do so depends on your host machine. If you:

* run on Linux, you probably have X11
* run on Mac OS, you need Xquartz (`brew install Xquartz`)
* run on Windows, you have a problem

### Using SSH with X11 forwarding

Use X11 forwarding through SSH if you want to go this way. Run `start_ssh` inside the container to start the server, make sure you expose port 22 when starting the container: `docker run -p 127.0.0.1:22:22 ...`, then use `ssh -X ...` when connecting (the script prints the password).

## Installed
### Tools

| Interface | Name | Description |
| :-------: | :--- | :---------- |
| CLI | [Amass](https://github.com/OWASP/Amass) | In-depth Attack Surface Mapping and Asset Discovery |
| CLI | [anew](https://github.com/tomnomnom/anew) | A tool for adding new lines to files, skipping duplicates |
| CLI | [curl](https://github.com/curl/curl) | A command line tool and library for transferring data with URL syntax, supporting HTTP, HTTPS, FTP, FTPS, GOPHER, TFTP, SCP, SFTP, SMB, TELNET, DICT, LDAP, LDAPS, MQTT, FILE, IMAP, SMTP, POP3, RTSP and RTMP. libcurl offers a myriad of powerful features |
| CLI | [dnsx](https://github.com/projectdiscovery/dnsx) | dnsx is a fast and multi-purpose DNS toolkit allow to run multiple DNS queries of your choice with a list of user-supplied resolvers. |
| CLI | [ffuf](https://github.com/ffuf/ffuf) | Fast web fuzzer written in Go |
| CLI | [findomain](https://github.com/Edu4rdSHL/findomain) | The fastest and cross-platform subdomain enumerator, do not waste your time. |
| CLI | [httpx](https://github.com/projectdiscovery/httpx) | httpx is a fast and multi-purpose HTTP toolkit allow to run multiple probers using retryablehttp library, it is designed to maintain the result reliability with increased threads. |
| CLI | [naabu](https://github.com/projectdiscovery/naabu) | A fast port scanner written in go with focus on reliability and simplicity. Designed to be used in combination with other tools for attack surface discovery in bug bounties and pentests |
| CLI | [nmap](https://github.com/nmap/nmap) | Nmap - the Network Mapper. Github mirror of official SVN repository. |
| CLI | [sigurlfind3r](https://github.com/signedsecurity/sigurlfind3r) | A passive reconnaissance tool for known URLs discovery - it gathers a list of URLs passively using various online sources. |
| CLI | [sigurlscann3r](https://github.com/signedsecurity/sigurlscann3r) | A web application attack surface mapping tool. It takes in a list of urls then performs numerous probes |
| CLI | [subdomains.sh](https://github.com/enenumxela/subdomains.sh) | A wrapper around for subdomains gathering tools (amass, subfinder, findomain & sigsubfind3r) to increase gathering efficiency and automating the workflow. |
| CLI | [subfinder](https://github.com/projectdiscovery/subfinder) | Subfinder is a subdomain discovery tool that discovers valid subdomains for websites. Designed as a passive framework to be useful for bug bounties and safe for penetration testing. |
| CLI | [wuzz](https://github.com/asciimoo/wuzz) | Interactive cli tool for HTTP inspection |
### Wordlists

| Wordlist | Description |
| :------- | :---------- |
| [SecLists](https://github.com/danielmiessler/SecLists)  | SecLists is the security tester's companion. It's a collection of multiple types of lists used during security assessments, collected in one place. List types include usernames, passwords, URLs, sensitive data patterns, fuzzing payloads, web shells, and many more. |
| [jhaddix](https://gist.github.com/jhaddix) / [content_discovery_all.txt](https://gist.github.com/jhaddix/b80ea67d85c13206125806f0828f4d10) | a masterlist of content discovery URLs and files (used most commonly with gobuster) |
