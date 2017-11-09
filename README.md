# CodePath-Week-7-Project
# Project 7 - WordPress Pentesting

Time spent: 4 hours spent in total

> Objective: Find, analyze, recreate, and document 3 affecting an old version of WordPress

## Pentesting Report

1. (Required) Large File Upload Error XSS
  - [ ] Summary: When large files are uploaded, wordpress doesn't sanitize the name of the file, which allows hackers to delpoy malicious xss attacks.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.15
  - [ ] GIF Walkthrough: ![alt text](https://github.com/davjd/CodePath-Week-7-Project/blob/master/largefile.gif)
  - [ ] Steps to recreate: Download a file of size larger than 10mb. Rename it with an xss attack. Upload as a media file on wordpress. 
  - [ ] Affected source code: handlers.min.js 
    - [Link 1](https://hackerone.com/reports/203515)
2. (Required) Unauthenticated Stored Cross-Site Scripting
  - [ ] Summary: When a post is submitted with large text(64kb+), wordpress truncates it when uploading, allowing users to insert an xss attack.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: ![alt text](https://github.com/davjd/CodePath-Week-7-Project/blob/master/xss.gif)
  - [ ] Steps to recreate: Initialize a post. Insert lots of text(about 64kb worth of text). Insert an xss attack inside the text. Upload the post. View the post.
  - [ ] Affected source code:
    - [Link 2](https://klikki.fi/adv/wordpress2.html)
3. (Required) Authenticated Stored Cross-Site Scripting
  - [ ] Summary: Due to poor sanitizing methods in this version of wordpress, an xss attack can be inserted in a post.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: ![alt text](https://github.com/davjd/CodePath-Week-7-Project/blob/master/authenticated_stored_xss.gif)
  - [ ] Steps to recreate: Initialize a post. Insert an xss attack(has to be advance) as an admin. Upload the post. View the post.
  - [ ] Affected source code:
    - [Link 3](https://klikki.fi/adv/wordpress3.html)

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

The initial exploit that was required was pretty difficult to recreate, mainly because the instructions weren't clear enough. All the exploits required lots of patience, but it was pretty cool executing them :)

## License

    Copyright 2017 David Medina

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
