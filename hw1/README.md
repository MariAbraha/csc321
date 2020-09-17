# Layer 2: Datalink

1. How many different things are listed in the output of the arp -a command?
 The interface is listed first. The internet address, physical address and type are given for 11 different listings.

    Interface: 10.0.0.166 --- 0x7
     Internet Address      Physical Address      Type
     10.0.0.1              78-23-ae-6c-67-a7     dynamic
     10.0.0.169            8c-49-62-52-b2-60     dynamic
     10.0.0.189            3c-9b-d6-59-d6-2b     dynamic
     10.0.0.201            54-8c-a0-e6-43-70     dynamic
     10.0.0.255            ff-ff-ff-ff-ff-ff     static
     224.0.0.2             01-00-5e-00-00-02     static
     224.0.0.22            01-00-5e-00-00-16     static
     224.0.0.251           01-00-5e-00-00-fb     static
     224.0.0.252           01-00-5e-00-00-fc     static
     239.255.255.250       01-00-5e-7f-ff-fa     static
     255.255.255.255       ff-ff-ff-ff-ff-ff     static

2. What are the different devices connected to your home network? Can you identify what they are based on this information?

    In [1]: import netlayers

    In [2]: netlayers.arp_table()
    ---------------------------------------------------------------------------
    KeyError                                  Traceback (most recent call last)
    <ipython-input-2-01bf855f0c30> in <module>
    ----> 1 netlayers.arp_table()

    ~\documents\csc321\hw1\netlayers.py in arp_table()
        182         _.map(lambda i: (i['name'], i['ip'], i['mac'],
        183                          i['info'].get('company', ''))),
    --> 184         lambda items: zip(*items),
        185     )
        186     max_n, max_i, max_m, max_c = _.pipe(

    c:\users\mari\appdata\local\programs\python\python37-32\lib\site-packages\toolz\functoolz.py in pipe(data, *funcs)
        632     """
        633     for func in funcs:
    --> 634         data = func(data)
        635     return data
        636

    ~\documents\csc321\hw1\netlayers.py in <lambda>(items)
        182         _.map(lambda i: (i['name'], i['ip'], i['mac'],
        183                          i['info'].get('company', ''))),
    --> 184         lambda items: zip(*items),
        185     )
        186     max_n, max_i, max_m, max_c = _.pipe(

    ~\documents\csc321\hw1\netlayers.py in <lambda>(i)
        180     names, ips, macs, companies = _.pipe(
        181         arp_items,
    --> 182         _.map(lambda i: (i['name'], i['ip'], i['mac'],
        183                          i['info'].get('company', ''))),
        184         lambda items: zip(*items),

    KeyError: 'name'


# Layer 3: Network

What are the differences between the two commands?
 - pinging the localhost was faster than google
 - different IP addresses

ping google.com

    PS C:\Users\Mari\documents\csc321\hw1> ping google.com

    Pinging google.com [2607:f8b0:4000:803::200e] with 32 bytes of data:
    Reply from 2607:f8b0:4000:803::200e: time=160ms
    Reply from 2607:f8b0:4000:803::200e: time=73ms
    Reply from 2607:f8b0:4000:803::200e: time=85ms
    Reply from 2607:f8b0:4000:803::200e: time=100ms

    Ping statistics for 2607:f8b0:4000:803::200e:
        Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
    Approximate round trip times in milli-seconds:
        Minimum = 73ms, Maximum = 160ms, Average = 104ms

ping localhost

    PS C:\Users\Mari\documents\csc321\hw1> ping localhost

    Pinging DESKTOP-H60JHVG [::1] with 32 bytes of data:
    Reply from ::1: time<1ms
    Reply from ::1: time<1ms
    Reply from ::1: time<1ms
    Reply from ::1: time<1ms

    Ping statistics for ::1:
        Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
    Approximate round trip times in milli-seconds:
        Minimum = 0ms, Maximum = 0ms, Average = 0ms