# hideandpeek.pcap
35 points
>This site is another suspicious site you found in his Herbert's browser history.
>This is OwnForAll's second dump of some of Herbert's activity, can we use this?
>We've uploaded it here for your convenience.
## Solving it
Since it is a *.pcap* (packet capture) file we know to open it in [wireshark.](https://www.wireshark.org/)

![hideandpeek](https://github.com/DigiBrkr/csaw_hsf_qualifier_2017_hideandpeek.pcap_35/blob/master/screenshot1.PNG?raw=true)

Looking at the file we can tell it is an [http](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) transaction of some sort. Since http is [plain-text](https://en.wikipedia.org/wiki/Plain_text) just as in the previous problem, the first thing to try is `tcp contains flag` in the filter box. However, this time it turns up no results (I should also mention that http is also [tcp](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) that's why we use `tcp contains`).
After briefly looking over the pcap we see an interesting packet  
`GET /abcdefghijklmnop.qrs.tuv.png HTTP/1.1`
this is an http [`GET` request](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.3) for a `png` file and a file name of `abcdefghijklmnop.qrs.tuv.png` sticks out like a sore thumb, so lets pull the file out.
So to do that we go to `File -> Export Objects -> HTTP` and there we see the file, so to export it simply click `Save`. Then open it up in the image viewer of your choice.


![image2](https://github.com/DigiBrkr/csaw_hsf_qualifier_2017_hideandpeek.pcap_35/blob/master/abcdefghijklmnop.qrs.tuv%20-%20fixed.png?raw=true)

`flag{you_g0T_m3_r3dHand3d!!} `

