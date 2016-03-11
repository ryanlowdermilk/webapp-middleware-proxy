![](http://i.imgur.com/GKYGYp1.png)

# webapp-middleware-proxy

A reverse-proxy powered by your production website. The rule-based proxy supports injecting, modifying and overwriting of content (HTML, JS and CSS), URL routing and caching atop of your production website! Create new mobile and desktop apps, powered by your website, without ever modifying your production website!

## Features
- Inject Javascript inline and/or via external files
- Override CSS inline and/or via external files
- Rewrite URLs e.g. http://site/products?category=mens&article=shirts to http://site.com/mens/shirts
- Anything (Not really, but a lot is possible!)

## Quick Installation
### Option 1: Microsoft Azure
- Create a new Azure Web App
- Upload, via FTP, applicationHost.xtd (to root) and web.config (to /site/wwwwroot)
- Restart Azure Web App

### Option 2: node.js (Coming Soon!)
<a name="option3"></a>
### Option 3: Local web server
- Using IIS Manager, create a 'New Website'
- In the new folder for the website, add the web.config file
- BONUS: You can add and modify the existing rules in the web.config using IIS Manager. Select the Website and use URL Rewrite component.
### Option 4: Development workstation
- Install IIS
- Install Application Request Routing 3.0 via [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) (WebPi)
- Complete the steps in [Option 3](#option3)
## Configuration
The web-middleware-proxy is driven by the web.config file. A simple XML file, the web.config configures the URL Rewrite component in IIS - the main component which allows injection and modifying of content, BEFORE it reaches the end user.

The easiest way to configure and test the webapp-middleware-proxy is by using your development workstation and using IIS Manager to create and modify rules. See [Option 3](#option3).

## Usage
### Basic Usage
### Advanced Usage
#### Creating new rules base one regular expressions


## Special Thanks
A special "thank you" goes to [@TomChantler](https://twitter.com/tomchantler) for his initial work on using Azure Web Apps as a reverse-proxy. His early work is the reason this project exists. Thanks, Tom!