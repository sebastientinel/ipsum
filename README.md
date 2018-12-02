![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2018-12-02)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
171.25.193.25|tor-exit5-readme.dfri.se|11
80.82.77.33|sky.census.shodan.io|10
35.0.127.52|tor-exit.eecs.umich.edu|10
80.82.77.139|dojo.census.shodan.io|10
51.254.47.198|ns3016508.ip-51-254-47.eu|10
119.97.170.34|34.170.97.119.broad.wh.hb.dynamic.163data.com.cn|9
199.19.226.226|-|9
89.234.157.254|marylou.nos-oignons.net|9
197.231.221.211|exit1.ipredator.se|9
111.40.120.33|-|9
5.188.10.76|-|9
80.67.172.162|algrothendieck.nos-oignons.net|9
185.104.120.2|exit02.brasshorncomms.uk|9
178.33.169.152|mobicite.dnsroute.fr|9
199.87.154.255|tor.les.net|9
128.199.140.214|exchangercoin.com|9
185.220.101.46|-|9
111.7.177.239|-|9
209.141.62.36|mx26.yongqianggd.com|9
192.160.102.170|ogopogo.relay.coldhak.com|9
211.226.176.47|-|9
66.70.217.179|tor.cusse.org|9
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|9
37.187.94.86|ns3035851.ip-37-187-94.eu|9
176.10.104.240|tor1e1.digitale-gesellschaft.ch|8
199.19.224.83|2wassecove.review|8
128.31.0.13|tor-exit.csail.mit.edu|8
51.15.53.83|83-53-15-51.rev.cloud.scaleway.com|8
209.141.53.94|earth.rickparrish.ca|8
94.142.242.84|tor-exit-1.zenger.nl|8
185.220.102.8|-|8
80.82.67.246|-|8
36.41.185.111|-|8
58.42.228.170|-|8
207.244.70.35|-|8
195.154.53.30|195-154-53-30.rev.poneytelecom.eu|8
171.25.193.235|tor-exit3-readme.dfri.se|8
66.242.170.49|mail.homesmart.phonesystems.bvn.net|8
178.73.215.171|178-73-215-171-static.glesys.net|8
58.218.213.156|-|8
65.19.167.131|-|8
209.141.50.57|voxility-filtered|8
186.207.162.26|bacfa21a.virtua.com.br|8
171.25.193.20|tor-exit0-readme.dfri.se|8
209.141.33.72|-|8
18.85.22.239|wholesomeserver.media.mit.edu|8
37.187.129.166|ns316491.ip-37-187-129.eu|8
185.104.120.4|exit03.brasshorncomms.uk|8
198.96.155.3|exit.tor.uwaterloo.ca|8
171.25.193.77|tor-exit1-readme.dfri.se|8
193.171.202.150|-|8
185.220.101.9|-|8
221.236.187.36|-|8
125.64.94.200|-|8
95.128.43.164|exit-1.fr.tor.aquaray.com|8
171.25.193.78|tor-exit4-readme.dfri.se|8
37.49.231.64|-|8
80.211.117.190|host190-117-211-80.serverdedicati.aruba.it|8
71.6.146.185|pirate.census.shodan.io|8
5.199.130.127|j061.jade.fastwebserver.de|8
188.0.133.241|241.133.0.188.static.ktc.kz|8
89.248.167.131|mason.census.shodan.io|8
69.60.21.172|staging.codeandtheory.com|8
192.160.102.164|snowfall.relay.coldhak.com|8
192.160.102.169|manipogo.relay.coldhak.com|8
113.106.92.60|-|8
117.36.157.226|-|8
185.165.168.229|-|8
185.220.101.21|-|8
166.70.207.2|this.is.a.tor.node.xmission.com|8
163.172.67.180|tor-exit-readme.memcpy.io|8
185.244.25.152|AWS-Panel|8
104.131.146.73|-|8
106.12.81.245|-|8
5.101.40.81|-|8
216.218.222.12|-|8
198.98.53.194|clientvps.com|8
122.2.223.242|122.2.223.242.static.pldt.net|8
