# plugin-flex-outbound-dialpad

This plugin is intended to demonstrate how to make outbound calls from twilio flex without having to do any custom work around call conferencing and monitoring.

This plugin uses a custom built backend system to facilitate creation of outbound calls using Twilio Programmable Voice. These calls are enqueued straight back to the agent that made the call. The backend system exposes a websocket to notify the front end client of changes to the call. This enables automated state management in the front end to ensure there is no competing with other tasks. As the calls are enqueued using Twiml, flex can accept the task reservation using reservation.conference() and the call from there is treated like any other call. Transfers and supervisor monitoring are enabled.


# screenshot

![alt text](https://raw.githubusercontent.com/jhunter-twilio/plugin-flex-outbound-dialpad/master/screenshot/dialpad.png)

# use

1. Create backend system by following the instructions provided 

2. Create a clone of this repository and update
  
3. run npm install
4. create your own public/appConfig.js based on the public/appConfig.example.js and include your own account number
5. run npm start

# in case you missed it

When setting up the backend in heroku or local, you must ensure you have setup a dedicated task router worfklow for outbound calls and set the workflow sid in the environment configuration.

Also, the plugin assumes an acitvity of "Busy" or "Offline" is configured for making the worker automatically unavailable, and it assumes activties "Idle" or "Available" are configured for automatically going available, if these are not worker activity states that are available, you can either add them or update the code to change to a different state.

# change log

v1.1 - added ringtone when dialing, DTMF tones while on a call and better state management.

- breaking change to url, must align with backend

v1.0 - initial release


# TODOs

1. improve styling to better match base palette
2. enhance state management so dialing and hanging up puts you back to starting state and not just "available"
