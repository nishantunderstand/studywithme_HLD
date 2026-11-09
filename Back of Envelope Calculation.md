Back of Envelope Math
Back of Envelope Calculation
Capacity Planning


[[Alex Xu]]



https://bytebytego.com/courses/system-design-interview/back-of-the-envelope-estimation



https://www.youtube.com/watch?v=DwqTon7ZS_s


![[Back of Envelope Calculation.png]]


Seconds in a day : 24h * 60m * 60s => 8,64,000


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

| Power of 2 | Approximate value | Full name  | Short name |
| ---------- | ----------------- | ---------- | ---------- |
| 10         | 1 Thousand        | 1 Kilobyte | 1 KB       |
| 20         | 1 Million         | 1 Megabyte | 1 MB       |
| 30         | 1 Billion         | 1 Gigabyte | 1 GB       |
| 40         | 1 Trillion        | 1 Terabyte | 1 TB       |
| 50         | 1 Quadrillion     | 1 Petabyte | 1 PB       |

| Power of 10  | Approximate value | Full number           | Zeros |
| ------------ | ----------------- | --------------------- | ----- |
| 10³          | 1 Thousand        | 1,000                 | 3     |
| 10⁶          | 1 Million         | 1,000,000             | 6     |
| 10⁹          | 1 Billion         | 1,000,000,000         | 9     |
| 10¹²         | 1 Trillion        | 1,000,000,000,000     | 12    |
| 10¹⁵         | 1 Quadrillion     | 1,000,000,000,000,000 | 15    |

Every next level adds 3 zeros.

- Thousand → 3 zeros
- Million → 6 zeros
- Billion → 9 zeros
- Trillion → 12 zeros
- Quadrillion → 15 zeros




Multiplication table of 864:

| Calculation | Result |
| :---------: | :----: |
|   864 × 1   |  864   |
|   864 × 2   | 1,728  |
|   864 × 3   | 2,592  |
|   864 × 4   | 3,456  |
|   864 × 5   | 4,320  |
|   864 × 6   | 5,184  |
|   864 × 7   | 6,048  |
|   864 × 8   | 6,912  |
|   864 × 9   | 7,776  |
|  864 × 10   | 8,640  |
|  864 × 100  | 86,400 |


#  Latency Numbers Every Programmer Should Know
Time units:  
ns = nanosecond, µs = microsecond, ms = millisecond

• 1 ns = 10⁻⁹ sec  
• 1 µs = 10⁻⁶ sec  
• 1 ms = 10⁻³ sec


| Operation name     | Time                  |
| ------------------ | --------------------- |
| L1 cache reference | 0.5 ns                |
| L2 cache reference | 7 ns                  |
| Disk seek          | 10,000,000 ns = 10 ms |

Key insights:  
- ✔ Memory is fast  
- ✔ Disk is slow  
- ✔ Avoid disk seeks  
- ✔ Compress before sending over network  
- ✔ Cross-region communication is expensive



# Availability (The “Nines” Concept)

High availability is measured in percentages.  
• 99% → ~3.65 days downtime/year  
• 99.9% → ~8.76 hours/year  
• 99.99% → ~52 minutes/year  
• 99.999% → ~5 minutes/year



| Availability | Downtime per Year |
| ------------ | ----------------- |
| 99%          | ~3.65 days        |
| 99.9%        | ~8.76 hours       |
| 99.99%       | ~52 minutes       |
| 99.999%      | ~5 minutes        |
| 99.9999%     | ~30 seconds       |

More “9s” = More reliability = More cost.


---


https://www.youtube.com/watch?v=VBw703pjC3E


https://dev.to/ievolved/how-i-calculate-capacity-for-systems-design-3477

https://www.codementor.io/@robinpalotai/back-of-the-envelope-calculation-for-system-design-interviews-z4ljbsp5l

![[Screenshot (533).png]]

![[Screenshot (534).png]]

![[Screenshot (535).png]]

![[Screenshot (536).png]]