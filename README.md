# Codepath_Unit-7-Project-WordPress-vs.-Kali
Codepath Cybersecurity Assigment Week 7
# Project 7 - WordPress Pen Testing

Time spent: 20 hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pen Testing Report

### 1. WordPress <= 4.2 - Unauthenticated Stored Cross-Site Scripting (XSS) CVE-2015-3440

- [ ] Summary: Attackers can post comments on posts with Cross-Site Scripting payload. In order for the attack to work the comment has to be 64KB size. 
  - Vulnerability types: XSS (side note: I noticed Wordpress has way too many XSS vulnerabilities)
  - Tested in version: 5.1.53 and 5.5.41.
  - Fixed in version: 4.2.1
- [ ] GIF Walkthrough: <img src="" alt="">
- [ ] Steps to recreate: You need to add the following while creating your comment "<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>". I generated some 64kb text with an online generator and followed the guide on https://klikki.fi/wordpress-4-2-core-stored-xss/
- [ ] Affected source code:
  - [Link 1] (https://wpscan.com/vulnerability/8051e64b-f73e-45ce-a853-02b8e425155b)
  
### 2. WordPress 2.5-4.6 - Authenticated Stored Cross-Site Scripting via Image Filename OVE-20160724-0018

- [ ] Summary: The admin has to be tricked or one needs to gain access to admin account so then an image with Cross-Site Scripting payload can be uploaded.
  - Vulnerability types: XSS
  - Tested in version: 4.5.3
  - Fixed in version: 4.2.10
- [ ] GIF Walkthrough: <img src="" alt="">
- [ ] Steps to recreate: Upload file with malicious Javascript code "cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg" and made a post. Followed this guide https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html
- [ ] Affected source code:
  - [Link 1] (https://wpscan.com/vulnerability/e84eaf3f-677a-465a-8f96-ea4cf074c980)

### 3. 4.0-4.7.2 - Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds 

- [ ] Summary: Embed youtube link on a post with Cross-Site Scripting payload, you have to access admin account or make the admin make a post with the modified embed link for a "youtube" video.
  - Vulnerability types: XSS
  - Tested in version: 
  - Fixed in version: 4.2.13
- [ ] GIF Walkthrough: <img src="" alt="">
- [ ] Steps to recreate: Create post and add [embed src='https:youtube.com/embed/12345/\x3csvg onload=alert(1)\x3e'[/embed]. I changed onload to onmouseover and posted it. After being posted anybody that passes their mouse over the "youtube" link gets an alert (1). Used this guide https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html
- [ ] Affected source code: 
  - [Link 1](https://wpscan.com/vulnerability/3ee54fc3-f4b4-4c35-8285-9d6719acecf0)

## Assets
<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>
cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg
[embed src='https:youtube.com/embed/12345/\x3csvg onload=alert(1)\x3e'[/embed]



## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html
- https://klikki.fi/wordpress-4-2-core-stored-xss/
- https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html
- https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html

GIFs created with  ...
ScreenToGif](https://www.screentogif.com/) for Windows

## Notes

Setting up Vagrant and Kali was very hard and consumed most of my time.

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
