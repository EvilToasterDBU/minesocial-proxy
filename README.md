# Ready-to-use autlib-injector proxy
Just use [autlib-injector](https://github.com/yushijinhun/authlib-injector) with `minesocial.ml` authentication server.

Code: `java -javaagent:authlib-injector.jar=minesocial.ml -jar server.jar`

# Deployment
This service is built with [Cloudflare Workers](https://workers.cloudflare.com/).
If you want to deploy your own service instance, please follow the steps below:
1. Login to Cloudflare
2. Go to `Workers > Manage KV namespaces`, then create a KV namespace
3. Go to `Workers > Create a Worker`
4. Copy the content of [index.js](https://github.com/EvilToasterDBU/minesocial-proxy/blob/master/index.js), and paste it to `Script` window, then click `Save and Deploy`
5. Go back to the worker page, open `Settings` tab, click `Add binding`
    * Variable name: `KV_MINESOCIAL_PROXY`
    * KV namespace: the KV namespace you created in the 2nd step
6. Connect custom domain for your Cloudflare Account
7. Go to `your_domine > Workers > Add route`
8. Select your worker and enter your domain address, save it.
9. Go to `your_domine > Rules > Create Page Rule`
10. Create 3 Rule for forward urls like this:
```
your_domine/sessionserver/* -> https://sessionserver.minesocial.net/$1
your_domine/api/*-> https://api.minesocial.net/$1
your_domine/authserver/*-> https://authserver.minesocial.net/$1
```

# Known issues
* Skins can't be loaded when the client uses authlib-injector while the server doesn't. (I have not tested it)
* Problem with the display of the cape of another player. (If the visible player does not have a cape) A player without a cape can turn it off in the skin settings in the game and the display will be repaired. 
* Incompatible with [HMCL](https://github.com/huanghongxun/HMCL). 
* If you use [Mohist server core](https://github.com/MohistMC/Mohist) and use built-in update mechanism, after update server.jar server start without injection from [autlib-injector](https://github.com/yushijinhun/authlib-injector), server restart required to resume injection.
