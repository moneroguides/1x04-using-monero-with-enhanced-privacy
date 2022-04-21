# Getting to Grips with Monero - Using Monero With Enhanced Privacy

## Prerequisites:

* Feather wallet
* Monerujo wallet
* Mullvad credit
* Tor (Linux)

<hr/>

### INTRO

This is the last in this four part series on "Getting to grips with Monero".

In this video we're going to be exploring ways in which you can easily enhance your privacy as a Monero user. We'll be exploring a few different networking methods and account management practices.

Let's get into it.


### COIN CONTROL

To begin we want continue on from the last video and introduce some privacy enhancing account practices. We're going to start by introducing a new term: **ring signatures**. Ring signatures are one of the key features of the Monero ecosystem which aims to anonymise our transactions. To learn more have a look at the [Moneropedia entry](https://www.getmonero.org/resources/moneropedia/ringsignatures.html)

Ring signatures aren't perfect as they only provide plausible deniability. Attacks can exist where two or more colluding parties attempt to learn information about someone they transact with. They can do so by tracing transaction graphs and performing statistical tests. This type of attack is especially effective against those who engage in repeated, uniform transactions and also provide personally identifiable information.

We won't be going into much detail so if you want to learn more about the attacks available to bad actors, please watch the [breaking Monero series](https://www.youtube.com/playlist?list=PLsSYUeVwrHBnAUre2G_LYDsdo-tD0ov-y).

There are two simple things we can do to reduce the risk imposed by these kinds of attacks. The first is by reducing input mixing. Input mixing is where you use owned outputs with multiple origins to satisfy a new transaction. Mixing inputs increases the amount of information available to those who are interested and can once again be used in a statistic analysis. 

That moves us onto the second thing you can do, churning. Churning is the act of sending outputs to yourself. Churning increases the level of plausible deniability as each of those outputs will then be included in many more ring signatures than before. If you need to mix inputs the best thing to do is churn them before mixing.

The "Coins" tab in Feather is great for managing both of these practices. To churn, simply right click on one of your owned outputs and select "Sweep output". When the new window opens, select "Send to self (churn)". **When using the send to self function, Feather will send that output to your primary address.**

Another helpful feature of Feather wallet is the ability to freeze outputs. This is useful when you have multiple outputs from different sources in the same account. Freezing them prevents Feather from using them when generating new transactions. You'll notice that the avilable balance in the tool bar has changed to reflect this.

With these ideas in mind in addition to what was learnt in video three about account management, you now have a wide range of tools to increase your level of privacy when using the network.


### NETWORKING

So far, we have only shown you how to connect to your own node from within your LAN. But what if you want to spend Monero whilst out shopping in town or when you're on holiday? 

Generally speaking, connecting to different nodes for one off payments is fine for maintaining privacy, especially if you're using either Feather or Monerujo which both support The Onion Routing (Tor) Project. However there have been several warnings throughout this series, particularly with regards to our network traffic.

During the second video we covered the kind of information made available to both internet service providers (ISPs) and node operators. You should keep these things in mind when making decisions about your networking preferences.

If your state has banned the use of Monero or you don't trust your ISP, you may want to manage this exposure and obfuscate your interactions with the Monero blockchain. Connecting to your own node through Tor or a VPN is the best method for achieving this.

Although we are primarily focused on privacy, there may be technical reasons for using a VPN or Tor. For example, your ISP may limit the use of port forwarding or you may not be able to access your router in an administrative capacity.

Before we continue, it would be good to introduce two terms which you may not have come across before. They are [Clearnet](https://en.wikipedia.org/wiki/Clearnet_networking) and [Darknet](https://en.wikipedia.org/wiki/Darknet). These terms have a well established history and can be be simply summarised in the following ways:

* Clearnet - Publicly accessible Internet 
* Darknet - Internet that can only be accessed with specific software, configurations, or authorisation,

For those of you who followed the previous videos and were not able to host your own node; you are already using the Darknet via [Tor](https://www.torproject.org). Tor is a free and open-source software which increases anonymity and censorship resistance on the internet. If you are interested in learning more please visit the Tor project website.

In the next sections we'll be demonstrating how to configure our nodes to accept RPC's from outside our LAN. Firstly using Clearnet and then Darknet, which is aimed only at Linux users.

We have one more warning before diving in. Opening ports comes with some risk, although we didn't issue a warning for the P2P networking, we will for RPC's. The risk of opening ports is normally tightly bound to the application that is being run through that port. Although there are no known vulnerabilities in the RPC implementation, it doesn't mean that there aren't any. If you have concerns or problems with port forwarding, we'd recomend you host your node over Tor, which does not require you to do this.

### CONFIGURING YOUR NODE - CLEARNET

If you have no reason to obfuscate your interactions with the Monero blockchain (and your router supports it), all you need to do is add firewall rules to your router and the machine which hosts your node. The default port for RPC's is **18081**. If you haven't done so already, you should add them now using the guide from the second video; **Setting up your own node**.

You will then need to discover your external IP address, which can most easily be done by visiting 3rd party sites such as those of VPN providers like [Mullvad](https://mullvad.net). Once you have done this, you have all the information you need to connect to your node.

### USING A VPN - CLEARNET

Using a VPN is equivalent to changing your ISP and depending on the service, you may gain some privacy enhancing features. In the last video we bought a subscription to [Mullvad](https://mullvad.net), a privacy focused VPN provider based in Sweden. We specifically chose Mullvad because we are able to configure multiple ports for use with our daemons and we were able to maintain some privacy when buying the subscription. 

Let's get started by heading over to Mullvad's web page and selecting "[Get started](https://mullvad.net/en/account/#/create/)".

Unlike services from Nord et al. which require you to provide email addresses and other personally identifying details, Mullvad uses account numbers. To generate an account number we can simply click on the button provided.

Now that we have our number, it's time to add some credit to our account. As we already purchased some credit we can select the **voucher** option and enter the details there. The final thing to do is download the appropriate software for your OS and assign ports to your account. Don't forget to verify your donwloads, Mullvads public key along with their own guide can be found through the following [link](https://mullvad.net/en/help/verifying-signatures/) or by clicking "what is this?" on the downloads page.

As a VPN user the ports you have access to will be limited. The default ports for P2P connections (18080) and RPC's (18081) will therefore likely be unavailable. To continue, we need to assign ports to our account.

Once logged in, choose a location and then a city using the drop down menu. Now click on the settings icon and then select "Advanced". There are two types of tunnelling protocols available through Mullvad, [OpenVPN](https://en.wikipedia.org/wiki/OpenVPN) and [WireGuard](https://en.wikipedia.org/wiki/WireGuard). We suggest selecting WireGuard, but you are free to make your own choice. If you're interested in the differences, please start with the links bellow.

Next, head back to Mullvads website and navigate to your account page. Once here, select "Manage ports and WireGuard keys". If you set your app to use WireGuard like us, you'll see your key displayed here. Scroll down to the "Port forwarding" subheading, now select the city you chose within the app and either the WireGuard key, or "No Key" for those of you using OpenVPN. 

Mullvad offers us the ability to forward up to 5 ports. Click on the green button to add ports, do this at least twice.

As you can see a few items have appeared under "ACTIVE PORTS". Now that we have these ports it's time to head back to our **bitmonero.conf** and change the default ports. The options are labelled `p2p-bind-port=` and `rpc-bind-port=`, replace the numbers which follow with the numbers given to you by Mullvad. Be sure to make a note of which ports you add to each option. You should then restart your daemon for these settings to take effect.

Finally, you need to add rules in the firewalls of both your computer and router. Please follow the instructions from the second video: **Setting up your own node**.

To connect to your node from outside your LAN your wallet software will require the port for RPC's and the IP address. You should already know your port number; to find our new IP address we can use the drop down menu in the Mullvad app. The IP address you need will be labeled "out".

Be warned, depending on your configuration, these IP address may not be static and can change without warning. Be sure to check again if you are ever unable to access your node. In order to see how to add your node to Monerujo or Feather, please move on the the section called **Adding nodes to your wallet software**. 

If you've had any problems with this process please double check you have your port numbers entered and forwarded correctly before reaching out.

Now for the the Darknet approach.


### CONFIGURING YOUR NODE - DARKNET (LINUX)

Welcome to the dark side. 

In this section, we'll be helping Linux users set up a hidden service, aka an [onion service](https://community.torproject.org/onion-services/). Hidden services are a convenient method of sharing local services on the internet. This is achieved by routing the traffic through tor and securing it with a private and complex addresses, which can be further secured using [authorisation methods](https://community.torproject.org/onion-services/advanced/client-auth/).

Although Tor is significantly slower than the Clearnet alternative, it is much more private. Onion addresses are not publicly available and are extremely difficult to guess.

To continue with this part of the guide, you need to have Tor installed on the machine that hosts your node. Installation depends on your distribution and is not covered in this video. If you need help, please consult the [tor website](https://community.torproject.org/onion-services/setup/install/). After the installation process you should now have a dedicated service which starts with your machine each time. To check if it's running use the command `sudo systemctl status tor@default.service`. 

Use `Ctrl + C` to exit.

With Tor installed it's rather simple to set up a hidden service. The first thing you need to do is edit the Tor config file, which is typically located in the following directory: `/etc/tor/torrc`. If everything is well your status should show that it's active and running.

Using your favourite editor you need to add a few lines, which will define your new service. I'm going to use [vim](https://www.vim.org/) and to enter the editing window I will use the command `sudo vim /etc/tor/torrc`, once that's done I will add the following lines:

	HiddenServiceDir /var/lib/tor/monero-service/
	HiddenServicePort 18081 127.0.0.1:18081

Take note of the fact that the option **HiddenServicePort** is a redirect of the already existing service on your host PC. If you have changed the default port for RPC's then this line needs to change to reflect that. You can also change the port on Tor to something else as well.

We can now exit our editor, making sure to save our changes. For the changes to take effect we must restart Tor, which should now be running as a service. We can do this with the command: `sudo systemctl restart tor@default`

To ensure Tor has started correctly and the settings have taken effect once again use the command: `sudo systemctl status tor@default.service`. Once again, use `Ctrl + C` to exit.

All that's left is to find out the hidden service address which has been issued by Tor. To print this information to the terminal we can use the concatenate command, along with the correct file location. The full command should look like this: `sudo cat /var/lib/tor/monero-service/hostname`.

We now have all the information we need to connect to our node using Tor enabled wallets.


### ADDING NODES TO YOUR WALLET SOFTWARE

Now that we've done that let's take a look at Monerujo. Although at the time of making this video Monerujo is currently an Android only wallet, we're using it due to its simple Tor integration. Please note, that for the Tor functionality to be enabled you will also need to have [Orbot](https://guardianproject.info/apps/org.torproject.android/) installed.

In order to add your node to Monerujo, first click on the network options. Once on the node selection menu, you should see a + symbol in the bottom corner. Here we can enter our details. In the "Hostname" field you should enter your external IP address or onion address. Once you've done that you need to enter the port which has been assigned to RPCs.

You can name the node what ever you like and for now we will leave the "Username" and "Password" fields blank. With all of that information filled in we can now select test to make sure everything has been configured correctly. 

If you have entered an onion address, this process may not work initially. Press ok to save your settings and then head back to the main menu. Click on the symbol next to the node name, once that's initialised, you should now see a little onion symbol, this means you are now using Tor to route your traffic. You can use Tor to connect to either Clearnet or Darknet nodes, but bare in mind Tor is much slower.

The process for adding your node to Feather is fairly similar. Start by selecting "File" and the "Settings". Next, select the "Node" tab and then highlight "From custom list". You should then enter your IP or onion address followed by the port number.

Click "OK" when you're done and then double click on the node to connect to it. There you have it, you are now able to use your node from outside of your LAN.


### PASSWORD PROTECTION

As we've seen here, it's possible to secure your RPC server with usernames and passwords. With this in place only those with a given username and password will be able to interact with the server. To enable this, we need to head back to our `bitmonero.conf` once more.

The flag for adding a username and password pair is as follows: `rpc-login=username:password`. This flag, along with many others can be found via the [Monerodocs website](https://monerodocs.org/interacting/monerod-reference/) which you may remember from the second video. With that line added, you should now restart your node for the settings to take effect.

Adding a username and password can grant you a little peace of mind and helps to prevent others from abusing your server.

### WHAT NEXT?

In the last few videos we've covered a lot. Don't worry if it all still seems a bit strange, it will take some time and practice for this information to be digested in it's entirety.

Please use these videos as a reference point for any further learning. The complete scripts for these videos are hosted on the [Monero Guides](https://www.moneroguides.org) website and are packed full of links to further reading which we've referenced throughout these guides. For additional reading, both [Zero to Monero](https://www.getmonero.org/library/Zero-to-Monero-2-0-0.pdf) and [Mastering Monero](https://masteringmonero.com/) offer a great level of detail and are very valuable resources.

We want to close by thanking you for staying tuned. We hope you now have the tools to both start and continue your journey with Monero.

So from us here at Monero Guides we wish you the best of luck on your adventures and look forward to seeing you again in future installments.

~moneroguides
