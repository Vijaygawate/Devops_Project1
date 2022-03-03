# Devops_Project1
Servers needed : Jenkins, ansible, github ac with code on it , web server 
**Step1**: 
Connecting github with jenkins : go into setting in jenkins/webhook add webhook put jenkins url here like(http://3.110.94.225:8080/github-webhook/)
**Step2**:
On ansible server set pw for root 
#passwd root 
#vi /etc/ssh/sshd_config
uncomment permmitrootlogin
and below no to yes 
#systemctl restart sshd 
Vijay22@
On jenkins server set pw for root 
#passwd root 
#Vijay22@
**Step3**: 
Establishing pw less connection between jenkins and ansible: On jenkins server 
#ssh-keygen  (3 times enter)
#ssh-copy-id -i root@< private ip of ansible server > 
Now , take ssh of ansible server you will logged in to ansible through jenkins server 
#ssh root@< private ip of ansible server >
**Step3**: 
Install httpd ob webserver instance 
Establishing pw-less connection between ansible and webserver instance : steps should same as above 
In ansible server , put private ip of webserver instance in 
#vi /etc/ansible/hosts file 
**Step4**:
Now add publish over ssh plugin into jenkins 
manage plugins > congigure system > at bottom 
add ssh 
name- jenkins 
hostname- private ip of jenkins 
advanced > pw auth> enter pw here (root) as Vijay22@ 
test connection > apply and save 
do same for ansible 
**Step5**:
Creation of jenkins job:
