# Get all public targets via Chaos 

> Tools

## jq

```sh
wget https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64
```

## Save as publictargets.sh

> mousepad publictargets.sh

```sh
curl -sL https://chaos-data.projectdiscovery.io/index.json | jq -r '.[] | select(.bounty == true) | select(.platform | contains ("hackerone")) | .URL' | xargs -I@ sh -c 'wget @' 
for f in *.zip; do unzip -d "${f%*.zip}" "$f"; done 
rm -rf *.zip
```

> chmod +x publictargets.sh

# Usage
> ./publictargets.sh

## You can change the name from hackerone to bugcrowd, intigriti, etc


