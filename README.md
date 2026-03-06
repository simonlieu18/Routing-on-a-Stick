<p align="center">
<img width="50%" height="324" alt="Screenshot 2026-03-06 at 11 49 15 AM" src="https://github.com/user-attachments/assets/eb10a04e-f620-4ced-b76a-bd58df84fa32" />

</p>

<h1>Router on a Stick with inter-VLAN communication</h1>
In this lab, we segment a network into VLANs and enable inter-VLAN routing using a Router on a Stick (ROAS) configuration<br />



<h2>Environments and Technologies Used</h2>

- Cisco Packet Tracer
- Cisco IOS CLI
- 802.1Q Trunking

<h2>Operating Systems Used </h2>

- Cisco IOS (Router & Switch)

<h2>High-Level Steps</h2>

- Configure VLANs on the switch and assign access ports
- Configure trunk port between switch and router
- Configure router sub-interfaces with 802.1Q encapsulation
- Verify inter-VLAN connectivity using ping (ICMP)

<h2>Configuration Steps</h2>

<img width="45%" height="262" alt="Screenshot 2026-03-06 at 2 49 04 PM" src="https://github.com/user-attachments/assets/51a169db-6b6a-4e93-b83c-23e2334c5d0c" />
<img width="45%" height="423" alt="Screenshot 2026-03-06 at 2 49 11 PM" src="https://github.com/user-attachments/assets/9dfa453e-2c7d-4698-83e1-416a465aa6c9" />



<p>
In this lab, subnets and IP addresses are already set up for the devices in the network besides the router. The goal is to put PC 1 & 3 in VLAN 10 and PC 2 & 4 in VLAN 20. To do that, we will have to get into global configuration mode on each switch and navigate to the interfaces of the ports connected to the PCs. Then switch the port modes to access and assign their respective VLANs.
</p>
<br />

<img width="50%" height="206" alt="Screenshot 2026-03-06 at 2 52 46 PM" src="https://github.com/user-attachments/assets/330be074-21fc-4b7c-87f8-e0907d3dce7f" />
<img width="40%" height="144" alt="Screenshot 2026-03-06 at 2 54 37 PM" src="https://github.com/user-attachments/assets/94f09139-8772-42a1-823f-eacf96045a16" />

<p>
Next, configure the trunk ports on the switches so that traffic from multiple VLANs can travel through. On this network, the gigabit ports on the switches must be configured as trunk ports.
</p>
<br />

<img width="45%" height="251" alt="Screenshot 2026-03-06 at 2 57 18 PM" src="https://github.com/user-attachments/assets/88dbef31-1dbf-4b09-84f7-80e92cf5978b" />
<img width="50%" height="208" alt="Screenshot 2026-03-06 at 2 57 53 PM" src="https://github.com/user-attachments/assets/ff098573-b5a1-4986-bf85-a47a13609d07" />



<p>
With the switches configured, we can now move on to the router. Since a single physical port handles traffic for multiple VLANs, we create sub-interfaces — one per VLAN — and assign each an IP address that will serve as the default gateway for that VLAN. Also don't forget to use "no shutdown" on the main interface to activate the port.
</p>
<br />

<img width="60%" height="476" alt="Screenshot 2026-03-06 at 2 59 38 PM" src="https://github.com/user-attachments/assets/f886cd86-f5c3-4a82-ad07-e854612558bc" />

<p>
The last step is to test connectivity with all devices across the network.
</p>
<br />
