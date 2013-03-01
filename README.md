# ZeroBin 

Version: **0.18 Alpha**

**THIS IS ALPHA SOFTWARE - USE AT YOUR OWN RISKS**

ZeroBin is a minimalist, opensource online pastebin where the server 
has zero knowledge of pasted data. Data is encrypted/decrypted in the 
browser using 256 bits AES. 

![Zerobin Text Screenshot](https://raw.github.com/wiki/mattrude/ZeroBin/images/zerobin_present_textshare.png)

* _More information may be found in the project's [wiki](https://github.com/mattrude/ZeroBin/wiki), or within it's [changelog](https://github.com/mattrude/ZeroBin/blob/master/CHANGELOG.md#zerobin-version-history)._
* [Screen Shots](https://github.com/mattrude/ZeroBin/wiki/Screen-Shots) are also avalable, so you can see what ZeroBin looks like.

## Features

* Easy to install (put the files, open the page)
* No database required.
* FAST
* Brain-dead easy to use: Paste text, click “Send”, share the URL.
* Data compressed and encrypted in the browser before sending to server. Uses 256 bits AES.
* Server has zero knowledge of data being stored. Your data is safe even in case of server breach or seizure.1)
* Expiration: 10 minutes, 1 hour, 1 day, 1 month, 1 year, never or ”Burn after reading” (Destroyed when read).
* Syntax coloring for 54 languages (using [highlight.js](http://softwaremaniacs.org/soft/highlight/en/)), supporting mixing (html/css/javascript).
* Automatic conversion of URLs into clickable links (http, https, ftp and magnet).
* Search engines are blind regarding paste content.
* Single button to clone an existing paste.
* Rate limiting: 10 seconds between each paste.
* Size limiting: 2 Mb per paste (of compressed and encrypted data - cleartext data can be larger).
 
**Discussions:**

* You can enable discussion on each paste.
* Discussion is of course also encrypted/decrypted in the browser.
* Server cannot see comments content or nicknames.
* VisualHash on each post to identify IP addresses without revealing them. Same image = same IP. 2)
* With paste expiration, you can have ad-hoc short-lived discussion which will disappear in the void after expiration.
* Discussions cannot be indexed by search engines. Period.3)
* Send a link by email to a friend for private discussions which will leave no trace in your email box, will not be indexed by searchengines, will not be read by robots and will never be archived.
* Free software
* GitHub access to source code.

**Upcoming features:**

* Syntax highligting.
* Password protection.

## Requirements

**Server:** 

* php 5.2.6 or above.
* GD
* No database required.

**Client:**

* A modern, javascript-capable browser (See FAQ for list of supported browsers).

## Pros/Cons

### Benefits

* Low server requirements, easy installation.
* Benevolent server admins can provide a service which protects their users privacy: text sharing and discussions.
* User data is protected even in case of server breach or seizure.
* Server admins cannot pro-actively moderate documents and (hopefuly) be held liable because they have no knowledge of data being shared and there is no searchengine.
* There is no public feed of google-indexable content (Google will not index documents except if you leak the URL).
* Admins can still remove a document upon injunction or infringement notice… but have no way to tell if the same document has been posted again.
* No advertising.

### Drawbacks

* Won't work if javascript is disabled.
* Users still have to trust the server regarding the respect of their privacy. ZeroBin won't protect the users against malicious servers.
* Won't protect against Man-in-the-middle attacks (eg. javascript substitution)
* Shitty look in Internet Explorer (but who cares?)

## How does it work?

When **pasting a text into ZeroBin**:

![Zerobin Encryption](https://raw.github.com/wiki/mattrude/ZeroBin/images/zerobin_figure_encryption.png)

* You paste your text in the browser and click the “Send” button.
* A random 256 bits key is generated in the browser.
* Data is compressed and encrypted with AES using specialized javascript libraries.
* Encrypted data is sent to server and stored.
* The browser displays the final URL with the key.
* The key is never transmitted to the server, which therefore cannot decrypt data.

When **opening a ZeroBin URL**:

![zerobin decryption](https://raw.github.com/wiki/mattrude/ZeroBin/images/zerobin_figure_decryption.png)

* The browser requests encrypted data from the server
* The decryption key is in the anchor part of the URL (#…) which is never sent to server.
* Data is decrypted in the browser using the key and displayed.

### Sample URL

If you have a URL like: http://example.com/?7a5dd0979f712164#QdnCROuH9ebUXv3oBjBw3eOdb3y9p5nEAkUJZBxg=

* **7a5dd0979f712164** is the paste identifier.
* **QdnCROuH9ebUXv3oBjBw3eOdb3y9p5nEAkUJZBxg=** is the decryption key. It is never sent to the server.

## License

    Copyright (c) 2013 Sébastien SAUVAGE (sebsauvage.net)
    Copyright (c) 2013 Matt Rude (mattrude.com)

    This software is provided 'as-is', without any express or implied warranty.
    In no event will the authors be held liable for any damages arising from 
    the use of this software.

    Permission is granted to anyone to use this software for any purpose, 
    including commercial applications, and to alter it and redistribute it 
    freely, subject to the following restrictions:

    1. The origin of this software must not be misrepresented; you must 
       not claim that you wrote the original software. If you use this 
       software in a product, an acknowledgment in the product documentation
       would be appreciated but is not required.

    2. Altered source versions must be plainly marked as such, and must 
       not be misrepresented as being the original software.

    3. This notice may not be removed or altered from any source distribution.
