# How Does the Internet Work?

You probably use the Internet dozens of times each day without thinking much about it. You send a message, watch a video, order something online, or search for an answer. A few seconds later, the information you wanted appears on your screen.

It almost feels instant. Behind the scenes, your device is talking to computers that may be hundreds or even thousands of kilometers away.

So how does that happen?

## It starts with a network

A network is a group of computers and other devices that can communicate with each other.

Think about the devices in your home. Your computer, phone, tablet, smart TV, and printer are usually part of the same network. They connect through your home router, often using Wi-Fi, although some devices may use Ethernet cables instead.

Schools and offices also have their own networks. As long as the devices can exchange information, they are part of the same network.

Inside a network, devices send information back and forth through **switches**. A  network switch connects devices *within a local area network* and forwards information to and from the devices in that network.   

One network is useful, but it can only connect the devices inside it.

The Internet is much bigger. It connects millions of separate networks around the world.

Those networks are linked together by devices called **routers**. A router connects one network to another and forwards information between them. Your home network, for example, connects to your Internet Service Provider through a router. Your provider then connects you to millions of other networks around the world.

Together, those connected networks form the Internet.

No single computer runs the Internet. No central control room directs every message. Each network manages its own part of the system while cooperating with the others. That is one reason the Internet continues to work even when individual devices, cables, or entire networks go offline.

## The Internet and the Web are not the same thing

People often use the words _Internet_ and _Web_ as though they mean the same thing. They do not.

The Internet is the global network that connects computers together.

The World Wide Web (or "Web") is one of the services that runs on the Internet. Websites are part of the Web. Email, video calls, online games, and many messaging apps also use the Internet, even though they are not part of the Web.

This article focuses on the Web because that is what most people use every day.

## Names and addresses

If you tell someone to deliver a package without giving them an address, they would have no idea where to take it.

Computers need addresses for the same reason.

So every device connected to the Internet has an _IP address_. IP stands for _Internet Protocol_, and an IP address is a unique number that identifies a device on a network.

But people are much better at remembering names than long strings of numbers. That is why websites use _domain names_ such as [www.wikipedia.org](http://www.wikipedia.org) instead of asking you to remember their IP addresses.

When you type a website name into your browser, your computer still needs its IP address before it can connect.

## The Domain Name System (DNS)

The Domain Name System, usually called _DNS_, is the service that matches domain names with IP addresses.

Suppose you type [www.wikipedia.org](http://www.wikipedia.org) into your browser.

Your device first sends a request to a DNS server. A DNS server keeps records of domain names and the IP addresses they point to. It replies with the address your browser needs.

Your browser can now contact the correct computer.

This usually takes only a fraction of a second. Your device and your Internet provider also remember recent DNS lookups. This is called _caching_. Caching means keeping information for a short time so it can be used again without looking it up from scratch. That's why, if you visit the same website again a few minutes later, your browser can often find the address more quickly.

## Information travels in packets

When your browser asks for a web page, it does not send one giant block of data across the Internet.

Instead, the information is divided into many small pieces called **packets**.

Each packet carries a small part of the data along with information about where it came from and where it needs to go.

The website sends its reply the same way. The text, images, and other files that make up the page all travel as packets.

Packets rarely travel straight from your device to a website.

Along the way they pass through several routers. A router connects one network to another. It reads the destination IP address on each packet and decides where to send it next.

Think of each router as handling only the next step of the journey. One router passes the packet to another until it finally reaches the network where the website lives.

The reply follows the same idea on its way back to you.

## Protocols

A Windows laptop, an Android phone, a Mac, and a Linux server all work differently. Even so, they can exchange information because they follow the same communication rules.

Those rules are called **protocols**.

A protocol defines how devices exchange information so that every device understands what it receives.

The Internet relies on many protocols. Two of the most important are **IP** and **TCP**.

IP gives every packet a source address and a destination address. Routers use those addresses to move packets across the Internet.

TCP, which stands for _Transmission Control Protocol_, keeps track of all the packets that belong together. If one packet goes missing, TCP asks for another copy. When every packet has arrived, TCP puts them back into the correct order before handing the complete data to your browser.

## HTTP and HTTPS

Once your browser reaches a website, it needs a way (a protocol) to ask for the page you want.

It does that using HTTP, which stands for _Hypertext Transfer Protocol_. HTTP defines how a browser requests web pages and how a web server sends them back.

Today, almost every website uses **HTTPS** instead. The extra _S_ stands for _Secure_.

HTTPS encrypts the information that travels between your device and the website. **Encryption** turns readable information into coded data that only the intended sender and receiver can read.

Your browser also checks the website's **digital certificate**. This certificate helps confirm that you have connected to the real website instead of a fake clone. When you see the padlock beside a website address, your browser is telling you that this secure connection is in use.

## How Wi-Fi and mobile data fit in

Wi-Fi and mobile data do not replace the Internet. They are two different ways of reaching it.

When you use Wi-Fi, your device sends data to your wireless router. The router passes it to your Internet provider.

When you use mobile data, your phone sends information to the nearest cell tower. From there, your mobile provider carries the traffic into the Internet.

Once your data reaches your provider's network, the rest of the journey works the same way.

## What happens when you open a website?

Now let's put everything together.

When you type **[www.wikipedia.org](http://www.wikipedia.org)** into your browser and press **Enter**, your browser asks a DNS server for Wikipedia's IP address. 

After it receives the answer, it opens a secure HTTPS connection to Wikipedia's servers. 

Your browser then sends a request asking for the page.

That request is divided into packets.

Routers forward those packets across the Internet until they reach Wikipedia's network.

Wikipedia's servers prepare the page and send the response back as another stream of packets.

TCP checks that every packet has arrived and puts them back into the correct order.

Finally, your browser reads the page, downloads the images and other files it needs, and displays the finished website on your screen.

All of that usually happens in well under a second.
