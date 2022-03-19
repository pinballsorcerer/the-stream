# 2022-03-18T18:20:00-07:00

## Agenda

* Write Twitch chatbot in Python

## Pre-Stream Setup

* Create new local user (previous one was in real name)
* Re-download and install VS Code
* Install Python extension
* Walk through tutorial https://code.visualstudio.com/docs/python/python-tutorial

## Chatbot

### What do we need?

* Instructions
  * https://dev.twitch.tv/docs/irc
* New Twitch account for the bot to chat as
  * BOT_USERNAME: Pinbot9000
  * CHANNEL_NAME: PinballSorcerer
  * OAUTH_TOKEN: ******
* We're not doing node, we're doing Python!
  * Need a Python library for IRC
  * Where do we find packages? pip
  * Looks promising: https://pypi.org/project/irc/
* Git repo (GitHub)
  * https://github.com/pinballsorcerer/pinbot9000
  * Cloned to local computer
* Created virtual Python environment
  * `py -3 -m venv .venv`
  * `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process`
  * `.venv\scripts\activate`
* Install `irc` package
  * `pip install irc`
  * `pip install pytest` (for the tests)
  * Ran `pytest` in the `tests` directory: all passed!
* Downloaded a sample client script to learn how this library works
  * https://github.com/jaraco/irc/blob/main/scripts/irccat.py
  * Set up debug config to step through the script and learn how it works
  * Needed to pass the password as fourth argument to `connect()`
  * Set up to read plaintext OAuth password from file (not in source control)
  * SSL endpoint did not work for me, only non-SSL on port 6667
  * Bot messages were not appearing
    * Updated chat privileges to be less restrictive
    * Bot messages appeared but only after refreshing chat
    * Sending messages from bot in Twitch browser appears immediately
      * In hindsight, should have tested the above first

### What to do next?

* Keep working on code: try to figure out what works
* Give up on IRC and use WebSockets?
* Script to set up our environment
* Write unit tests
* Make sure to reply PONG to server PING
