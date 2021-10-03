# Get all public targets via Chaos 

- bounty: true


This command line helps to grep all public bounty programs


## Tool

> jq

```sh
wget https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64
```
- rename the file to jq

```sh
mv jq-linux64 jq

chmod +x jq
```

- move to bin

```sh
sudo mv jq /usr/local/bin
```


## Open mousepad & Save as publictargets.sh

> mousepad publictargets.sh

```sh
curl -sL https://chaos-data.projectdiscovery.io/index.json | jq -r '.[] | select(.bounty == true) | select(.platform | contains ("hackerone")) | .URL' | xargs -I@ sh -c 'wget @' 
for f in *.zip; do unzip -d "${f%*.zip}" "$f"; done 
rm -rf *.zip
```

### You can change the name from hackerone to bugcrowd, intigriti, etc

> chmod +x publictargets.sh

# Usage
> ./publictargets.sh




