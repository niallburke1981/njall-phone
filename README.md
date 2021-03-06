[![Requirements Status](https://requires.io/github/righettod/website-passive-reconnaissance/requirements.svg?branch=master)](https://requires.io/github/righettod/website-passive-reconnaissance/requirements/?branch=master) [![Known Vulnerabilities](https://snyk.io/test/github/righettod/website-passive-reconnaissance/badge.svg?targetFile=requirements.txt)](https://snyk.io/test/github/righettod/website-passive-reconnaissance?targetFile=requirements.txt) ![Test application running state](https://github.com/righettod/website-passive-reconnaissance/workflows/Test%20application%20running%20state/badge.svg)

# Objectives

Script to automate, when possible, the **passive reconnaissance** performed on a website prior to an assessment (no direct hit on the target). 

Also used to guide a reconnaissance phase by defining all steps (manual or automated) that must be mandatory performed.

# Requirements

Python >= 3.7

# Installation of dependencies

Use the following command:

```bash
$ pip install -r requirements.txt
```

# Update of the "requirements.txt" file

Use the following command to use [pipreqs](https://github.com/bndr/pipreqs):

```bash
$ pipreqs --force .
```

# Update TLD list caching of the module "tldextract"

Use the following command from [here](https://github.com/john-kurkowski/tldextract#note-about-caching):

```bash
$ tldextract --update
```

# API keys file

> The script assume that an API key binded to the free version of the API is used of each service.

API keys are expected to be provided within an **INI** file having the following structure:

```ini
[API_KEYS]
;See https://www.shodan.io/
shodan=xxx
;See https://www.hybrid-analysis.com
hybrid-analysis=xxx
;See https://www.virustotal.com
virustotal=xxx
;See https://intelx.io/
intelx=xxx
;See https://azure.microsoft.com/en-us/try/cognitive-services/?api=search-api-v7
azure-cognitive-services-bing-web-search=xxx
```

# Usage examples

```bash
$ python --version
Python 3.7.5

$ python website_passive_recon.py --help
usage: website_passive_recon.py [-h] -d DOMAIN_NAME [-a API_KEY_FILE] [-n NAME_SERVER] [-p HTTP_PROXY] [-s]

optional arguments:
  -h, --help       show this help message and exit
  -d DOMAIN_NAME   Domain to analyse.
                   Ex: excellium.lu
  -a API_KEY_FILE  Configuration INI file with all API keys.
                   Ex: conf.ini
  -n NAME_SERVER   Name server to use for the DNS query.
                   Ex: 8.8.8.8
  -p HTTP_PROXY    HTTP proxy to use for all HTTP call to differents services.
                   Ex: http://5.196.132.126:3128
  -s               Save the result of the Google/Bing Dork searching for
                   interesting files to the file 'filetype_dork_result.txt'.

$ python website_passive_recon.py -d excellium-services.com
...

$ python website_passive_recon.py -d excellium-services.com -n 8.8.8.8
...

$ python website_passive_recon.py -d excellium-services.com -a api_keys.ini
...

$ python website_passive_recon.py -d excellium-services.com -a api_keys.ini -n 8.8.8.8
...

$ python website_passive_recon.py -d excellium-services.com -a api_keys.ini -n 8.8.8.8 -p http://5.196.132.126:3128
...

$ python website_passive_recon.py -d excellium-services.com -a api_keys.ini -n 8.8.8.8 -p http://5.196.132.126:3128 -s
...
```
