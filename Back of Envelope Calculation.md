[[Alex Xu]]



https://bytebytego.com/courses/system-design-interview/back-of-the-envelope-estimation



https://www.youtube.com/watch?v=DwqTon7ZS_s


https://highscalability.com/google-pro-tip-use-back-of-the-envelope-calculations-to-choo/



https://www.linkedin.com/posts/rohit-prasad-kushwaha_systemdesign-backendengineering-scalability-share-7432988709064519680-18ex/


https://harshityadav.in/Notex/system-design/overview/


https://systemdesign.one/back-of-the-envelope/
---


# Power of Two (Data Size Basics)
Understanding data units is critical.  
• 1 Byte = 8 bits  
• 1 KB = 2¹⁰ bytes (1,024 bytes)  
• 1 MB = 2²⁰ bytes  
• 1 GB = 2³⁰ bytes  
• 1 TB = 2⁴⁰ bytes  
• 1 PB = 2⁵⁰ bytes

|Power|Approximate value|Full name|Short name|
|---|---|---|---|
|10|1 Thousand|1 Kilobyte|1 KB|
|20|1 Million|1 Megabyte|1 MB|
|30|1 Billion|1 Gigabyte|1 GB|
|40|1 Trillion|1 Terabyte|1 TB|
|50|1 Quadrillion|1 Petabyte|1 PB|

#  Latency Numbers Every Programmer Should Know
Time units:  
ns = nanosecond, µs = microsecond, ms = millisecond

• 1 ns = 10⁻⁹ sec  
• 1 µs = 10⁻⁶ sec  
• 1 ms = 10⁻³ sec


| Operation name                                | Time                    |
| --------------------------------------------- | ----------------------- |
| L1 cache reference                            | 0.5 ns                  |
| L2 cache reference                            | 7 ns                    |
| Disk seek                                     | 10,000,000 ns = 10 ms   |

Key insights:  
- ✔ Memory is fast  
- ✔ Disk is slow  
- ✔ Avoid disk seeks  
- ✔ Compress before sending over network  
- ✔ Cross-region communication is expensive


# Availability numbers
