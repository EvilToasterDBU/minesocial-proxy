

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

# Known issues
* Skins can't be loaded when the client uses authlib-injector while the server doesn't.
