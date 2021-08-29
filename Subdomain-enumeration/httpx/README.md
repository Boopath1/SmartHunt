# ONE-LINE COMMANDs

```sh
cat all-subdomains.txt | httpx -follow-redirects -status-code -threads 100 | tee httpx.txt
```
