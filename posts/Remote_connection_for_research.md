---
layout: post
title: Building a Remote ML Workstation with WSL and Tailscale
date: 2026-05-18
permalink: /posts/remote_connection_with_tailscale/
cover: /assets/img/Tailscale_concept.png
---

Using an old laptop can become quite frustrating. Slow speed does not seem to be the only downside, but also old machines have hardwares which are incapable of running ML processes. In addition, application developing companies often stop to support old OS versions, which makes an application highly incompatible and unstable. 

With such an old laptop, even simple progress can become painfully slow. Especially if you don't like working at home, you need to figure a way out. Luckily someone has a nice workstation with a GPU :) Så skal jeg kun forbinde den laptop og den desktop!

At forbinde to computerne kan være enkel, hvis man bruger en agent application. Der hedder [Tailscale](https://tailscale.com/) som jeg bruger, en VPN service. Tailscale tilbyder en personlig konto hvor man kan tilmelde machines til en liste, som kan blive forbundet, gennem en krypteret forbindelse.

# Machine Specification
* <b><span style="color:#00A6A6;">Workstation</span></b>
  * Windows 11 Intel i9-12900K
  * 64GB DDR5 RAM
  * NVIDIA RTX 4070Ti 12GB GDDR
  * **CUDA 13.1**
  * WSL2 Ubuntu
  * Conda environment
* <b><span style="color:#1E90FF;">Laptop (MacBook Pro 2016 13')</span></b>
  * macOS Monterey 12.7.6
  * 2.9 GHz Dual-Core Intel Core i5
  * 16 GB 2133 MHz LPDDR3
  * Intel Iris Graphics 550 1536 MB


# Tailscale
> Two machines see each other as if they were on the same local network!   
 
[Download Tailscale application](https://tailscale.com/download) on the both machine, choosing right one for right operating system. (Allowing the network access from the settings on Mac was required for me) Create account if you are using for first time. The basic option I choose can be used free of charge. If you sign into Tailscale, you can see the list of machines and their ip addresses. How the two machines can see each other. Write the <b>Tailscale ip address of the workstation</b> fx. <u>100.12.345.6</u>.

The connection is encrypted and private. It is not exposing the workstation to the public internet through open SSH ports, Tailscale creates a private mesh VPN between trusted devices using WireGuard-based encryption. 

The overal configuration is shown in the figure below.

![Remote Connection with Tailscale](/assets/img/Tailscale_concept.png){: width="66%" } 


# Setup After Installation 
Inside the Ubuntu WSL environment on the Windows workstation, run these commands to install, activate, and check an SSH server (the workstaton).

<style>
  .windows-terminal {
    background-color: #251318;
    color: #00A6A6;
    font-family: 'monaco', Courier, monospace;
    padding: 15px;
    border-radius: 5px;
    border-left: 5px solid #00A6A6;
    overflow-x: auto;
  }
</style>

<style>
  .mac-terminal {
    background-color: #422a45;
    color: #00BFFF;
    font-family: 'monaco', Courier, monospace;
    padding: 15px;
    border-radius: 5px;
    border-left: 5px solid #00BFFF;
    overflow-x: auto;
  }
</style>

<pre class="windows-terminal">
sudo apt install openssh-server 
sudo service ssh start
</pre>

This command should show a message,
<pre class="windows-terminal">
sudo service ssh status
</pre>
 containing this line:
<pre class="windows-terminal">
Active: active (running)
</pre>

Now go to the laptop, and see the Tailscale IP address of the workstation, where in this case, is <u>100.12.345.6</u>. Put this command in Terminal to initiate access.

<pre class="mac-terminal">
ssh workstation_name@100.12.345.6
</pre>

# Post-Setup
Yet, this might not work. WSL runs inside a virtualised network environment, meaning the SSH server inside Ubuntu is not automatically visible from outside the Windows host. Because of this, Windows needs to forward incoming SSH traffic to the internal WSL IP address.

The internal WSL IP address can be obtained using:
<pre class="windows-terminal">
hostname -I
</pre>

The forwarding rule tells Windows to listen for SSH traffic on port 22 and forward it to the SSH server running inside WSL.

<pre class="windows-terminal">
netsh interface portproxy add v4tov4 listenport=22 listenaddress=0.0.0.0 connectport=22 connectaddress=(laptop Tailscale IP address)
</pre>

Also allow the Windows firewall to accept incoming SSH traffic:
<pre class="windows-terminal">
New-NetFirewallRule -DisplayName "WSL SSH" -Direction Inbound -LocalPort 22 -Protocol TCP -Action Allow
</pre>

Now, finally you should be able to do this from the laptop:
<pre class="mac-terminal">
ssh workstation_name@100.12.345.6
</pre>

