# README
This is my template dockerized PHP developement environment. It is very easy to switch to other PHP versions or add additional modules in the PHP-FPM. 

### Docker rootless mode
This setup can also run in docker rootless mode, though you need to jump through a couple of hoops because the XDebug inside the PHP-FPM container cannot 
reach the listening XDebug instance on 0.0.0.0:9003 due to namespace shizzle. You need to enter the same namespace as the `dockerd` instance to make it work.
```
nsenter -U --preserve-credentials -n -m -t $(cat $XDG_RUNTIME_DIR/docker.pid)
cd ~/location/of/your/repository
code --no-sandbox --user-data-dir /home/user/.vscode  .
```
You will get a couple of warnings from VS Code because it thinks you are running the whole thing as root, but you can safely ignore those since you are only a fake root ;)

## Happy coding and signing
