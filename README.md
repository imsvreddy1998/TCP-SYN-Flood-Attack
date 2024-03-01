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






