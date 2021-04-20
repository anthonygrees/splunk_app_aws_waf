# Splunk App - AWS Web Application Firewall Logs
### Introduction
[AWS WAF](https://aws.amazon.com/waf/) is a web application firewall that helps protect your web applications or APIs against common web exploits and bots that may affect availability, compromise security, or consume excessive resources.  
  
### The Splunk App
This is a `demo` Splunk App to display the logs from AWS Web Application Firewall.  
  
### What the App looks like
The app is a demo application that can be extended for customer or partner needs.  
  
![WAF App](/images/waf.png)
  
### Get Data In (GDI)
Ingesting WAF Full Logs into Splunk is quick and easy.  
  
Step 1: Enable Splunk to receive Kinesis data via the [Splunk Add-on for AWS](https://splunkbase.splunk.com/app/1876/).  
```bash
select sourcetype=aws:waf
```
Detailed instructions can be found on [Splunk Docs](https://docs.splunk.com/Documentation/AddOns/released/AWS/Kinesis).
  
Step 2: Add these settings to `props.conf` of your Splunk Search Head(s) and Splunk HTTP Event Collector(s).  
```json
{code}
[aws:waf]
SHOULD_LINEMERGE = false
TIME_FORMAT = %s%Q
TIME_PREFIX = "timestamp":
KV_MODE = json
{code}
```
  
Step 3: Enable stream to Kinesis from WAF via the AWS Console.
  
![Enable Kinesis](/images/enable.png)
  
### Install It
Download the `aws-waf-app_001.tgz` file onto your Splunk Server and run the command:  
```bash
splunk install app /tmp/aws-codecommit-app_001.tgz -auth user:password
```  
  
## License and Author
  
* Author:: [Anthony Rees](<reesy@splunk.com>)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.