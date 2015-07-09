# Introduction #

android2cloud was written with the principle of being **open** driving it. I kept as much of the application decoupled from itself as I could. The Android application will ask you what server you want to use (it doesn't care whether it's App Engine or not), the Chrome extension will ask what server to use (it, likewise, doesn't care if you're on App Engine), and the server will return results to any client (you can actually run this all through your browser, though that's kind of pointless).

The project is divided into three different trees: app-engine, chrome, and android. I'm sure you can guess which tree belongs to which part.


# Android #

The Android app is very poorly documented right now (version 0.1a), and is a mess. I apologise; this is an early alpha release, and I just wanted to push the working code into the hands of anyone who wanted it. I'll be working to try and clean up the documentation and readability of the code in the future.

# App Engine #

The App Engine server is really a very simple piece of work. It is an OAuth provider that interfaces with the Chrome extension and the Android app. All it really needs is:

  * Support for OAuth
  * A /links/get that returns the latest link of the authenticated user (between "`<link>`" and "`</link>`", or redirects the user to a login
  * A /links/add that accepts a POST parameter of "link"

I've got a few other things floating around in there (a /links/all, and a GET method for links/add) but that's really all you need.

# Chrome #

The Chrome extension is also very simple. It asks for the server's /links/get page every fifteen seconds. If it finds that the link is different from the last opened one, it opens it in a new tab. If the link isn't between `<link>` and `</link>`, it assumes something went wrong (error message, server is down, etc.) and does nothing. It also lets you click the button in your toolbar to retrieve /links/get, and open it (regardless of whether or not it has been opened).

I'm sorry for the sparse documentation; I'll be working to improve it in the future.