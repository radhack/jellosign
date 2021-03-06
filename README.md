# java + hellosign = jellosign
When trying to figure out an API or a new piece of code, sometimes seeing it in action is the best way to learn how it works.

This project contains some JSPs that demonstrate how to use the official [HelloSign Java SDK](https://github.com/HelloFax/hellosign-java-sdk) to add document signing, requesting, and template creation to your website.

## Make it go!
To run this demo locally, you'll need [git](https://git-scm.com/), [maven](https://maven.apache.org/),  [java](http://www.oracle.com/technetwork/java/javase/downloads/index.html), and [ngrok](https://ngrok.com/).

1. Start ngrok to create a tunnel to your localhost, specifying a subdomain (replace <YOUR_SUBDOMAIN> with the subdomain of your choosing) and port 8080:

    ```
    ngrok http -subdomain=<YOUR_SUBDOMAIN> 8080
    ```

1. Create an [API app configuration](https://www.hellosign.com/oauth/createAppForm) and enter your app details:
    1. Associated domain name: `ngrok.io`
    1. Event callback url: `https://<YOUR_SUBDOMAIN>.ngrok.io/hello`
    1. (Optional) OAuth callback url: `https://<YOUR_SUBDOMAIN>.ngrok.io/oauthDemoCallback.jsp`

1. Fork, then clone this repository.

1. Copy [web.properties.sample](src/test/webapp/WEB-INF/web.properties.sample) to  `src/test/webapp/WEB-INF/web.properties`

1. Edit `web.properties` and enter your [HelloSign API key](https://www.hellosign.com/home/myAccount#api), API app client ID, and client secret (if you enabled OAuth).

1. Start a Jetty container using the maven command:

    ```
    mvn -Dorg.slf4j.simpleLogger.defaultLogLevel=debug jetty:run
    ```

1. Open a web browser and point it to: `http://<YOUR_SUBDOMAIN>.ngrok.io`

1. Go wild!

## Handling callback events
Take a look at  [ExampleCallbackServlet.java](src/test/java/com/hellosign/sdk/callback/ExampleCallbackServlet.java) to see an example of handling callback events in Java. This servlet will be initialized when jetty starts and is configured in [web.xml](src/test/webapp/WEB-INF/web.xml).

# License
```
The MIT License (MIT)

Copyright (c) 2015 hellosign.com

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
