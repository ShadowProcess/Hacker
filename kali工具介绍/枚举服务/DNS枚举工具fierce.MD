```text
fierce  /fɪrs/
adj. 凶猛的；猛烈的；暴躁的
n. （Fierce）（英）菲尔斯（人名）
```

fierce命令：
optional arguments:
  -h, --help            show this help message and exit
  --domain DOMAIN       domain name to test
  --connect             attempt HTTP connection to non-RFC 1918 hosts
  --wide                scan entire class c of discovered records
  --traverse TRAVERSE   scan IPs near discovered records, this won't enter adjacent class c's
  --search SEARCH [SEARCH ...]
                        filter on these domains when expanding lookup
  --range RANGE         scan an internal IP range, use cidr notation
  --delay DELAY         time to wait between lookups
  --subdomains SUBDOMAINS [SUBDOMAINS ...]
                        use these subdomains
  --subdomain-file SUBDOMAIN_FILE
                        use subdomains specified in this file (one per line)
  --dns-servers DNS_SERVERS [DNS_SERVERS ...]
                        use these dns servers for reverse lookups
  --dns-file DNS_FILE   use dns servers specified in this file for reverse lookups (one per line)
  --tcp                 use TCP instead of UDP
  
  
```shell script
(root💀kali)-[~]
└─# fierce --domain baidu.com
NS: ns7.baidu.com. ns3.baidu.com. ns4.baidu.com. ns2.baidu.com. dns.baidu.com.
SOA: dns.baidu.com. (110.242.68.134)
Zone: failure
Wildcard: failure
Found: 0.baidu.com. (180.149.144.203)
Found: 01.baidu.com. (180.101.49.147)
Found: 11.baidu.com. (220.181.57.55)
Found: 8.baidu.com. (220.181.33.181)
Found: a.baidu.com. (112.80.248.124)
Found: abc.baidu.com. (180.101.49.11)
Found: ac.baidu.com. (180.97.104.203)
Found: ad.baidu.com. (182.61.62.50)
Found: ae.baidu.com. (110.242.68.66)
Found: af.baidu.com. (157.255.77.113)
Found: ag.baidu.com. (202.108.23.198)
Found: ai.baidu.com. (115.231.186.230)
Found: antivirus.baidu.com. (103.235.46.69)
...
```  
输出的信息显示了baidu.com下所有的子域。从倒数第2行，可以看到总共找到133个条目。
执行以上命令后，输出的内容较多。但是由于篇幅的原因，部分内容使用省略号（……）取代。