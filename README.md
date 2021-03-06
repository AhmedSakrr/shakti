# shakti

#### Bind the shell to any http port | Remote controller | Shell Attached Kindly To Internet

<img width=100% src="https://media.giphy.com/media/3ohzdV0vtdPPMUniE0/giphy.gif"></img>


### ⮊ What?

This is a remote shell. It allow to send <b>unix</b> commands via the http protocol.

An interface will be accessible on the defined port, with some usefuls predefined commands. They are meant to be edited.

This interface allow to send shell commands and will echo the command result on the wanted ports.

Commands can be sent in loop. They can also be sent/called from a terminal with <b>w3m</b>

This program is a php shell script written in one file to keep it portable.


### ⮊ Why?

Allow to control devices in an easy way. Commands automation are then easy to manage.

As example, controls a <i>raspberry pi</i> directly via any browser on the local network.

There is no authentification. There is no keys to setup. 


### ⮊ NEWS!

The last version does NOT need to be run as supersuser. 

### ⮊ How?

Shell results are converted to html, then served with the php built-in server.

Commands are sent with ajax/javascript to the php file. 

The system need <b>aha</b> and <b>screen</b>.

    sudo apt install aha screen

The server act as a daemon, wait for commands, and can open ports on demand. 

    ./shakti

Default <b>port 707</b>, or pass the port with the  <b>-p</b> argument:

    ./shakti -p 8080
    
### ⮊ When?

Anytime when a remote controller with no security is desirable. 

This tool won't replace ssh, but allow to remotly simulate his behavior, in an easier setup way

If you need security, use ssh.

But if you don't, here is a one liner pipe runner:

    wget https://webdev23.github.io/shakti/shakti && chmod +x shakti && ./shakti -p 3838

### ⮊ Where?

Localhost, private networks, dev/hack environments, clusters.

Of course it can as well fully works on the public web, with just a little port forwarding.

The php built-in server can fall asleep after some times, to avoid wake up him in intervals with any command.


### ⮊ Usage? 

Just open with a browser the link given on launch.


### To run into termux android

We need to install some packages into termux.
Mostly aha isn't available into termux apt, so we need to complile with make/clang.
Here is <b>adb</b> commands to run from a computer, from a stock blank termux install to a full running <b>shakti</b>:

    adb shell input keyevent KEYCODE_WAKEUP && adb shell input text apt%supdate%s&&%sapt%supgrade && adb shell input keyevent 160
    adb shell input text apt%sinstall%swget%sgit%smake%sclang%sscreen%stermux-setup-storage%stermux-exec%stermux-api%s-y && adb shell input keyevent 160
    adb shell input text git%sclone%shttps://github.com/theZiz/aha.git && adb shell input keyevent 160
    adb shell input text cd%saha
    adb shell input text make
    adb shell input text make%sinstall
    adb shell input keyevent KEYCODE_WAKEUP  && adb shell am force-stop com.termux && adb shell monkey -p com.termux 1 
    adb shell input text wget%shttps://webdev23.github.io/shakti/shakti && adb shell input keyevent 160
    adb shell input text chmod%s+x%sshakti && adb shell input keyevent 160
    adb shell input text ./shakti%s-p%s8080 && adb shell input keyevent 160
   

### ⮊ Examples of uses? 

From the default port 707, open the port 3838 to echo the command <b>ls</b>

http://localhost:707/?cmd=ls&port=3838

Then open http://localhost:3838 

or http://localhost:3838/?cmd=ls&port=3838&live to see live refreshing results, every 1 seconds

The <b>&live</b> parameter, will refresh the page every second.

We can also use any browser tab reloader module.

From a terminal, using <a href="apt://w3m">w3m</a>

    w3m 'http://localhost:707/?cmd=ls&port=3000'

Will show <b>ls</b> result every second on this link: http://localhost:3000/?cmd=ls&port=3000&live 


### ⮊ Who?

Nico Krazhtest https://ponyhacks.com

