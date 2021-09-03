# ONE-LINE COMMANDs

## Using httpx
After Enumerating all Subdomains,

```sh
cat all-subdomain.txt | httpx -status-code --path .s3.amazonaws.com
```

## Using FFUF

```sh
ffuf -w all-subdomains.txt:FUZZ -u http://FUZZ.s3.amazonaws.com
```
------------------------------------------------------------------------------------------------------------------
> Methods
```sh
aws s3 ls s3://[bucket_name]
aws s3 cp [FILE] s3://[bucket_name]
aws s3 mv [FILE] s3://[bucket_name]
aws s3 rm s3://[bucket_name]/[FILE]
```

> Step 1
```sh
aws s3 ls s3://[bucket_name] --no-sign-request
```
-(AccessDenied)-


> Step 2

```sh
aws s3 ls s3://[bucket_name] --profile=xyz
```
```sh
aws s3 cp ~/[FILE] s3://[bucket_name] |  if status-code 403
```

> Final Step
```sh
aws s3 cp [FILE] s3://[bucket_name] --acl public-read
```

For more [info](https://medium.com/techiepedia/misconfigured-3-bucket-a-semi-opened-environment-9cfb9dee782d)
