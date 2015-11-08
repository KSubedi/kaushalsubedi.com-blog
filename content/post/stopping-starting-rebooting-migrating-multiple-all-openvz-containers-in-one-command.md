+++
date = "2014-11-22"
title = "Stopping / Starting / Rebooting / Migrating Multiple (All) OpenVZ Containers In One Command"

+++

Working as a systems administrator, there are many times where you want to automate things so that you don't have to do them manually. A lot of times I am working with OpenVZ nodes, I run into situations where I have to run a command in all vm's or reboot all vm's (don't reboot all in production node). Here is a simple linux command that will find all openvz vm's and reboot / restart or do anything with it.

<b>Reboot All Containers</b>
<div class="postContent">
<pre>for VE in $(vzlist -Ha -o veid); do vzctl restart $VE; done</pre>
<b>Start All Containers</b>
<pre>for VE in $(vzlist -Ha -o veid); do vzctl start $VE; done</pre>
&nbsp;

<b>Migrate All Containers</b>

</div>
&nbsp;
<div class="postContent">
<pre>for VE in $(vzlist -Ha -o veid); do vzmigrate --remove-area no --keep-dst [NODE_IP] $VE; done
</pre>
</div>
<div class="postBookmarks"> Just replace the [NODE_IP] with the ip of the node that you want to migrate them to. Make sure you have keys on the node that you are migrating to so that it doesn't repititively ask you for password.</div>
<div class="postBookmarks"></div>
<div class="postBookmarks">You can pretty much do anything with all the VM's by following the following format:</div>
<div class="postBookmarks">
<div class="postContent">
<pre>for VE in $(vzlist -Ha -o veid); do [COMMAND]; done
</pre>
Just replace the [COMMAND] with the command you want to run for each VM. Use $VE to get the VEID of the container.

</div>
</div>
