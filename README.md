# howtocreateavirtualboxongcp
How to create a virtual box on gcp


#--- 1. Enable Virtualization on a VM ----
a) create an centos7 machine called centos7
   grep -cw vmx /proc/cpuinfo
b) stop instance , and show disks in GCP Console
   # create image with virtualization enabled in google cloud shell
   gcloud compute images create centos7-with-base-virtization-image --source-disk=centos7  --source-disk-zone=europe-west2-a --licenses https://compute.googleapis.com/comput...
b) now create an instance called centos7-with-virtization-instance
   grep -cw vmx /proc/cpuinfo

#--- 2. Configure VM : Install Desktop & Utilities ----
#
   sudo yum update
   sudo  yum  groupinstall -y "Xfce" 
   sudo yum install -y firefox htop

#--- 3. Configure VM : Install xrdp and configure ----
#
   sudo yum install -y xrdp
   sudo systemctl enable xrdp 
   sudo systemctl disable firewalld 
   echo "xfce4-session" (Greater Than Charecter) ~/.Xclients
   chmod a+x ~/.Xclients

#--- 4. Configure VM : Basic security for xrdp ----
#
   sudo passwd {userid}
   sudo -i       
   sudo usermod -aG wheel {userid}
   sudo reboot

#--- 5. Virtualbox : Install Virtualbox Prerequisits ----
#
sudo yum groupinstall "Development tools"
sudo yum install kernel-headers qemu-kvm  patch gcc kernel-devel  make perl 
 
#--- 6. Virtualbox : Download Latest Version of Virtualbox ---
#
Connect via RDP
open browser, goto virtualbox website
download centos7 .rpm file

-- 7. Virtualbox : Install Virtualbox ---
start a terminal
cd Downloads
sudo yum localinstall VirtualBox-6.1-6.1.18_142142_el7-1.x86_64.rpm
sudo reboot

 ** FINISHED **



