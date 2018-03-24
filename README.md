# Project 7 - WordPress Pentesting

Time spent: **8** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. CVE-2016-7168: Authenticated Stored Cross-Site Scripting via Image Filename
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.5.3
    - Fixed in version: 4.6.1
  - [ ] GIF Walkthrough:  <img src="https://media.giphy.com/media/5T0joYC3ZSKCRlXWMO/giphy.gif" width="800">
  - [ ] Steps to recreate: 
      1. A WordPress admin uploads a malicious image file requested by a user this admin trusts or a popular malicious image that was spread via social media. ( In the Proof of Concept the file name cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg was used.) 
      2. An attacker can now determine if the file name with which the malicious file is available on the WordPress site. With this information he can spread the URL to end users and the WordPress admin.
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0)
    

2. CVE-2015-5734: Legacy Theme Preview Cross-Site Scripting (XSS)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2.3
    - Fixed in version: 4.2.4
  - [ ] GIF Walkthrough:  <img src="https://media.giphy.com/media/8UGFQgh0eVDaRReYXV/giphy.gif" width="800">
  - [ ] Steps to recreate: 
       1. A logged-in administrator visits one of the site's pages and clicks on a malicious link.
       2. The onclick=" handlers will get removed as it could be used to actually insert new tag attributes to the HTML link by sending a tag similar to the following in a post comment:

        <a href='/wp-admin/' title="onclick='" Title='" style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(1)//'>Test</a>
        
       3. This bypasses their filters that were in place to disallow javascript from being executed.

  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/changeset/33549)    


3. CVE-2015-5714: Authenticated Shortcode Tags Cross-Site Scripting (XSS)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.3.1
  - [ ] GIF Walkthrough:  <img src="https://media.giphy.com/media/fH6lvRN4OSETz2dvd9/giphy.gif" width="800">
  - [ ] Steps to recreate: 
       1. The remote authenticated user gains access to an account and creats a post/page or modifies the existing ones.
       2. Injects arbitrary web script or HTML by placing a crafted shortcode inside an HTML element such as the following and posts: 
       
         TEST!!![caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">Click me</a>
       
  - [ ] Affected source code: 
    - [Link 1](https://github.com/WordPress/WordPress/commit/f72b21af23da6b6d54208e5c1d65ececdaa109c8) 


4. CVE-2015-5622 & CVE-2015-5623: Authenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.1
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: <img src="https://media.giphy.com/media/2dmiGzQvCRopZNxlSl/giphy.gif" width="800">
  - [ ] Steps to recreate: 
       1. The remote authenticated user gains access to an account and creats a post/page or modifies the existing ones.
       2. Injects arbitrary web script or HTML by placing a crafted shortcode inside an HTML element such as the following and posts: 
       
        <a href="[caption code=">]</a><a title=" onmouseover=alert('XSS!')  ">More info...</a>
       
  - [ ] Affected source codes:
    - [Link 1](https://core.trac.wordpress.org/changeset/33359)
    - [Link 2](https://core.trac.wordpress.org/changeset/33357)

       

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- [Common Vulnerabilities and Exposures](https://cve.mitre.org/)

GIFs created with [GIPHY Capture](https://giphy.com/apps/giphycapture).

## Notes

  In challenge #1, it was difficult to create a walkthrough gif in 15 seconds or so since the Burp Intercept was on which makes loading the pages slower. 


## License

    Copyright [2018] [Mahshid Mehrayin]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
