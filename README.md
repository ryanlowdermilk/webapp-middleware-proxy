![](http://i.imgur.com/GKYGYp1.png)

# webapp-middleware-proxy

A reverse-proxy powered by your production website. The rule-based proxy supports injecting, modifying and overwriting of content (HTML, JS and CSS), URL routing and caching atop of your production website! Create new mobile and desktop apps, powered by your website, without ever modifying your production website!

## Features
- Inject Javascript inline and/or via external files
- Override CSS inline and/or via external files
- Rewrite URLs e.g. http://site/products?category=mens&article=shirts to http://site.com/mens/shirts
- Anything (Not really, but a lot is possible!)

## Installation
### Option 1: Microsoft Azure
- Create a new Azure Web App
- Upload, via FTP, applicationHost.xtd (to root) and web.config (to /site/wwwwroot)
- Restart Azure Web App

### Option 2: node.js (Coming Soon!)
### Option 3: Local web server
- Using IIS Manager, create a 'New Website'
- In the new folder for the website, add the web.config file
- BONUS: You can add and modify the existing rules in the web.config using IIS Manager. Select the Website and use URL Rewrite component.
### Option 4: Development workstation
- Install IIS
- Install Application Request Routing 3.0 via [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) (WebPi)
- See Option 3
## Usage
### Basic Usage
### Advanced Usage
#### Creating new rules base one regular expressions

## Special Thanks
A special "thank you" goes to [@TomChantler](https://twitter.com/tomchantler) for his initial work on using Azure Web Apps as a reverse-proxy. His early work is the reason this project exists. Thanks, Tom!