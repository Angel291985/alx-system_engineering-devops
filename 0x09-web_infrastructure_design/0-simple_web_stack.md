# Simple Web Stack
![Simple web stack](https://github.com/Angel291985/alx-system_engineering-devops/blob/master/0x09-web_infrastructure_design/0-simple_web_stack.png)

## Description
This is a simple web infrastructure that hosts a website that is reachable via www.foobar.com. There are no firewalls or
SSL certificates for protecting the server's network. Each componet (database, application server) has to share the resources (CPU, RAM, and SSD) provided by the server.

## Specifics About This Infrastructure
> What is a server?
> A server is a computer hardware or software that provides services to other computers,which are usually referred to as
clients.
>
> What is the role of the Domain name?
> The role is to provide a human-friendly alias for an IP Address. For example, the domain name google.com is easier
to recognize and remember than 198.102. 434.8. . The IP address and domain name alias is mapped in the Domain Name System (DNS)
>
> What type of DNS record www is in www.foobar.com?
> www.foobar.com uses an **A record**. This can be checked by running dig www.foobar.com.
**Note**: the results might be different but for the infrastructure in this design, an **A record** is used.
Address Mapping record (A Record)--also known as a DNS host record, stores a hostname and its corresponding IPv4 address.
>
> What is the role of the web server?
> The web server is a software/hardware that accepts requests via HTTP or secure HTTP (HTTPS) and responds with the content of the requested resource or an error message.
>
> What is the role of the application server?
> It is to install, operate and host applications and associated services for end users, IT services and organizations anddelivery of high-end consumer or business applications
>
> What is the role of the database?
> It is to maintain a collection of organized information that can easily be accessed, managed and updated
>
> What the server uses to communicate with the client (computer of the user requesting the website).
> Communication between the client and the server occurs over the internet network through the TCP/IP protocol suite.

## Issues With This Infrastructure
> There are multiple SPOF (Single Point Of Failure) in this infrastructure.
> For example, if the MySQL database server is down, the entire site would be down.
>
> Downtime when maintenance needed.
> When we need to run some maintenance checks on any componet, they have to be put down or the server has to be turned off. Since there's only one server, the website would be experiencing a downtime.
>
> Cannot scale if there's too much incoming traffic.
> It would be hard to scale this infastructure because one server contains the required components. The server can quicly run out of resources or slow down when it starts receiving a lot of requests.
