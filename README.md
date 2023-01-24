<h2 align="left"><img src="https://i.ibb.co/Xsnxkbz/Copy-of-Untitled-Design.png" height="35" alt="telegram logo">  PrivateMiner Open Source Blockchain Private Key Explorer for EVM Networks</h2>
<p>In EVM networks (<strong>Ethereum</strong>, <strong>Binance Smart Chain</strong>, <strong>Polygon</strong>, <strong>Avax</strong>, <strong>Arbitrum</strong>, <strong>Fantom</strong>, <strong>Cronos</strong>, <strong>Optimism</strong>, <strong>Gnosis</strong>) I will talk about 2 different ways to scan for active or unused wallets;</p>
<p><strong>Ethereum</strong>, <strong>Binance Smart Chain</strong>, <strong>Polygon</strong>, <strong>Avax</strong>, <strong>Arbitrum</strong>, <strong>Phantom</strong>, <strong>Cronos</strong>, <strong>Optimism</strong>, <strong>Gnosis</strong> Since the private key encryption of these EVM networks is the same, we will scan them all at the same time, thus increasing our chances of finding the existing private key.</p>
<p>It may seem confusing to you before we start, but I will try to explain it for you in the simplest way with examples, tests and hardware knowledge.</p>
<h2>
</h2><ul>

<p><strong><img src="https://i.ibb.co/8xXHWc3/top-rated.png" height="20" alt="telegram logo"> Querying the balances of Private Keys Generated with RPC</strong></p>


<p><strong><img src="https://i.ibb.co/8xXHWc3/top-rated.png" height="20" alt="telegram logo"> Saving current wallet addresses in home networks to our local machine and querying as database without RPC (Fastest method)</strong></p>
<h2>
</ul>


<blockquote>
<p><strong>Ethereum</strong> DATABASE DUMPS -- 221M-Address — 200$<br>
<strong>BSC</strong> DATABASE DUMPS -- 245M-Address — 200$<br>
<strong>Polygon</strong> DATABASE DUMPS -- 215M-Address — 150$<br>
<strong>Avax</strong> DATABASE DUMPS -- 5M-Address — 50$<br>
<strong>Arbitrum</strong> DATABASE DUMPS -- 2.7M-Address — 50$<br>
<strong>Fantom</strong> DATABASE DUMPS -- 51M-Address — 100$<br>
<strong>Cronos</strong> DATABASE DUMPS -- 1.1M-Address — 50$<br>
<strong>Optimism</strong> DATABASE DUMPS -- 2.7M-Address — 50$<br>
<strong>Gnosis</strong> DATABASE DUMPS -- 5M-Address — 50$</p>
</blockquote>

<p>The database shooting process is a very laborious and tedious process. It takes almost years to scan the blocks in EVM networks with RPC, but you can easily reach them all. Unfortunately, this data is not sold on the Internet, it can be said that it is impossible to find.</p>
<h2 id="how-does-this-work">How does this work?</h2>
<p>A private key is basically just a number between 1 and 2256. This website generates keys for all of those numbers, spread out over pages of 128 keys each.</p>
<p><img src="https://i.ibb.co/YjczR3X/za19Z.png" alt="enter image description here"></p>
<p>This website doesn’t actually have a database of all private keys, that would take an impossible amount of disk space. Instead, keys are procedurally generated on the fly when a page is opened. The page number is used to calculate which keys should be on that page.</p>
<p>Finding an active wallet is difficult but not impossible. When we generate a random private key, you have a chance to find someone else’s fortune.</p>
<h2 align="left">Querying Private Keys created with RPC</h2>
<p>Querying with RPC is a bit slow system, RPC’s request restrictions per current second, hangups (RPC crashes) occur because we send too many queries.<br>
Although all the RPC links I tried on <a href="http://chainlist.org">chainlist.org</a> were successful, controlling many networks at the same time reduces our chance of finding private keys. Because it is necessary to query the created Private Key with different RPCs in 9 networks, which makes it impossible, so if we are going to continue with RPC, we have to choose 1 EVM network and try our luck in this network.</p>

```mermaid
graph LR
 A[Private Key Generator] ---> B((EVM RPC))
B --> D{Balance Check}
D --> E($ Found! Save to Database)
E --> A;
```


<p>When the balance query is made, if there is any txns record or balance in the account, the database automatically records it.</p>
<h2 id="supported-platforms">Supported Platforms</h2>
<p>On <strong>Linux</strong> and <strong>Windows</strong> EVM networks support private key generation.</p>
<h2 id="recommended-requirements">Recommended Requirements</h2>
<ul>
<li>Server running the latest versions of Linux or Windows.</li>
<li>10 core CPU and 16 GB memory (RAM)</li>
<li>Broadband internet connection with 50MB/s upload/download speeds</li>
</ul>
<h2>
## Registering the current wallet addresses in the home networks to our local machine and querying as a database without RPC
</h2><p>As the fastest method we discovered, without RPC query, the query speed is incredibly fast and trouble-free through the database we created, but it has a disadvantage, if the accounts with balance in the newly created blocks are not in the existing database, it means we will never be able to access them, but don’t worry, they have already been used or are still being used in all networks. There are 1.2 Billion wallet addresses in progress. Let’s understand this mechanism graphically.</p>

```mermaid
graph LR
 A[Private Key Generator] ---> D{SQL Wallet Address Check}
 D --> E($ Found! Save to Database)
 E --> A;
```



<p>As the chart shows, the RPC in the first example is completely gone, we don’t need it anymore as it slows us down so much. Let’s take a look at our speed tests and information about hardware information.</p>
<h2 id="supported-platforms-1">Supported Platforms</h2>
<p>On <strong>Linux</strong> and <strong>Windows</strong> EVM networks support private key generation.</p>
<h2 id="recommended-requirements-1">Recommended Requirements</h2>
<ul>
<li>Server running the latest versions of Linux or Windows.</li>
<li>Minimum Intel® Core™ i5 Processor</li>
<li><strong>IMPORTANT</strong> 3x - 512 TB free disk space, solid state drive(NVMe SSD), 7000 MB/s transfer rate, read speed. (It will need an NVMe SSD as speed is important in generating and querying private keys)</li>
<li>10 core CPU and 16 GB memory (RAM)</li>
<li>It will not need an internet connection.</li>
</ul>
<p>One of the reasons for the 3x NVMe SSD is that we can increase the speed even more by operating on 3 different SSDs. However, you can start with any number you want.</p>
<h2 id="test-operations-and-speed-results">Test Operations and Speed Results</h2>
<p>Yes, I know it sounds so complicated and you may be confused, but you will probably be surprised when you see the speed results.</p>
<p>Test and Speed results were captured on the hardware I mentioned above.</p>
<p>It can generate 1x NVMe SSD/second <strong>1M</strong> private key and query.<br>
It can generate 3x NVMe SSD/second <strong>2.8M</strong> private key and query.</p>
<p>We query approximately 241,920,000,000 Private Keys a day, amazing isn’t it? Even if the probability of finding a Private Key is low, if we can reach this number per day, isn’t it worth trying?</p>
<p>I would like to give some information about our 3-month testing process;</p>
<ul>
<li>3x NVMe SSD max on each device. Let’s take a look at the graph of the data accessed for 4 months with 4 different devices.</li>
</ul>
<p><img src="https://i.ibb.co/khk6PJy/Device-Working-Timeline-1.png" alt="enter image description here"></p>
<p>Now that we’ve taken a look at the data, it’s time to decide…<br>
Start by working with RPC with fewer processes? Or will you think professionally and activate the 2nd stage?</p>
<p>You can contact me for your questions.</p>
<h3 id="section"></h3>
<img align="right" height="150" src="https://i.imgflip.com/65efzo.gif">
<h3 id="section-1"></h3>
<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.cprogramming.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg" alt="c" width="40" height="40"> </a> <a href="https://www.w3schools.com/cpp/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/cplusplus/cplusplus-original.svg" alt="cplusplus" width="40" height="40"> </a> <a href="https://golang.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/go/go-original.svg" alt="go" width="40" height="40"> </a> <a href="https://nodejs.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg" alt="nodejs" width="40" height="40"> </a> <a href="https://www.centos.org/" target="_blank" rel="noreferrer"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/centos/centos-original.svg" alt="c" width="40" height="40"> </a>  <a href="https://www.php.net/" target="_blank" rel="noreferrer"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" alt="c" width="40" height="40"> </a> <a href="https://www.mongodb.com/" target="_blank" rel="noreferrer"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg" alt="c" width="40" height="40"> </a> </p>
<h3 id="section-2"></h3>
<div align="left">
  <img src="https://img.shields.io/static/v1?message=Telegram&amp;logo=telegram&amp;label=&amp;color=2CA5E0&amp;logoColor=white&amp;labelColor=&amp;style=for-the-badge" height="35" alt="telegram logo">
  <img src="https://img.shields.io/static/v1?message=Youtube&amp;logo=youtube&amp;label=&amp;color=FF0000&amp;logoColor=white&amp;labelColor=&amp;style=for-the-badge" height="35" alt="youtube logo">
  <img src="https://img.shields.io/static/v1?message=Gmail&amp;logo=gmail&amp;label=&amp;color=D14836&amp;logoColor=white&amp;labelColor=&amp;style=for-the-badge" height="35" alt="gmail logo">
  <img src="https://img.shields.io/static/v1?message=Twitter&amp;logo=twitter&amp;label=&amp;color=1DA1F2&amp;logoColor=white&amp;labelColor=&amp;style=for-the-badge" height="35" alt="twitter logo">
  <img src="https://img.shields.io/static/v1?message=Medium&amp;logo=medium&amp;label=&amp;color=12100E&amp;logoColor=white&amp;labelColor=&amp;style=for-the-badge" height="35" alt="medium logo">
</div>
<h2>
</h2>
<div align="center">
<img src="https://svgshare.com/i/pgi.svg" alt="Snake animation">
</div>
</div>
</body>

</html>
