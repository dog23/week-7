# Project 7 - WordPress Pentesting

Time spent: **12** hours spent in total


## Pentesting Report

User Enumeration
  - [ ] Summary: WPscan enumerates users
    - Vulnerability types: User Enumeration
    - Tested in version: 4.2.2
    - Fixed in version: 
  - [ ] GIF Walkthrough: ![](https://i.imgur.com/ffo9OYX.gif)
  - [ ] Steps to recreate: run "wpscan --url http://wpdistillery.vm/ --enumerate u" on WPscan

  - [ ] Affected source code: https://github.com/WordPress/WordPress/blob/4.2-branch/wp-login.php
  
Same-Origin Method Execution (SOME)
  - [ ] Summary: WordPress 4.5.1 is vulnerable against a Same-Origin Method Execution (SOME) vulnerability that stems from an insecure URL sanitization process performed in the file plupload.flash.swf. The code in the file attempts to remove flashVars ¹ in case they have been set GET parameters but fails to do so, enabling XSS via ExternalInterface ².
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version:  4.2.8
  - [ ] GIF Walkthrough: <img src="https://i.imgur.com/ID8jnAo.gif" width="800">
  - [ ] Steps to recreate: Go to any post and paste 
  ```<button onclick="fire()">Click</button> <script> function fire() { open('javascript:alert(23)');}</script>```
  
  Alert 23 will pop up
  - [ ] Affected source code: 
   https://gist.github.com/cure53/09a81530a44f6b8173f545accc9ed07e
    
Legacy Theme Preview XSS
  - [ ] Summary: Cross-site scripting (XSS) vulnerability in the legacy theme preview implementation in wp-includes/theme.php in WordPress before 4.2.4 allows remote attackers to inject arbitrary web script or HTML via a crafted string.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.4
  - [ ] GIF Walkthrough: <img src="https://i.imgur.com/dwgnDan.gif" width="800">
  - [ ] Steps to recreate: 
  
    Comment on a post with this comment ```<a href='/wp-admin/' title=""             style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(23)//'>Test</a>```
  
  post comment
  
  alert 23 will show
  - [ ] Affected source code:
  https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5734
  
  Cross Site Scripting
  - [ ] Summary: Cross-site scripting (XSS) vulnerabilities in wp-includes/class-wp-theme.php in WordPress before 4.4.1 allow remote attackers to inject arbitrary web script or HTML via a (1) stylesheet name or (2) template name to wp-admin/customize.php.
    - XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.4.2
  - [ ] GIF Walkthrough: ![](https://i.imgur.com/tUCPLSZ.gif)
  - [ ] Steps to recreate: Go to any post 
  Post ```http://www.example.com/wp-admin/customize.php?theme=<svg onload=alert(40)>```
  Alert 40 will pop up.

  - [ ] Affected source code: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-1564
  

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2018] [Mark Carino]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
