# TCP-SYN-Flood-Attack
<p align="center" >
 <b>
  <span style="color:red"> Welcome to the TCP SYN Flood Attack project !</span> 
 </b>
 </p>
 
This deliverable would discuss TCP SYN Flood Attacks and demonstrate how to launch a SYN Flood Attack using Kali Linux and the Metasploit framework. It will also demonstrate how to recognize one using the Wireshark protocol analyzer.

# Introduction to TCP SYN Flood Attack

<p align="justify" > A TCP SYN Flood attack is a form of <b>denial-of-service (DoS) attack</b> commonly used to overwhelm a target server's ability to respond to legitimate requests. It exploits the <b>TCP handshake</b> process, which is a three-step procedure for establishing a connection between two devices: <b>SYN, SYN-ACK, and ACK</b>. </p>

<p align="justify" > During a TCP SYN Flood attack, the attacker sends a large number of SYN (synchronization) packets to the target server, but does not respond to the server's SYN-ACK (synchronization acknowledgment) packets. This causes the server to allocate resources and maintain <b>half-open connections</b> for each incoming SYN packet, eventually exhausting the server's resources and preventing it from servicing legitimate connection requests. The goal of a TCP SYN Flood attack is to disrupt the availability of a service or website, rendering it inaccessible to legitimate users. These attacks can be launched using various tools and techniques, including specialized software and frameworks like the <b>Metasploit framework</b> on platforms such as <b>Kali Linux</b>.</p>

<p align="justify" > TCP SYN Flood attacks are a serious threat to <b>network infrastructure</b> and require effective mitigation strategies to defend against them. Understanding the mechanics of these attacks is crucial for network administrators and security professionals to protect their systems and maintain the availability of critical services.</p>

<p align="justify" > Furthermore, In a SYN Flood Attack, the attacker floods the server with SYN packets from spoof IP addresses, leading the server to respond with a SYN-ACK and leave its ports partially open while waiting for a response from a nonexistent host.</p>

![image](https://github.com/imsvreddy1998/TCP-SYN-Flood-Attack/assets/124395648/da0a3514-3ae3-4498-95fe-322cfe867a8b)

<p align="justify" > In simple terms, the attacker can target the destination web server by flooding the SYN packets and not responding with ACK. In this situation, the target struggles to handle such traffic, which in turn causes a rise in CPU and memory utilization, which eventually exhausts the target's resources (CPU and RAM). Either the fraudulent client sends the expected ACK, or it does not. It never gets the SYN-ACK in the first place if the IP address is spoofed. In either case, the server is being attacked and will be patiently awaiting the acknowledgment of its SYN-ACK message.</p>

## Setting Up Kali Linux

<b> 1. Download Kali Linux ISO:</b>
<ul>
  <li> Visit the official Kali Linux website and download the latest ISO image suitable for your system architecture (32-bit or 64-bit).</li>
</ul>

<b> 2. Create Bootable USB Drive or Virtual Machine:</b>
<ul> 
<li> Use a tool like Rufus (for Windows) or Etcher (for macOS and Linux) to create a bootable USB drive with the Kali Linux ISO. Alternatively, set up a virtual machine using software like VirtualBox or VMware.</li>
</ul>

<b> 3. Boot from USB Drive or Start Virtual Machine:</b>
<ul> 
<li>Restart your computer and boot from the USB drive with Kali Linux or start the virtual machine.</li>
</ul>

<b> 4. Select Installation Option:</b>
<ul>
  <li> Once Kali Linux boots up, you'll be presented with several options. Choose either <b>"Graphical Install"</b> for a user-friendly installation process or <b>"Install"</b> for a text-based installation.</li>
</ul>

<b> 5. Follow Installation Wizard:</b>
<ul>
  <li> Follow the on-screen prompts to set up language, location, keyboard layout, and other system settings.</li>
</ul>

<b> 6. Partition Disk:</b>
<ul>
  <li> Choose the disk or partition where you want to install Kali Linux. You can select automatic partitioning or manually partition the disk according to your preferences.</li>
</ul>

<b> 7. Create User Account:</b>
<ul> 
  <li> Set up a username and password for the Kali Linux user account.</li>
</ul>

<b> 8. Configure Network Settings:</b>
<ul>
  <li> Configure network settings, including setting up a static or dynamic IP address, depending on your network environment.</li>
</ul>

<b> 9. Install GRUB Boot Loader:</b>
<ul>
  <li>Install the GRUB boot loader to the Master Boot Record (MBR) or the EFI system partition, depending on your system's firmware. </li>
</ul>

<b> 10. Complete Installation:</b>
<ul>
  <li> Once the installation process is complete, reboot your system and remove the installation media (USB drive or ISO file) if necessary.</li>
</ul>

<b> 11. Update System Packages:</b>
<ul>
  <li> After booting into Kali Linux, open a terminal and run the following commands to update the system packages:</li>
</ul>

            sudo apt update
            sudo apt upgrade

<b> 12. Optional: Install Additional Tools:</b>
<ul>
  <li> Install any additional tools or packages you may need for your specific tasks using the APT package manager, such as Metasploit Framework for security testing purposes.</li>
</ul>

<p align="justify" > Congratulations! You've successfully set up Kali Linux on your system. Now you're ready to explore its features and use it for various security testing and penetration testing tasks.</p>

<p align="justify" > Setting Up Kali Linux provides the foundational environment necessary for conducting various security testing and penetration testing tasks. Once Kali Linux is installed and configured, the next step is to install the Metasploit Framework, a powerful tool for exploiting vulnerabilities and performing security assessments.</p>

## Installation of Metasploit Framework

<p align="justify" > The Metasploit Framework stands as one of the most potent tools in the arsenal of ethical hackers, security professionals, and penetration testers alike. Its versatility and extensive array of exploits, payloads, and auxiliary modules make it an indispensable asset for assessing and fortifying the security posture of systems and networks. </p>

<p align="justify" >In this guide, I delve into the process of installing Metasploit Framework on Kali Linux, the widely acclaimed operating system tailored explicitly for penetration testing and digital forensics. By following these steps, you'll unlock the potential to conduct comprehensive security assessments, identify vulnerabilities, and craft effective defenses against potential threats.</p>

<b> 1. Update Package Repositories:</b>
<ul>
  <li> Before installing Metasploit Framework, ensure that your Kali Linux system's package repositories are up to date by running:</li>
</ul>

            sudo apt update

<b> 2. Install Metasploit Framework:</b>
<ul>
  <li> Use the following command to install Metasploit Framework along with its dependencies:</li>
</ul>

           sudo apt install metasploit-framework

<b> 3. Verify Installation:</b>
<ul>
<li> Once the installation is complete, you can verify that Metasploit Framework is installed correctly by running:</li>
</ul>

            msfconsole

<ul>
  <li> This command will launch the Metasploit console, indicating that the framework is ready for use.</li>
</ul>

<b> 4. Update Metasploit Framework (Optional):</b>
<ul> 
<li> It's advisable to regularly update Metasploit Framework to ensure you have the latest features and security patches. You can update it by running:</li>
</ul>

           sudo msfupdate

<b> 5. Explore Metasploit Framework:</b>
<ul>
  <li> Spend some time familiarizing yourself with the features and capabilities of Metasploit Framework. You can explore various modules, exploits, payloads, and auxiliary modules available within the framework.</li>
</ul>

<b> 6. Optional: Configure Database:</b>
<ul>
  <li> Metasploit Framework can optionally use a PostgreSQL database to store information about targets, vulnerabilities, and exploits. You can set up and configure the database by following the instructions provided in the Metasploit documentation.</li>
</ul>

<b> 7. Begin Security Assessments:</b>
<ul>
  <li> With Metasploit Framework installed, you're ready to start conducting security assessments, penetration tests, and vulnerability assessments against target systems.</li>
</ul>

<p align="justify" > By following these steps, you'll have successfully installed Metasploit Framework on your Kali Linux system, enabling you to leverage its powerful features for ethical hacking and security testing purposes.</p>

<p align="justify" > Once Metasploit Framework is installed on your Kali Linux system, you gain access to a powerful suite of tools and modules for conducting security assessments and penetration tests. Among its capabilities is the ability to understand and simulate various types of network attacks, including the <b>TCP SYN Flood attack</b>. By delving into the specifics of how Metasploit facilitates such attacks, you'll gain valuable insights into both offensive and defensive strategies in the realm of cybersecurity.</p>

## Understanding the SYN Flood Attack in Metasploit

<p align="justify" > Metasploit Framework provides a comprehensive platform for not only exploiting vulnerabilities but also for simulating and understanding various types of network attacks, including the TCP SYN Flood attack. Within Metasploit, the SYN Flood attack is typically conducted using auxiliary modules designed specifically for this purpose.</p>

<p align="justify" > By exploring these modules and their functionalities, users can gain a deeper understanding of how the SYN Flood attack operates, its impact on target systems, and the techniques used to mitigate such attacks. Additionally, Metasploit allows users to customize parameters such as target IP addresses, port numbers, and packet rates, enabling them to tailor the attack to specific scenarios and environments.</p>

<p align="justify" > Understanding the SYN Flood attack in Metasploit provides valuable insights into the mechanisms of denial-of-service (DoS) attacks, enhances knowledge of network security, and equips security professionals with the skills necessary to defend against such threats effectively.</p>

## Identifying the target

<p align="justify" > Before launching a TCP SYN Flood attack using Metasploit, it's crucial to identify the target system or network. The target could be a specific IP address, domain name, or a range of IP addresses representing a network segment. I am using <b>testphp.vulnweb.com</b> as my victim in this case.</p>

<p align="justify" > By accurately identifying the target system or network, you can effectively focus your efforts and ensure that the TCP SYN Flood attack is conducted in a controlled and responsible manner.</p>

## Launching the Attack

<p align="justify" > Once I have identified the target system and prepared the necessary parameters, launching a TCP SYN Flood attack using Metasploit involves executing the appropriate auxiliary module with the desired configurations. Here's a step-by-step guide:</p>

<b> 1. Determine the IP Address for the Hostname:</b>
<ul>
<li> 
 Use the <b>ping </b> command to find the IP Address of the hostname: testphp.vulnweb.com in the terminal. 
</li> 
</ul>

          ping testphp.vulnweb.com

<p align="justify" > Here, The ping command sends an ICMP (Internet Control Message Protocol) packet to a networked computer. If you try to ping a hostname, the ping program performs a DNS request to discover the host's IP address. The IP address is displayed in the command output.</p>

![image](https://github.com/imsvreddy1998/TCP-SYN-Flood-Attack/assets/124395648/d6e9641d-582d-4bf1-bf41-60f75593095c)

So, now I know the victim’s <b>IP address: 44.228.249.3</b> and then Launch the metasploit.

<b> 2. Open Metasploit Console:</b>
<ul>
 <li> Launch the Metasploit console by typing <b>msfconsole</b> in the Kali Linux terminal.</li>
</ul>

<b> 3. Search for SYN Flood Module:</b>
<ul>
 <li> Use the <b>"search</b> command to find the SYN Flood auxiliary module. You can search for it using keywords like "synflood" or "dos."</li>
</ul>

![image](https://github.com/imsvreddy1998/TCP-SYN-Flood-Attack/assets/124395648/2f1e39d3-9799-4d90-8746-d8eaea90edab)

<b> 4. Select the Module:</b>
<ul>
 <li> Once you've identified the IP address for the target hostname, use the <b>"use"</b> command to select it. Make sure to note the module's name and path by running the following command.</li>
</ul>

         Msf6 > use auxiliary/dos/tcp/synflood
         Msf6 > show options

 
<b> 5. View Module Options:</b>
<ul>
 <li> Display the available options for the selected module using the <b>"show options"</b> command. This will show you the parameters that need to be configured before launching the attack.</li>
 <li> Now, I can now view the options that are available for setting.</li>
</ul>

![image](https://github.com/imsvreddy1998/TCP-SYN-Flood-Attack/assets/124395648/5ca573da-01cb-4c61-aa2e-53235364375b)

<ul>
 <li> To set an option just I have to type set and the option name. I have the following two main options to set.</li>
</ul>

<ol>
 <li> RHOST = Target IP Address</li>
 <li> RPORT = Target Port Address</li>
</ol>

![image](https://github.com/imsvreddy1998/TCP-SYN-Flood-Attack/assets/124395648/d74698cd-637b-4c99-b934-daac5ca8f2fa)


<b> 6. Set Target IP and Port:</b>
<ul>
 <li> Use the <b>"set"</b> command to specify the target IP address and port number by running following commands. These parameters define the destination of the SYN Flood attack.</li>

             set RHOST 44.228.249.3
             set RPORT 80
</ul>

![image](https://github.com/imsvreddy1998/TCP-SYN-Flood-Attack/assets/124395648/3c02588f-5f25-4c5e-bc7b-a8d853473db2)


<b> 7. Verify Settings:</b>
<ul>
 <li> Double-check the configured settings using the <b>"show options"</b> command to ensure that everything is set up correctly.</li>
</ul>

<b> 8. Launch the Attack:</b>
<ul>
 <li> Once all parameters are configured, you can launch the SYN Flood attack by typing <b>"exploit"</b> or <b>"run"</b> in the console.</li>
</ul>

![image](https://github.com/imsvreddy1998/TCP-SYN-Flood-Attack/assets/124395648/82fc7107-f944-4249-a43e-71cf039f26d4)




















