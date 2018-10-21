# Setting up Network Proxy through terminal
> 21/10/2018

- Switching the network proxy on and off is a long process in macos. You turn on and off a web proxy from `System Preferences > Network > Proxies`, by checking Web Proxy (HTTP) and designating the Web Proxy Server etc. and by clicking OK and then "Apply". This is way too many steps.
- Instead one can do it with a single terminal command, checkout `networksetup`.
- If you want to turn on Wi-Fi proxy, do the following
  ```bash
  networksetup -setsecurewebproxystate Wi-Fi on
  ```
- To save even more time, give an alias to `networksetup -setsecurewebproxystate Wi-Fi` (say `proxy`). So just `proxy on/off` should do the job.
- With the proxy on, I'm not able to access network in terminal (but works in browsers). If you find any way to bypass proxy in terminal, please PM.
