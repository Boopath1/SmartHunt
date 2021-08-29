## Setting up DNSValidator and getting list of 50resolvers.txt

```sh
git clone https://github.com/vortexau/dnsvalidator.git

cd dnsvalidator

python3 setup.py install

dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 200 -o resolvers.txt

sort -R resolvers.txt | tail -n 50 > 50resolvers.txt
```

## Download Amass :

```sh
wget https://github.com/OWASP/Amass/releases/download/v3.13.4/amass_linux_amd64.zip
```
