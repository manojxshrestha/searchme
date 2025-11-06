# Google Dorks for Bug Bounty Hunters

[![GitHub stars](https://img.shields.io/github/stars/manojxshrestha/searchme.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/manojxshrestha/searchme)
[![GitHub forks](https://img.shields.io/github/forks/manojxshrestha/searchme?style=for-the-badge&logo=github&logoColor=white)](https://github.com/manojxshrestha/searchme/network/members)
[![GitHub issues](https://img.shields.io/github/issues/manojxshrestha/searchme?style=for-the-badge&logo=github&logoColor=white)](https://github.com/manojxshrestha/searchme/issues)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/manojxshrestha/searchme?style=for-the-badge&logo=github&logoColor=white)](https://github.com/manojxshrestha/searchme/pulls)
[![GitHub license](https://img.shields.io/github/license/manojxshrestha/searchme?style=for-the-badge&logo=open-source-initiative&logoColor=white)](https://github.com/manojxshrestha/searchme/blob/main/LICENSE)

**A compact, practical, and responsibly-organized collection of Google Dorks aimed at reconnaissance and authorized bug bounty testing.**

> ⚠️ **Disclaimer:** This repository is intended for authorized security research only. Never use these dorks outside of programs where you have explicit permission. Misuse may violate laws and platform terms. Always follow program scope, responsible disclosure procedures, and the law.

---

## What this repo is

This repository collects curated Google dorks and search patterns to help security researchers quickly find information exposed on the public web. The list is organized by risk level — from **Critical** (high-impact leaks) to **Low** (informational reconnaissance) — so you can scan methodically during authorized engagements.

Use this repo to:

* Speed up reconnaissance in scoped, authorized targets.
* Learn how different types of information commonly leak on the public web.

---

## Quick start

1. **Fork & star** the repo if it’s useful.
2. Replace `example.com` with your target domain in the dork patterns.
3. Respect program scope, robots.txt, and usage policies.
4. Pair searches with automation tools or manual review to triage findings.

---

## How this README is organized

* **CRITICAL:** Immediate security risks — exposed credentials, private keys, tokens, sensitive config dumps.
* **HIGH:** Cloud leaks, backups, exposed DB dumps, S3 buckets, API secrets.
* **MEDIUM:** Admin panels, debug pages, phpinfo, error log disclosures.
* **LOW:** Subdomains, technology fingerprinting, staging/test hosts, public documentation.
* **Supplementary sections:** Login portals, code pastes, API docs, vuln-specific signatures, notes for scanners.

---

## Responsible usage & rules of engagement

1. **Authorization first** — Only test targets that explicitly allow your activity (bug bounty program, written permission, etc.).
2. **Limit impact** — Use non-invasive searches, avoid automated mass requests that could cause disruption.
3. **Respect privacy & law** — Don’t harvest or publish sensitive personal data. Follow the law and program policies.
4. **Report responsibly** — Follow the program’s disclosure guidelines; include reproduction steps and suggested remediation.

---

> The full list of dorks:

## CRITICAL DORKS - Immediate Security Risks

```
site:example.com "-----BEGIN RSA PRIVATE KEY-----" OR "-----BEGIN PRIVATE KEY-----" OR "-----BEGIN EC PRIVATE KEY-----"
```

```
site:example.com "aws_access_key_id" OR "aws_secret_access_key" OR "AKIA[0-9A-Z]{16}"
```

```
site:example.com "api_key" OR "api_secret" OR "secret_key" OR "private_key" filetype:env OR filetype:yml OR filetype:yaml
```

```
site:example.com "database_password" OR "db_pass" OR "mysql_password" OR "postgres_password"
```

```
site:example.com "ftp_password" OR "ftp_user" OR "sftp_password"
```

```
site:pastebin.com "example.com" "password" OR "secret" OR "key" OR "token"
```

```
site:github.com "example.com" "password" OR "secret" OR "key" OR "token" OR "api_key"
```

```
site:example.com "GITHUB_TOKEN" OR "GITLAB_TOKEN" OR "AZURE_CLIENT_SECRET"
```

```
site:example.com "stripe_key" OR "paypal_secret" OR "twilio_api_key"
```

```
site:example.com filetype:env "REDIS_PASSWORD" OR "ELASTIC_PASSWORD"
```

## HIGH SEVERITY - Critical Exposures

```
site:s3.amazonaws.com "example.com"
```

```
site:blob.core.windows.net "example.com"
```

```
site:googleapis.com "example.com"
```

```
site:drive.google.com "example.com"
```

```
site:docs.google.com "example.com"
```

```
site:dev.azure.com "example.com"
```

```
site:firebaseio.com "example.com"
```

```
site:digitaloceanspaces.com "example.com"
```

```
site:sharepoint.com "example.com"
```

```
site:s3-external-1.amazonaws.com "example.com"
```

```
site:example.com inurl:apidocs OR inurl:api-docs OR inurl:swagger OR inurl:openapi
```

```
site:example.com "swagger-ui" OR "swagger.json" OR "api.html" OR "graphql"
```

```
site:example.com "index of" OR "parent directory" OR "directory listing"
```

```
site:example.com ext:sql OR ext:dbf OR ext:mdb OR ext:backup OR ext:bak
```

```
site:example.com ext:log OR ext:txt OR ext:conf OR ext:config OR ext:ini
```

```
site:example.com filetype:pdf OR filetype:doc OR filetype:docx OR filetype:xls OR filetype:xlsx
```

```
site:example.com "robots.txt" intext:"Disallow:" -site:example.com.com
```

```
site:example.com inurl:.env OR inurl:config.json
```

```
site:example.com ext:sql | ext:dbf | ext:mdb
```

```
site:example.com ext:xml | ext:conf | ext:cnf | ext:reg | ext:inf | ext:rdp | ext:cfg
```

```
site:example.com ext:log
```

```
site:example.com ext:bkf | ext:bkp | ext:bak | ext:old | ext:backup
```

```
site:example.com ext:doc | ext:docx | ext:odt | ext:pdf | ext:rtf | ext:sxw
```

```
site:s3.dualstack.us-east-1.amazonaws.com "example.com"
```

```
site:dropbox.com/s "example.com"
```

```
site:docs.google.com inurl:"/d/" "example.com"
```

```
site:onedrive.live.com "example.com"
```

## MEDIUM SEVERITY - Important Findings

```
site:example.com inurl:admin OR inurl:login OR inurl:portal OR inurl:dashboard
```

```
site:example.com intitle:"admin" OR intitle:"login" OR intitle:"dashboard"
```

```
site:example.com "wp-admin" OR "administrator" OR "backend"
```

```
site:example.com inurl:cmd OR inurl:exec OR inurl:command OR inurl:run
```

```
site:example.com inurl:file OR inurl:document OR inurl:folder OR inurl:path
```

```
site:example.com inurl:url OR inurl:redirect OR inurl:return OR inurl:next
```

```
site:example.com inurl:id OR inurl:user OR inurl:account OR inurl:customer
```

```
site:example.com "config.php" OR "configuration.php" OR "settings.php"
```

```
site:example.com ".gitignore" OR ".htaccess" OR "web.config"
```

```
site:example.com "backup.zip" OR "dump.sql" OR "migration.sql"
```

```
site:example.com inurl:phpinfo OR intitle:"PHP Version"
```

```
site:example.com inurl:xdebug OR inurl:trace
```

```
site:example.com "error_log" OR "access_log" filetype:log
```

```
ext:php intitle:phpinfo "published by the PHP Group" site:example.com
```

```
inurl:readme | inurl:license | inurl:install | inurl:setup | inurl:config site:example.com
```

```
site:example.com "sitemap.xml" OR "sitemap_index.xml"
```

```
site:example.com filetype:json intext:"version"
```

```
site:example.com ext:php inurl:? -shop
```

```
site:example.com ext:log | ext:txt | ext:conf | ext:cnf | ext:ini | ext:env
```

```
site:example.com ext:asp | ext:aspx | ext:config | ext:ashx | ext:asmx
```

```
site:example.com ext:jsp | ext:jspx | ext:jsw | ext:jsv | ext:jspf
```

```
site:example.com intext:"powered by WordPress" OR "Joomla" OR "Drupal"
```

```
site:example.com "X-Powered-By: ASP.NET" OR "Server: Apache"
```

## LOW SEVERITY - Information Gathering

```
site:*.example.com -www -shop -mail
```

```
site:*.example.com inurl:dev OR inurl:test OR inurl:staging OR inurl:qa
```

```
site:example.com "node_modules" OR "bower_components" OR "vendor"
```

```
site:example.com "package.json" OR "composer.json" OR "requirements.txt"
```

```
site:example.com "Dockerfile" OR "docker-compose.yml"
```

```
site:example.com intitle:"index of" ext:sql OR ext:xls OR ext:xml OR ext:json OR ext:csv
```

```
site:example.com "contact" OR "about" OR "team" OR "careers"
```

```
site:example.com inurl:changelog OR inurl:release-notes
```

```
site:example.com filetype:txt intext:"powered by"
```

```
site:example.com inurl:readme.md OR inurl:INSTALL.txt
```

```
site:example.com inurl:conf | inurl:env | inurl:cgi | inurl:bin | inurl:etc | inurl:root | inurl:sql | inurl:backup | inurl:admin | inurl:php
```

## LOGIN PAGES & PORTALS

```
inurl:signup | inurl:register site:example.com
```

```
intext:"Create an account" | intext:"register account" | intext:"sign up" site:example.com
```

```
inurl:login | inurl:portal | inurl:sign-in | inurl:dashboard | inurl:/admin/ site:example.com
```

```
inurl:*admin | login | inurl:.php | .asp site:example.com
```

```
intitle:"admin login" site:example.com
```

```
inurl:console/login.jsp site:example.com
```

```
inurl:wp-admin site:example.com
```

```
site:example.com inurl:auth OR inurl:oauth
```

```
inurl:login | inurl:signin | intitle:login | intitle:signin | inurl:secure site:example.com
```

## EXPOSED FILES & CONFIGURATIONS

```
site:example.com ext:sql | ext:dbf | ext:mdb
```

```
site:example.com ext:xml | ext:conf | ext:cnf | ext:reg | ext:inf | ext:rdp | ext:cfg
```

```
site:example.com ext:log
```

```
site:example.com ext:bkf | ext:bkp | ext:bak | ext:old | ext:backup
```

```
site:example.com ext:doc | ext:docx | ext:odt | ext:pdf | ext:rtf | ext:sxw
```

```
ext:php intitle:phpinfo "published by the PHP Group" site:example.com
```

```
inurl:readme | inurl:license | inurl:install | inurl:setup | inurl:config site:example.com
```

```
site:example.com "sitemap.xml" OR "sitemap_index.xml"
```

```
site:example.com filetype:json intext:"version"
```

```
site:example.com ext:txt | ext:pdf | ext:xml | ext:xls | ext:xlsx | ext:ppt | ext:pptx | ext:doc | ext:docx intext:“confidential” | intext:“Not for Public Release” | intext:”internal use only” | intext:“do not distribute”
```

```
site:example.com ext:log | ext:txt | ext:conf | ext:cnf | ext:ini | ext:env | ext:sh | ext:bak | ext:backup | ext:swp | ext:old | ext:~ | ext:git | ext:svn | ext:htpasswd | ext:htaccess | ext:json
```

## VULNERABILITY SPECIFIC DORKS

```
inurl:cmd | inurl:exec= | inurl:query= | inurl:code= | inurl:do= | inurl:run= site:example.com
```

```
inurl:include | inurl:dir | inurl:detail= | inurl:file= | inurl:folder= site:example.com
```

```
inurl:http | inurl:url= | inurl:path= | inurl:dest= | inurl:html= site:example.com
```

```
inurl:id= | inurl:pid= | inurl:category= | inurl:cat= | inurl:action= site:example.com
```

```
inurl:url= | inurl:return= | inurl:next= | inurl:redirect= | inurl:redir= site:example.com
```

```
site:example.com inurl:search?q= OR inurl:query=
```

```
site:example.com inurl:upload OR inurl:filemanager
```

```
inurl:q= | inurl:s= | inurl:search= | inurl:query= | inurl:keyword= | inurl:lang= inurl:& site:example.com
```

```
inurl:url= | inurl:return= | inurl:next= | inurl:redirect= | inurl:redir= | inurl:ret= | inurl:r2= | inurl:page= inurl:& inurl:http site:example.com
```

```
inurl:id= | inurl:pid= | inurl:category= | inurl:cat= | inurl:action= | inurl:sid= | inurl:dir= inurl:& site:example.com
```

```
inurl:http | inurl:url= | inurl:path= | inurl:dest= | inurl:html= | inurl:data= | inurl:domain=  | inurl:page= inurl:& site:example.com
```

```
inurl:include | inurl:dir | inurl:detail= | inurl:file= | inurl:folder= | inurl:inc= | inurl:locate= | inurl:doc= | inurl:conf= inurl:& site:example.com
```

```
inurl:cmd | inurl:exec= | inurl:query= | inurl:code= | inurl:do= | inurl:run= | inurl:read=  | inurl:ping= inurl:& site:example.com
```

```
inurl:"error" | intitle:"exception" | intitle:"failure" | intitle:"server at" | inurl:exception | "database error" | "SQL syntax" | "undefined index" | "unhandled exception" | "stack trace" site:example.com
```

```
site:example.com inurl:email= | inurl:phone= | inurl:name= | inurl:user= inurl:&
```

## TECHNOLOGY & FRAMEWORK SPECIFIC

```
site:example.com ext:php inurl:? -shop
```

```
site:example.com ext:log | ext:txt | ext:conf | ext:cnf | ext:ini | ext:env
```

```
site:example.com ext:asp | ext:aspx | ext:config | ext:ashx | ext:asmx
```

```
site:example.com ext:jsp | ext:jspx | ext:jsw | ext:jsv | ext:jspf
```

```
site:example.com intext:"powered by WordPress" OR "Joomla" OR "Drupal"
```

```
site:example.com "X-Powered-By: ASP.NET" OR "Server: Apache"
```

```
site:example.com inurl:changelog OR inurl:release-notes
```

```
site:example.com filetype:txt intext:"powered by"
```

```
site:example.com inurl:readme.md OR inurl:INSTALL.txt
```

```
inurl:/wp-admin/admin-ajax.php site:example.com
```

```
intext:"Powered by" & intext:Drupal & inurl:user site:example.com
```

```
site:example.com inurl:/joomla/login
```

```
inurl:/content/usergenerated | inurl:/content/dam | inurl:/jcr:content | inurl:/libs/granite | inurl:/etc/clientlibs | inurl:/content/geometrixx | inurl:/bin/wcm | inurl:/crx/de site:example.com
```

```
site:jfrog.io "example.com"
```

## API & ENDPOINTS

```
site:example.com inurl:apidocs | inurl:api-docs | inurl:swagger | inurl:api-explorer | inurl:redoc | inurl:openapi | intitle:"Swagger UI"
```

```
site:example.com inurl:api | site:example.com/rest | site:example.com/v1 | site:example.com/v2 | site:example.com/v3
```

```
site:example.com inurl:upload intext:"choose file" | intext:"select file" | intext:"upload PDF"
```

## TEST ENVIRONMENTS & STAGING

```
site:example.com inurl:test | inurl:env | inurl:dev | inurl:staging | inurl:sandbox | inurl:debug | inurl:temp | inurl:internal | inurl:demo
```

```
site:*.example.com inurl:dev OR inurl:test OR inurl:staging OR inurl:qa
```

## CODE LEAKS & PASTES

```
site:pastebin.com "example.com"
```

```
site:jsfiddle.net "example.com"
```

```
site:codebeautify.org "example.com"
```

```
site:codepen.io "example.com"
```

```
site:groups.google.com "example.com"
```

```
site:openbugbounty.org inurl:reports intext:"example.com"
```

## DOMAIN-WIDE SEARCHES

```
site:example.com -www -shop -share -ir -mfa
```

## BUG BOUNTY & VDP DISCOVERY

```
"submit vulnerability report" | "powered by bugcrowd" | "powered by hackerone"
```

```
site:*/security.txt "bounty"
```

## SERVER & CMS SPECIFICS

```
site:example.com/server-status apache
```

**Remember to hack responsibly, stay within scope, and happy hunting.** 🧑🏻‍💻🥳
