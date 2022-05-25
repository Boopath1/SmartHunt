# Effectively Hunt on Wordpress
------------------------------------------------------------------------------------------------------------------

You can install it from [here](https://github.com/wpscanteam/wpscan)

```sh
wpscan --url https://redacted.com -e vp --api-token <YOUR_API_TOKEN> --random-user-agent --ignore-main-redirect --force --disable-tls-checks
```

> You have to create an account on https://wpscan.com to get your free API-Token

- Sometimes, it is not necessary the wordpress has been hosted on the main site or on the root directory

## For Example

> It might have been hosted like this: 
- https://redacted.com/blog/wp-content or
- https://redacted.com/news/articles/wp-content

#### Most of the hackers only checks if wordpress is hosted on the main site or not, but we also have to check the potential paths

> To find such endpoints, we can use the tools [waybackurls](https://github.com/tomnomnom/waybackurls) and [httpx](https://github.com/projectdiscovery/httpx)

```sh
waybackurls redacted.com | grep "wp-content" | httpx — mc 200
```
------------------------------------------------------------------------------------------------------------------

#### Now once we have the specific endpoint we can again use wp-scan modifying the command like this

```sh
wpscan --url https://redacted.com/blog -e vp --api-token <YOUR-API-TOKEN> --random-user-agent --ignore-main-redirect --force --disable-tls-checks
```
> Sometimes it may show error that the tool cannot find wp-content directory. In such situation it is better to specify the directory and use command like this

```sh
wpscan --url https://redacted.com/news/artcile/wp-content --wp-content-dir -e vp --api-token YOUR_API_TOKEN --random-user-agent --ignore-main-redirect --force --disable-tls-checks
```
> The same way you can exploit vulnerable themes. All you need to do is to replace vp with vt in the wpscan command like this

```sh
wpscan --url https://redacted.com -e vt --api-token <YOUR_API_TOKEN> --random-user-agent --ignore-main-redirect --force --disable-tls-checks
```
- Please don’t completely trust wpscan because sometimes it fails detecting plugins/themes version
- Also, sometimes the tool may miss displaying some plugins/themes that are actually being used
- For these reasons, please check for view-source and search keyword “/plugins” and “/themes” in the source on different paths of the wordpress site
- Sometimes wpscan misses detecting some plugins and themes, This technique may help in such cases.

------------------------------------------------------------------------------------------------------------------

> In order to find <b> wp-content </b> directories even more efficiently, you can also use tools like [FFUF](https://github.com/ffuf/ffuf)
