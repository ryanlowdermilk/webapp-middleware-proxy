![](http://i.imgur.com/GKYGYp1.png)

# webapp-middleware-proxy

A reverse-proxy powered by your production website. The rule-based proxy supports injecting, modifying and overwriting of content (HTML, JS and CSS), URL routing and caching atop of your production website! Create new mobile and desktop apps, powered by your website, without ever modifying your production website!

## Features
- Inject Javascript inline and/or via external files
- Override CSS inline and/or via external files
- Rewrite URLs
- Spoof User-Agent
- Anything (Not really, but a lot is possible!)

## Quick Installation
### Option 1: Microsoft Azure
- Create a new Azure Web App
- Clone this repo
- From your clone, edit web.config to replace 'contosotravel-proxy' with the CNAME for your new Azure Web app
- Upload, via FTP, applicationHost.xtd (to /site) and web.config (to /site/wwwwroot)
- Restart Azure Web App
- Navigate to your Azure Web app
- Yay! You have a reverse-proxy of the Azure Travel Website. You can now inject, overwrite and modify content without affecting production!

### Option 2: node.js (Coming Soon!)

### Option 3: IIS on Windows Server (Coming Soon!)
- Install IIS
- Install Application Request Routing 3.0 via [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) (WebPi)
- Using IIS Manager, create a 'New Website'
- In the new folder for the website, add the web.config file from this repo
- In IIS select the newly created website node
- In the Features Pane select URL Rewrite
- In the Actions Pane on the right hand side select "View Server Variables..."
- Select "Add..." to add a new server variable and add each of the following
    - HTTP_ACCEPT_ENCODING
    - HTTP_X_ORIGINAL_ACCEPT_ENCODING
    - HTTP_X_PROXY_HOST
    - HTTP_X_ROOT_DOMAIN
- After each server variable has been added Select the root server node in IIS
- In the Feature Pane double click Application Request Routing
- In the Actions Pane on the right select "Server Proxy Settings..."
- Ensure that "Enable proxy" is checked
- You now have a working reverse proxy to contosotravel.azurewebsites.net

### Option 4: IIS on Windows development workstation
- Install IIS
- Install Application Request Routing 3.0 via [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) (WebPi)
- Using IIS Manager, create a 'New Website'
- In the new folder for the website, add the web.config file from this repo
- Edit web.config to replace 'contosotravel-proxy' with the host name of your new Website
- BONUS: Modify the rules in the web.config file is easier using IIS Manager. Select the Website (left side) and use URL Rewrite component (right side).

## Configuration
The web-middleware-proxy is driven by the web.config file - a simple XML file. The web.config configures the URL Rewrite component in IIS - the main component which drivers the injection and modifying of content. It's worth noting that all of this modification happens BEFORE it reaches the end user!

The easiest way to configure and test the webapp-middleware-proxy is by using your development workstation and using IIS Manager to create and modify rules. See [Option 3](#option3).

## Special Thanks
A special "thank you" goes to [@TomChantler](https://twitter.com/tomchantler) for his initial work on using Azure Web Apps as a reverse-proxy. His early work is the reason this project exists. Thanks, Tom!



## Samples
* Removing Compatability mode from older websites
```xml
<outboundRules> 
    <clear />   
    <rule name="X-UA-Compatible" preCondition="_ResponseIsHtml" patternSyntax="ExactMatch">  
        <match filterByTags="None" pattern="&lt;meta http-equiv='X-UA-Compatible' content='IE=EmulateIE7' /&gt;" />  
        <action type="Rewrite" />    
    </rule>  
</outboundRules> 
```

* Adding a new CSS Style Sheet  
```xml
<outboundRules/>  
    <clear />     
    <rule name="_Style" preCondition="_ResponseIsHtml" patternSyntax="ExactMatch">    
        <match filterByTags="None" pattern="&lt;link href='app.css' rel='stylesheet' /&gt;" />
        <action type="Rewrite" value="&lt;link href='mystyle.css' rel='stylesheet' /&gt;" />
    </rule >  
</outboundRules >
```