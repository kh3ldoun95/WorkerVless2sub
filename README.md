Here is the translation of the provided Chinese text into English:

---

# Preferred Subscription Generator WorkerVless2sub

### This is a subscription content generator for VLESS / Trojan nodes, built using Cloudflare Workers, which automatically generates preferred routes [[Implementation Principle]](https://www.youtube.com/watch?v=p-KhFJAC4WQ&t=70s).

Telegram Group: [@CMLiussss](https://t.me/CMLiussss), **Thanks to [Alice Networks](https://alice.ws/aff.php?aff=15) for providing the cloud servers to maintain the [CM Subscription Conversion Service](https://sub.fxxk.dedyn.io/)!**

# Pages Deployment Method [Video Tutorial](https://www.youtube.com/watch?v=p-KhFJAC4WQ&t=509s)

### 1. Deploy Cloudflare Pages:
   - First, Fork this project on GitHub and click on Star!!!
   - In the Cloudflare Pages console, select `Connect to Git`, then choose the `WorkerVless2sub` project and click `Start Setup`.
     
### 2. Bind Custom Domain to Pages:
   - In the Pages console, go to the `Custom Domains` tab, then click `Set Custom Domain`.
   - Enter your custom subdomain (make sure not to use your root domain), for example:
     If your domain is `fuck.cloudns.biz`, enter `sub.fuck.cloudns.biz` as the custom domain.
   - Follow Cloudflare’s instructions to add a CNAME record `WorkerVless2sub.pages.dev` for the custom domain `sub`, then click `Activate Domain`.

### 3. Modify Quick Subscription Access and Add Built-in Node Information:

  For example, if your Pages project domain is: `sub.fuck.cloudns.biz`;
   - Add a `TOKEN` variable, for quick subscription access; default value: `auto`. The default subscription node address is `/auto`, for example, `https://sub.fuck.cloudns.biz/auto`;

**Add VLESS Built-in Node Information**
   - Add a `HOST` variable, for example, `edgetunnel-2z2.pages.dev`;
   - Add a `UUID` variable, for example, `30e9c5c8-ed28-4cd9-b008-dc67277f8b02`;
   - Add a `PATH` variable, for example, `/?ed=2560`;

**Add Trojan Built-in Node Information**
   - Add a `HOST` variable, for example, `hbpb.us.kg`;
   - Add a `PASSWORD` variable, for example, `bpb-trojan`;
   - Add a `PATH` variable, for example, `/tr?ed=2560`;

### 4. Add Your Exclusive Preferred Routes:

   - Add variables `ADD`/`ADDNOTLS` for local static preferred routes. If no port is provided, TLS default port is 443, and noTLS default port is 80, with `#` used for alias comments, for example:
   ```
   icook.tw:2053#Preferred Domain
   cloudflare.cfgo.cc#Official Preferred Route
   ```

   - Add variables `ADDAPI`/`ADDNOTLSAPI` for **Preferred IP address txt files** URLs, for example:
   ```url
   https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt
   https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesipv6api.txt
   ```

<details>
<summary><code><strong>"I'm not a beginner! I have an IP database! I know what IPtest is! I also have a CSV speed test file!"</strong></code></summary>

   - Add the variable `ADDCSV` for **IPtest speed test CSV file URLs**, for example:
   ```js
   https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv
   ```
   - Add the variable `DLS`, which stands for `ADDCSV` meeting the minimum speed requirement. IPs that do not meet this value will not be added to the preferred subscription content. Note: Ignore units, only consider the numerical value, and adjust based on your speed test results. For example:
   ```js
   8
   ```

 </details>

# Workers Deployment Method [Video Tutorial](https://youtu.be/AtCF7eq0hcE)

### 1. Deploy Cloudflare Worker:

   - In the Cloudflare Worker console, create a new Worker.
   - Paste the content of [worker.js](https://github.com/cmliu/WorkerVless2sub/blob/main/_worker.js) into the Worker editor.

### 2. Modify Quick Subscription Access and Add Built-in Node Information:

  For example, if your Workers project domain is: `sub.cmliussss.workers.dev`;
   - Add a `TOKEN` variable, for quick subscription access; default value: `auto`. The default subscription node address is `/auto`, for example, `https://sub.cmliussss.workers.dev/auto`;

**Add VLESS Built-in Node Information**
   - Add a `HOST` variable, for example, `edgetunnel-2z2.pages.dev`;
   - Add a `UUID` variable, for example, `30e9c5c8-ed28-4cd9-b008-dc67277f8b02`;
   - Add a `PATH` variable, for example, `/?ed=2560`;

**Add Trojan Built-in Node Information**
   - Add a `HOST` variable, for example, `hbpb.us.kg`;
   - Add a `PASSWORD` variable, for example, `bpb-trojan`;
   - Add a `PATH` variable, for example, `/tr?ed=2560`;

### 3. Add Your Exclusive Preferred Routes:

**3.1 Modify `addresses` Parameter Example**

 - Modify the `addresses` parameter to add local static preferred routes. If no port is specified, it defaults to 443 for TLS and does not support generating non-TLS subscriptions. Use `#` for alias comments, for example:
	```js
	let addresses = [
		'icook.tw:2053#Preferred Domain',
		'cloudflare.cfgo.cc#Official Preferred Route',
		'185.221.160.203:443#Telecom Preferred IP',
	];
	```
	We recommend adding preferred domain entries this way, and frequent changes should be handled with `addressesapi`.

 **3.2 Modify `addressesapi` Parameter Example**
 
 - Modify the `addressesapi` parameter, setting the `addressesapi` variable to **Preferred IP address txt file** URLs, for example:
	```js
	let addressesapi = [
		'https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt',
 		'https://addressesapi.090227.xyz/CloudFlareYes',
	];
	```
	You can refer to [addressesapi.txt](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt) for content format and set up your own.

<details>
<summary><code><strong>"I'm not a beginner! I have an IP database! I know what IPtest is! I also have a CSV speed test file!"</strong></code></summary>

 
  **3.3 Modify `addressescsv` Parameter Example**
  
 - Modify the `addressescsv` parameter, setting the `addressescsv` variable to **IPtest speed test result CSV file URL**, for example:
	```js
	let DLS = 4; // Speed threshold
	let addressescsv = [
		'https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv',
 		'https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv',
	];
	```
	`DLS` is the minimum speed required. IPs not meeting this value will not be added to the preferred subscription content. Note: Only consider the numeric value, adjust according to your speed test results.

 </details>

# Subscription Generator Usage [Video Tutorial](https://youtu.be/OjqCKeEY7DQ)

  For example, if your Workers project domain is: `sub.cmliussss.workers.dev`;
  
## 1. Quick Subscription

   - Add a `TOKEN` variable for quick subscription access; default value: `auto`. The default subscription node address is `/auto`, for example:
     ```url
     https://sub.cmliussss.workers.dev/auto
     ```
     
## 2. Custom Subscription 
### VLESS Subscription
   - **Custom subscription format** `https://[Your Workers Domain]/sub?host=[Your Vless Domain]&uuid=[Your UUID]&path=[Your ws Path]`
   - **host**: Your VLESS disguised domain, e.g., `edgetunnel-2z2.pages.dev`;
   - **uuid**: Your VLESS client UUID, e.g., `30e9c5c8-ed28-4cd9-b008-dc67277f8b02`;
   - **path** (optional): Your VLESS path (leave empty if not needed), e.g., `/?ed=2560`.
   - **sni** (optional): Your VLESS SNI (default is same as `host`), e.g., `www.10068.cn`.
   - **type** (optional): Your VLESS transport protocol (default is `ws`), e.g., `splithttp`.
   - Custom subscription URL example:
     ```url
     https://sub.cmliussss.workers.dev/sub?host=edgetunnel-2z2.pages.dev&uuid=30e9c5c
