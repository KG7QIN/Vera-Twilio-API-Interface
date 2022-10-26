# Twilio.com API Interface

Vera - Twilio API Interface

This is a Vera 3 (UI5) plugin I wrote.  This code and accompanying documentation was originally published to the MIOS Trac SVN repo at: http://code.mios.com/trac/mios_twilio-api-iface

I have moved it here so that it can be with the other code/projects I have on Github.


**Issues**:  Please check the existing issues before submitting a new one-- duplicate issues will be closed without comment.   

**Pull requests**:  Please submit all PRs against the develop branch.  Include both a description and any instructions on what features you added/fixed in your PR.  


Original code posted: http://forum.micasaverde.com/index.php/topic,15499.msg117950.html#msg117950

Plugin available from the MiOS App store: [https://apps.mios.com/plugin.php?id=4076]

----

## You will need to register for an account at [http://www.twilio.com] in order to use this plugin.

----
## How to use 

This is plugin  will allow to you have your Vera call and say text, or send SMS messages using the Twilio.com Call and SMS APIs.  


These are mandatory items that you need to configure before you can use the plugin:
* Account SID - Your Twilio.com account SID
* Auth Token - Your Twilio.com account Authenrication Token
* Caller ID - Phone number authorized to make calls

These two items are optional (unless using the !CustomVoiceCall function):

* Custom MSG URL - URL that points to a custom TwiML creator
* Custom MSG Var Name - Custom Message variable passed in URL


There are three functions that you can use:

* InitiateVoiceCall
* SendSMSMessage
* CustomVoiceCall

The Twilio.com API's use what they have dubbed TwiML, which is an XML DTD that the API understands for passing it commands.


----


* InitiateVoiceCall will use the free twimlets.com/message TwiML generator to have Twilio's API speak the message you pass to the function.

(Note:  we will assume our plugin has an ID of 66 in the following examples.  Make sure you replace the 66 in the code below with the actual ID number of the plugin on your system)

Example:

    luup.call_action("urn:twilioapi-org:serviceId:TwilioInterface1", "InitiateVoiceCall",{ PhoneNumber= "555-555-1212", Message="Greetings from your Vera Home Automation System"}, 66)


* PhoneNumber = number of recipient

* SendSMSMessage will send an SMS using Twilio's API:


Example:

    luup.call_action("urn:twilioapi-org:serviceId:TwilioInterface1", "SendSMSMessage",{ PhoneNumber= "555-555-1212", Message="Greetings from your Vera Home Automation System"}, 66)


* PhoneNumber = number of recipient

* CustomVoiceCall will initiate a voice call, using the URL you specified in the Custom MSG URL by itself or with the Custom MSG Var Name config items.

Example:

    luup.call_action("urn:twilioapi-org:serviceId:TwilioInterface1", "CustomVoiceCall",{ PhoneNumber= "555-555-1212", Message="Hi there", MsgFlag=2}, 66)


* PhoneNumber = number of recipient
* MsgFlag = 1 to only use custom URL, 2 to use custom URL and message variable name


----

Twilio, TwiML, and OpenVBX are trademarks of Twilio, Inc.
