# URL Utils

Utilities to share shortcut links to web pages between MS Windows and Linux:
* **url-open** -- Opens MS Windows .url shortcuts in Linux, using the default web browser.
* **webloc-open** -- Opens Apple .webloc shortcuts in Linux, using the default web browser.
* **link2url** -- Converts Linux Desktop links into MS Windows .url shortcuts.

## Installation
* Make the files executable:
~~~bash
$  chmod u+x url-open webloc-open link2url
~~~
* Move the files to `~/bin` or `/usr/local/bin`
* Double-click on a .url shortcut file and associate it with `url-open`, checking the 'Always open with this program' box, if the option exists.
* Similarly, assocaite .webloc shortcuts with `webloc-open`.

## How it works
MS Windows .url shortcuts are text files with a list of `name = value` assignments. The URL name contains the URL to the web page.

Here's an example of the contents of a Windows .url file linking to google.com:
~~~
[InternetShortcut]
URL=https://www.google.com/?gws_rd=ssl
~~~

And, the equivalent Linux Desktop link file:
~~~
[Desktop Entry]
Encoding=UTF-8
Name=Link to https://www.google.com/?gws_rd=ssl
Type=Link
URL=https://www.google.com/?gws_rd=ssl
Icon=text-xml
~~~

The `url-open` script extracts the URL value from the shortcut file and then opens it. Since different Linux distributions can use different methods to open a URL in the default web browser, we attempt different common strategies.

The `webloc-open` works in a similar manner, but the URL in Apple .webloc files is extracted from within a `<string></string>` tag pair.

The `link2url` script replaces the first line in the Linux Desktop version to make it a Windows .url file.

## Usage
* `url-open` and `webloc-open` are used seamlessly from the Desktop. After associating the corresponding script with .url or .webloc files, the links should just work when double clicked.
* `link2url` is expected to be used from a terminal prompt:
~~~bash
$  link2url -h
Usage: link2url LINK_FILE [URL_FILE]
Converts a Linux Desktop link file into a Windows .url shortcut file
If no URL_FILE is specified, LINK_FILE.url is created
~~~

## License
MIT license. See the LICENSE file for details. 

