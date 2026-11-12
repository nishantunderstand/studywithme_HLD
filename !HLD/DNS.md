https://www.youtube.com/watch?v=SbjQjkhmcEY


https://www.instagram.com/p/Dcsm8qli2dE/


--- 
DNS 
AnyCast


https://www.instagram.com/p/DeqBxEHST38/


Many people assume DNS is a single massive database containing every website’s IP address, but it is actually a global distributed hierarchy. When you type google.com, your computer first checks your browser’s cache and your operating system’s shared cache. If neither knows the address, your computer asks a recursive resolver provided by your internet provider. To locate an unknown domain, this resolver queries the Root servers at the top of the internet, which point it to the servers running the .com registry, which then redirect the request directly to Google’s authoritative name server.  
  
Google’s authoritative server holds the official records and hands back the exact IP address, allowing your browser to finally start its connection. Although querying multiple servers for a single website sounds slow, aggressive caching at every single layer ensures your resolver rarely needs to start from the top, resolving most web lookups in just a few milliseconds.



> If we going through so many server, Then why it is not slow
> Answer : Caching

Recursive Resolver 
Why Recursive  ? 
Just Like Recursion

```
www.google.com -> Browser Cache -> OS Cache -> WIFI Rounter -> DNS 
-> RecursiveResovler -> Root Server -> TLD Server -> AuthortiveServer
```


----

https://www.instagram.com/p/DcTLndyheCJ/


DNS (Domain Name System) converts human-readable domain names like "google.com" into IP addresses that computers use to communicate.  
  
Here’s how it works:  
  
1. You enter "google.com" in your browser.  
2. The DNS Resolver checks its cache.  
3. If the IP is not cached, it queries the Root DNS Server.  
4. The Root Server directs it to the ".com" TLD Server.  
5. The TLD Server points to the Authoritative DNS Server.  
6. The Authoritative Server returns the IP address.  
7. The Resolver sends the IP back to your browser.  
8. Your browser uses that IP to connect to the server.  
  
In simple terms:  
  
Domain Name → DNS Resolver → Root → TLD → Authoritative DNS → IP Address  
  
Think of DNS as the phonebook of the internet. It helps translate names into addresses that computers can understand.
