Telecom Company Use Analysis
Telecom services now include fixed-network services (data retail, Internet retail,voice retail and wholesale) and mobile services. Fixed-data services includes all
dedicated/private line, packet and circuit-switched access services (for example,frame relay, asynchronous transfer mode, IP, Integrated Services Digital Network,
DSL, multichannel multipoint distribution service and satellite) retail revenue. No differentiation is made between the type of traffic or application carried by these
services. The telecom company which gives these kinds of services wants to analyze dataset about their service.
1. Telecom wants to see each service use type of customers and total number in each use type customers which accept a partner .
 ```sql
                   create table telecom2(id int,
					 gender varchar(300),
					 Partner varchar(300),
					 ServiceForPhone varchar(300),
					 ormoreLines varchar(300),
					 ServiceforInternet varchar(300),
					 Security varchar(300),
					 ProtectionforDevice varchar(300),
					 Support varchar(300),
					 UseType varchar(300),
					 MonthlyofCharges float,
					 TotalofCharges float)
select * from public.telecom2
select usetype,count(*) from public.telecom2 where partner='Yes' group by usetype
 ```

| usetype        | count |
|----------------|-------|
| One year       | 426   |
| Month-to-month | 648   |
| Two year       | 597   |
2. The company sees that some customers accept device protection but not accept security for the internet.So company wants to see the number of each
internet service type which customers do not accept security for internet but accept device protection.
```sql
select ServiceforInternet,count(*) from public.telecom2 where security='No' and ProtectionforDevice='Yes' group by ServiceforInternet
```

| serviceforinternet | count |
|--------------------|-------|
| DSL                | 211   |
| Fiber optic        | 443   |
3. Some customers use more than 2 lines for their internet use and communications. Company wants to see customers who have more than 2000$ total charges.
```sql
SELECT * FROM public.telecom2 WHERE ormorelines = 'Yes'  AND TotalofCharges>2000;
```

| id  | gender | partner | serviceforphone | ormorelines | serviceforinternet | security | protectionfordevice | support | usetype         | monthlyofcharges | totalofcharges |
|-----|--------|---------|-----------------|-------------|--------------------|----------|---------------------|---------|-----------------|------------------|----------------|
| 12  | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 100.35           | 5681.1         |
| 13  | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 103.7            | 5036.3         |
| 15  | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 113.25           | 7895.15        |
| 28  | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 90.25            | 6369.45        |
| 30  | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 96.35            | 6766.95        |
| 35  | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | Two year        | 99.9             | 7251.7         |
| 38  | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 106.35           | 3549.25        |
| 41  | Female | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | No      | Two year        | 69.2             | 4872.35        |
| 43  | Female | No      | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 79.85            | 4861.45        |
| 45  | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 84.5             | 3906.7         |
| 48  | Male   | No      | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | Two year        | 79.75            | 4217.8         |
| 49  | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 64.15            | 4254.1         |
| 50  | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 90.25            | 3838.75        |
| 56  | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 99.65            | 6311.2         |
| 57  | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 108.45           | 7076.35        |
| 59  | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 107.5            | 7853.7         |
| 60  | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 100.5            | 4707.1         |
| 61  | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 89.9             | 5450.7         |
| 66  | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | One year        | 78.9             | 3650.35        |
| 72  | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 111.6            | 7099           |
| 75  | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 110.5            | 6139.5         |
| 511 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Month-to-month  | 106.45           | 6300.15        |
| 513 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 105.45           | 5916.95        |
| 514 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Month-to-month  | 95               | 2852.4         |
| 515 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Month-to-month  | 104.8            | 4131.95        |
| 520 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 105.4            | 6989.45        |
| 522 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 85.5             | 4713.4         |
| 524 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 100.05           | 3480           |
| 526 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 115.75           | 8399.15        |
| 527 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 94.7             | 5430.35        |
| 529 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 99.9             | 5706.3         |
| 533 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 107.15           | 7379.8         |
| 536 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 81.55            | 5029.05        |
| 540 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 113.1            | 8248.5         |
| 547 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 105.05           | 6744.25        |
| 548 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 101.9            | 5265.5         |
| 550 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 110.3            | 7966.9         |
| 551 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 115.6            | 8220.4         |
| 554 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 80.35            | 2596.15        |
| 555 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | No      | One year        | 68.75            | 3808           |
| 560 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 107.25           | 6033.3         |
| 563 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Two year        | 99.5             | 5861.75        |
| 567 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | Two year        | 73.5             | 5357.75        |
| 568 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 100.25           | 3527.6         |
| 571 | Male   | No      | Yes             | Yes         | DSL                | No       | No                  | Yes     | Two year        | 59.6             | 2754           |
| 573 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | One year        | 100.3            | 5614.45        |
| 574 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Month-to-month  | 110.85           | 3204.4         |
| 576 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 98.05            | 3082.1         |
| 578 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 94.55            | 3365.4         |
| 588 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 99.15            | 7422.1         |
| 589 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 90.4             | 6668.05        |
| 590 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 111.9            | 8071.05        |
| 592 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | No      | Two year        | 83.5             | 5435           |
| 598 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | One year        | 90.35            | 4614.55        |
| 602 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | One year        | 74.25            | 4859.25        |
| 603 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 108.65           | 4903.2         |
| 604 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | One year        | 109.55           | 3608           |
| 605 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 86.65            | 6094.25        |
| 608 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 114.55           | 8306.05        |
| 609 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Month-to-month  | 105.25           | 6786.4         |
| 613  | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 109.8            | 4860.35        |
| 614  | Male   | No      | Yes             | Yes         | DSL                | No       | Yes                 | Yes     | Two year        | 69.5             | 3418.2         |
| 617  | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 102.85           | 6976.75        |
| 618  | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | Month-to-month  | 87.55            | 4884.85        |
| 621  | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 92.05            | 5755.8         |
| 627  | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 104.6            | 6819.45        |
| 628  | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 111.65           | 7943.45        |
| 629  | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 90.05            | 4547.25        |
| 630  | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Month-to-month  | 110.75           | 4687.9         |
| 631  | Female | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | No      | Month-to-month  | 55               | 2473.95        |
| 632  | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 89.85            | 6562.9         |
| 635  | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 105.5            | 6985.65        |
| 637  | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 70.9             | 4911.35        |
| 638  | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 104.55           | 5794.65        |
| 647  | Male   | Yes     | Yes             | Yes         | DSL                | No       | Yes                 | Yes     | One year        | 69.65            | 3442.15        |
| 656  | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 88.85            | 6132.7         |
| 663  | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | No      | Two year        | 69.55            | 4459.15        |
| 675  | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 110.35           | 7246.15        |
| 1623 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Two year        | 97.2             | 5129.45        |
| 1624 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | One year        | 98.25            | 5508.35       |
| 1628 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 90.05            | 2627.2         |
| 2216 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Month-to-month  | 108.95           | 7111.3         |
| 2217 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 89.9             | 5958.85        |
| 2222 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 101.15           | 3956.7         |
| 2223 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 89.95            | 2625.55        |
| 2228 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Two year        | 104.45           | 7349.35        |
| 2235 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | No      | One year        | 78.35            | 3211.2         |
| 2240 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 89.55            | 6448.85        |
| 2243 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 100.8            | 6690.75        |
| 2244 | Female | No      | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | One year        | 64.4             | 2088.75        |
| 2245 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 105.35           | 7240.65        |
| 2254 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 93.05            | 6735.05        |
| 2257 | Female | No      | Yes             | Yes         | DSL                | No       | Yes                 | Yes     | One year        | 80.55            | 4847.05        |
| 2261 | Female | Yes     | Yes             | Yes         | DSL                | No       | No                  | No      | Month-to-month  | 52.15            | 2583.75        |
| 2264 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 114.95           | 7711.25        |
| 2267 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 113.65           | 8124.2         |
| 2276 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Month-to-month  | 104.15           | 4495.65        |
| 2277 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Month-to-month  | 109.15           | 6941.2         |
| 2282 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 99.5             | 6822.15        |
| 2285 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Month-to-month  | 93.9             | 5029.2         |
| 2287 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 108.4            | 7318.2         |
| 2289 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 107.45           | 7576.7         |
| 2292 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 91.3             | 4965           |
| 2293 | Male   | Yes     | Yes             | Yes         | DSL                | No       | Yes                 | Yes     | Two year        | 85.95            | 6151.9         |
| 2297 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 110.35           | 5893.15        |
| 2298 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Two year        | 79.2             | 5420.65        |
| 2300 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 103.25           | 5037.55        |
| 2302 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 91.25            | 6589.6         |
| 2305 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 97.7             | 3410           |
| 2309 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Two year        | 90.45            | 5229.8         |
| 2313 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 104.3            | 4451.85        |
| 2314 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 93.25            | 6688.95        |
| 2315 | Male   | Yes     | Yes             | Yes         | DSL                | No       | No                  | Yes     | One year        | 73.45            | 2661.1         |
| 2318 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 100.5            | 7030.65        |
| 2320 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 89.4             | 5597.65        |
| 2321 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 95.45            | 6223.3         |
| 2323 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 98.6             | 2933.2         |
| 2326 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 109.15           | 7789.6         |
| 2328 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 102.05           | 3452.55        |
| 2329 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 94.7             | 5468.95        |
| 2333 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | Month-to-month  | 65.2             | 3687.85        |
| 2337 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 104.75           | 5510.65        |
| 2341 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 114.9            | 7843.55        |
| 2342 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | Month-to-month  | 106.4            | 3211.9         |
| 2346 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Two year        | 95.75            | 6849.4         |
| 2349 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 90.45            | 6565.85        |
| 2357 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | No      | One year        | 75.1             | 5064.45        |
| 2359 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | No      | Month-to-month  | 72.75            | 2447.45        |
| 2368 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 117.15           | 8529.5         |
| 2369 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 99.25            | 6549.45        |
| 2370 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 112.55           | 7806.5         |
| 2372 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 90.3             | 6287.3         |
| 2379 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 106.35           | 3520.75        |
| 2380 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 103.75           | 5969.95        |
| 2384 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 91.05            | 4370.75        |
| 2389 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | One year        | 85.45            | 6300.85        |
| 2393 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 103.7            | 3467           |
| 2394 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | One year        | 79.05            | 5552.5         |
| 2395 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 90.7             | 2835.5         |
| 2396 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 95               | 3591.25        |
| 2404 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 94.45            | 3923.8         |
| 2410 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 80.45            | 3398.9         |
| 2411 | Male   | No      | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 84.95            | 4984.85        |
| 2415 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 94.55            | 3640.45        |
| 2416 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 100.5            | 2673.45        |
| 2418 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 86.45            | 2401.05        |
| 2424 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 112.95           | 6465           |
| 2428 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 99.25            | 3777.15        |
| 2443 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 109.55           | 7887.25        |
| 2444 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 99.95            | 3186.65        |
| 2450 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 110.45           | 8058.85        |
| 2451 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 106.1            | 2847.4         |
| 2458 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 105.05           | 5163.3         |
| 2467 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 97.95            | 4917.9         |
| 2471 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 98.4             | 5149.5         |
| 2472 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 70.9             | 4677.1         |
| 2474 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 106.35           | 4849.1         |
| 2479 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | Two year        | 75.85            | 4261.2         |
| 2480 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 93.85            | 5574.75        |
| 2483 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Month-to-month  | 100.7            | 4541.2         |
| 2486 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 90.45            | 2509.25        |
| 2489 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | One year        | 78.45            | 5333.35        |
| 2490 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Two year        | 100.55           | 3895.35        |
| 2494 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 75.35            | 2636.05        |
| 2508 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 110.5            | 7069.25        |
| 2514 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 89.7             | 2187.55        |
| 2515 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 115.1            | 7334.05        |
| 2518 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 99.65            | 2404.85        |
| 2521 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 85.25            | 3132.75        |
| 2522 | Male   | Yes     | Yes             | Yes         | DSL                | No       | Yes                 | Yes     | One year        | 78.75            | 3942.45        |
| 2525 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | Two year        | 97.75            | 6991.6         |
| 2534 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | One year        | 107.2            | 7317.1         |
| 2535 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 92.2             | 6474.45        |
| 2537 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 113.4            | 8164.1         |
| 2540 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 111.95           | 7795.95        |
| 2556 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Month-to-month  | 84.55            | 3713.95        |
| 2559 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 115.55           | 8425.3         |
| 2560 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 93.7             | 4154.8         |
| 2561 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 99               | 7061.65        |
| 2563 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 105.95           | 2655.25        |
| 2566 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 91.55            | 5963.95        |
| 2567 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 95.75            | 5742.9         |
| 2570 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 94.05            | 2866.45        |
| 2574 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 95.65            | 3759.05        |
| 2580 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 101.3            | 2974.5         |
| 2591 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 100.6            | 5611.7         |
| 2594 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 107.65           | 7082.85        |
| 2595 | Female | Yes     | Yes             | Yes         | DSL                | No       | Yes                 | Yes     | Two year        | 80.45            | 5662.25        |
| 2597 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 109.6            | 7854.15        |
| 2601 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 98.65            | 7129.45        |
| 2602 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 111.45           | 7266.95        |
| 2603 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 114.9            | 8496.7         |
| 2604 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 100.55           | 2878.75        |
| 2606 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 104.35           | 3205.6         |
| 2609 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 105.55           | 6281.45        |
| 2614 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | One year        | 94.35            | 6341.45        |
| 2615 | Female | No      | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 91.35            | 6697.2         |
| 2619 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Month-to-month  | 110.45           | 3655.45        |
| 2625 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 86.4             | 4922.4         |
| 2630 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | Two year        | 84.65            | 5377.8         |
| 2633 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | One year        | 100.15           | 6643.5         |
| 2636 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 113              | 7987.6         |
| 2643 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 83.35            | 2757.85        |
| 2648 | Male   | No      | Yes             | Yes         | DSL                | Yes      | Yes                 | No      | Month-to-month  | 59.6             | 2094.9         |
| 2659 | Female | No      | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 86.45            | 5175.3         |
| 2663 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 109.15           | 6557.75        |
| 2664 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 94.95            | 5791.85        |
| 2667 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 115.05           | 8405           |
| 2670 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | One year        | 95.15            | 5000.05        |
| 2671 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 105.4            | 6713.2         |
| 2673 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 101.35           | 2317.1         |
| 2684 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 105.2            | 7386.05        |
| 2685 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 100.65           | 7334.05        |
| 2689 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 116.75           | 8277.05        |
| 2695 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | One year        | 81.4             | 4354.45        |
| 2697 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 87.95            | 6365.35        |
| 2699 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 96.35            | 3190.25        |
| 2714 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 95.1             | 5064.85        |
| 2717 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 92.65            | 6733           |
| 2730 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 106.65           | 5168.1         |
| 2731 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Month-to-month  | 108.25           | 6780.1         |
| 2735 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 72.95            | 3829.75        |
| 2736 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 89.45            | 5294.6         |
| 2737 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 104.65           | 6889.8         |
| 2739 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 101.15           | 6383.9         |
| 2742 | Male   | No      | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 68.75            | 4447.55        |
| 2749 | Male   | Yes     | Yes             | Yes         | DSL                | No       | Yes                 | No      | One year        | 77.2             | 2753.8         |
| 2757 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 84.45            | 5848.6         |
| 2764 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | No      | Month-to-month  | 67.6             | 2000.2         |
| 2766 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | One year        | 115              | 7396.15        |
| 2767 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Month-to-month  | 84.8             | 3958.85        |
| 2772 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | Two year        | 74               | 4868.4         |
| 2775 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | One year        | 60.05            | 3229.65        |
| 3068 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 96.4             | 4911.05        |
| 2782 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 85.4             | 3297           |
| 2783 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 94.1             | 4107.3         |
| 2785 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 108.9            | 2809.05        |
| 2788 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 85.45            | 6028.95        |
| 2789 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 88.95            | 2072.75        |
| 2790 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | Two year        | 109.65           | 5551.15        |
| 2796 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 89.8             | 4959.6         |
| 2801 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 106.05           | 6703.5         |
| 2802 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Month-to-month  | 104.9            | 3351.55        |
| 2806 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | No      | Two year        | 86.1             | 4890.5         |
| 2810 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 103.9            | 6767.1         |
| 2812 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 104.05           | 6890           |
| 2816 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 109.55           | 8165.1         |
| 2822 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Month-to-month  | 79.9             | 3326.2         |
| 2832 | Male   | Yes     | Yes             | Yes         | DSL                | No       | No                  | Yes     | One year        | 70.75            | 2921.75        |
| 2835 | Female | No      | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | One year        | 63.85            | 4174.35        |
| 2836 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 98.7             | 4920.55        |
| 2847 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 79.3             | 2015.8         |
| 2850 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 99               | 6017.9         |
| 2851 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 90.6             | 5817.45        |
| 2853 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 79.2             | 4765           |
| 2859 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 88.55            | 6306.5         |
| 2860 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 101.4            | 6841.05        |
| 2865 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 109.25           | 7082.5         |
| 2870 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 107.95           | 5969.85        |
| 2873 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 94.7             | 2362.1         |
| 2877 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 99.15            | 6010.05        |
| 2879 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 102.95           | 7101.5         |
| 2884 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 90.15            | 6716.45        |
| 2885 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 116.1            | 7839.85        |
| 2901 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Two year        | 95.1             | 6843.15        |
| 2912 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 93.5             | 2970.8         |
| 2926 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 116              | 8182.85        |
| 2931 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 105.35           | 3465.05        |
| 2932 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 113.6            | 6292.7         |
| 2936 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 102.65           | 4108.15        |
| 2937 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 92.85            | 5980.75        |
| 2938 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 97.75            | 5043.2         |
| 2941 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 97.95            | 7114.25        |
| 2946 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 80.75            | 4116.9         |
| 2948 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 99.8             | 4259.3         |
| 2953 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 105.85           | 2239.65        |
| 2959 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | Month-to-month  | 100.75           | 2793.55        |
| 2960 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 100.75           | 2095           |
| 2965 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 80               | 4242.35        |
| 2967 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 113.75           | 6561.25        |
| 2969 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 109.3            | 7337.55        |
| 2971 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 90.3             | 5194.05        |
| 2974 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 94.5             | 2659.4         |
| 2983 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 89.9             | 6457.15        |
| 2985 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 113.2            | 3914.05        |
| 2988 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 109.65           | 7880.25        |
| 2997 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 89.95            | 6143.15        |
| 3003 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 79.5             | 2180.55        |
| 3010 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 80.45            | 3162.65        |
| 3012 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | Two year        | 65.65            | 3566.7         |
| 3013 | Female | No      | Yes             | Yes         | DSL                | No       | No                  | No      | One year        | 71               | 2080.1         |
| 3014 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 89.2             | 4040.2         |
| 3023 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 89.7             | 6339.3         |
| 3033 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Two year        | 110.8            | 7553.6         |
| 3038 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 105.6            | 7112.15        |
| 3040 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 108.6            | 7690.9         |
| 3046 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 103.3            | 6518.35        |
| 3051 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 89.9             | 6342.7         |
| 3052 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | No      | Month-to-month  | 55.05            | 2030.75        |
| 3053 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 104.1            | 6700.05        |
| 3054 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 106.6            | 7244.7         |
| 3055 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 75.2             | 3678.3         |
| 3056 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | Two year        | 70.5             | 3486.65        |
| 3061 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 106.4            | 2483.5         |
| 3063 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 100.05           | 3810.55        |
| 3071 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 90.5             | 4318.35        |
| 3072 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | One year        | 79.4             | 4820.55        |
| 3074 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | No                  | No      | Month-to-month  | 59.45            | 2136.9         |
| 3075 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 105.7            | 7472.15        |
| 3082 | Male   | No      | Yes             | Yes         | DSL                | Yes      | No                  | Yes     | One year        | 59.9             | 3043.6         |
| 3100 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 94.45            | 5073.1         |
| 3101 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 79.8             | 4526.85        |
| 3107 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 113.65           | 8182.75        |
| 3111 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Two year        | 103.4            | 7372.65        |
| 3112 | Male   | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | Two year        | 100.55           | 7325.1         |
| 3113 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 95.4             | 3474.2         |
| 3117 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 107.9            | 7475.85        |
| 3119 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 85.95            | 2628.6         |
| 3129 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 95               | 6602.9         |
| 3131 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 78.45            | 5682.25        |
| 3135 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 99.55            | 3734.25        |
| 3137 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 109.1            | 4454.25        |
| 3163 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 90.7             | 3413.25        |
| 3170 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | One year        | 100.2            | 2688.45        |
| 3181 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 81.3             | 5129.3         |
| 3184 | Female | Yes     | Yes             | Yes         | DSL                | No       | Yes                 | Yes     | Two year        | 83.3             | 5894.5         |
| 3198 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 106              | 4178.65        |
| 3200 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 104.3            | 5278.15        |
| 3201 | Female | No      | Yes             | Yes         | DSL                | No       | No                  | Yes     | Two year        | 79.6             | 4024.2         |
| 3203 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 88.05            | 6520.8         |
| 3205 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 117.6            | 8308.9         |
| 3208 | Male   | Yes     | Yes             | Yes         | DSL                | No       | Yes                 | No      | One year        | 70.55            | 3420.5         |
| 3214 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | One year        | 79.6             | 3974.7         |
| 3215 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 80.25            | 3439           |
| 3220 | Male   | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 77.3             | 5498.2         |
| 3228 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 105.25           | 5576.3         |
| 3240 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | One year        | 106.55           | 5763.3         |
| 3247 | Female | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 111.6            | 8012.75        |
| 3251 | Female | No      | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 106.75           | 4056.75        |
| 3253 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | Month-to-month  | 104.5            | 3684.95        |
| 3255 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | Yes     | One year        | 110.6            | 7210.85        |
| 3262 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 87.45            | 2874.15        |
| 3278 | Female | Yes     | Yes             | Yes         | DSL                | No       | No                  | Yes     | Two year        | 79.4             | 5071.9         |
| 3282 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 102.5            | 6157.6         |
| 3284 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 84.9             | 3369.05        |
| 3286 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 95.45            | 3474.05        |
| 3289 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 88.5             | 3645.05        |
| 3295 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 80.2             | 5714.2         |
| 3297 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 84.35            | 3571.6         |
| 3299 | Male   | No      | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | One year        | 117.2            | 8035.95        |
| 3302 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 103.45           | 3066.45        |
| 3304 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 109.95           | 7634.25        |
| 3305 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 94.75            | 3653           |
| 3307 | Female | Yes     | Yes             | Yes         | DSL                | No       | No                  | Yes     | Two year        | 79.65            | 3870.3         |
| 3315 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 107.35           | 7051.95        |
| 3327 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 95.3             | 6273.4         |
| 3330 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 97.8             | 4913.3         |
| 6675 | Female | No      | Yes             | Yes         | DSL                | No       | No                  | Yes     | One year        | 70.7             | 2511.95        |
| 6676 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | No                  | No      | Month-to-month  | 94.3             | 3893.6         |
| 6682 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Two year        | 92.45            | 6460.55        |
| 6686 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 109.75           | 7758.9         |
| 6689 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | One year        | 112.35           | 7388.45        |
| 6690 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 94.3             | 3460.95        |
| 6692 | Female | No      | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Month-to-month  | 74.65            | 3090.65        |
| 6695 | Female | Yes     | Yes             | Yes         | DSL                | Yes      | Yes                 | Yes     | Two year        | 71.1             | 5224.95        |
| 6697 | Female | No      | Yes             | Yes         | DSL                | Yes      | Yes                 | No      | One year        | 79.3             | 2427.1         |
| 6700 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Two year        | 106.3            | 7565.35        |
| 6704 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | One year        | 106.15           | 6256.2         |
| 6709 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | One year        | 99.4             | 5059.75        |
| 6711 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | No                  | No      | Month-to-month  | 98.35            | 4889.2         |
| 6713 | Male   | No      | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 95.9             | 6503.2         |
| 6717 | Male   | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | No      | Month-to-month  | 100.6            | 5746.15        |
| 6720 | Male   | Yes     | Yes             | Yes         | DSL                | No       | Yes                 | Yes     | Two year        | 84.1             | 5979.7         |
| 6721 | Female | Yes     | Yes             | Yes         | DSL                | No       | No                  | Yes     | Two year        | 79.3             | 3902.45        |
| 6722 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | No      | One year        | 107.05           | 7142.5         |
| 6728 | Female | Yes     | Yes             | Yes         | Fiber optic        | Yes      | Yes                 | Yes     | Two year        | 115.15           | 8349.7         |
| 6732 | Female | No      | Yes             | Yes         | Fiber optic        | No       | No                  | Yes     | Month-to-month  | 89.55            | 2259.35        |
| 6737 | Female | Yes     | Yes             | Yes         | Fiber optic        | No       | Yes                 | Yes     | Two year        | 109.25           | 6841.4         |
