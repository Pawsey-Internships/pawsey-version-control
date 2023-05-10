+++
title = "d. Proxy setup"
weight = 2
chapter = false
+++

You can change your configuration as many times as you want: use the
same commands to choose another editor or update your email 

This step probably won't be required unless you are on a restricted or specialised network.

> ## Proxy
>
> In some networks you need to use a
> [proxy](https://en.wikipedia.org/wiki/Proxy_server). If this is the case, you
> may also need to tell Git about the proxy:
>
> ```Bash
> $ git config --global http.proxy proxy-url
> $ git config --global https.proxy proxy-url
> ```
>
> To disable the proxy, use
>
> ```Bash
> $ git config --global --unset http.proxy
> $ git config --global --unset https.proxy
> ```
