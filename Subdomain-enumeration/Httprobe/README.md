# ONE-LINE COMMANDs

```sh
cat all-subdomains.txt | httprobe -c 50 -t 3000 -p  443,80 | tee -a httprobe.txt
```
