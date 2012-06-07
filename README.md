#FeedHenry & Stackato on HP Cloud Services

## Overview

This app demonstraits deploying a FeedHenry application into the Stackato Sandbox.

Both the FeedHenry platform (https://hpcs.feedhenry.com) and the Stackato Sandbox (https://api.stackato.ddns.us) are running on the HP Cloud 

![](https://github.com/johnfriz/HP-Sencha-Demo/raw/stackato/docs/HomeView.png)

## Setup
1. Clone this app into the hpcs.feedhenry.com studio (See https://vimeo.com/42889556 for more info on how to clone the app) 
2. Install the FeedHenry command line client fhc - See https://vimeo.com/33966777
3. Use fhc to set the appropriate app properties to target stackato
  fhc update <APP GUID> nodejs.developmenttarget cloudfoundry
  fhc call /box/srv/1.1/ide/hpcs/app/setstagingconfig POST "{'guid':'<APP GUID>', config:{'livetarget':'cloudfoundry', 'cfurl':'https://api.stackato.ddns.us', 'cfuser':'<STACKATO USER>', 'cfpwd':'<STACKATO PASSWORD>'}}"
4. Use FeedHenry App Studio to stage the cloud code to stackato
5. Use FeedHenry App Studio to build the app client as a native binary & install on device
5. ssh to the staged app in stackato and tail the stdout.log file:
  stackato ssh <STAGED APP IDENTIFIER>
  tail -f /app/logs/stdout.log
6. The log file should update with new data as the app on device is being used